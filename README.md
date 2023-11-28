# GMail_Automation
GMail automation project


package com.gmail;

import static org.testng.Assert.assertTrue;

import java.net.PasswordAuthentication;
import java.sql.Driver;
import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.devtools.idealized.Javascript;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.testng.annotations.Test;

import com.beust.jcommander.JCommander.Builder;

public class Login_Test {
	WebDriver driver = new ChromeDriver();
	WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
	Actions actions = new Actions(driver);
	WebElement element;

	@Test(priority = 1 )
	public void Log_In() {

		driver.get("https://gmail.com/");
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(20));
		WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
		driver.manage().window().maximize();
		Actions actions = new Actions(driver);
		driver.findElement(By.id("identifierId")).sendKeys("teamqobox@gmail.com");
		driver.findElement(By.xpath("//span[contains(text(),'Next')]")).click();
		WebElement PasswordAuthentication = wait.until(ExpectedConditions
				.visibilityOfElementLocated(By.xpath("//input[@class='whsOnd zHQkBf' and @type='password']")));
		PasswordAuthentication.sendKeys("teamqobox2023");
		driver.findElement(By.xpath("//span[contains(text(),'Next')]")).click();
		actions.moveToElement(driver.findElement(By.xpath("//a[@aria-label='Google apps' and @class='gb_d']"))).click()
				.build().perform();
}
