# lexisNexis

package MyPackage;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.edge.EdgeDriver;
import org.testng.Assert;

import org.testng.annotations.*;

public static void main(String[] args) {

    WebDriver driver = new ChromeDriver();
    driver.get("http://www.google.com");
    WebElement element = driver.findElement(By.name("q"));
    element.sendKeys("LexisNexis"); 
    element.submit();

    // wait until the google page shows the result
    WebElement myDynamicElement = (new WebDriverWait(driver, 10))
              .until(ExpectedConditions.presenceOfElementLocated(By.id("resultStats")));

    List<WebElement> findElements = driver.findElements(By.xpath("//*[@id='rso']//h3/a"));

    //Get the url of third link and click it it
   driver.findElement(By.xpath(".//*[@id='rso']/li[3]/div/h3/a")).click();

//Return page title
String actualTitle = driver.getTitle();
String expectedTitle = "Title of Page";
assertEquals(expectedTitle,actualTitle);

//driver.close();


}
