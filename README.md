package practice;
import java.util.*;
import java.io.*;

public class Practice {
public static void displayTitle()
{
String title = "Computer Hardware Graphics Quality Recommendation Tool";
System.out.println(title);
}
public static String getResolutionString(int num)
{
String resolution;
switch(num)
{
case 1: resolution = "1280 x 720";
break;
case 2: resolution = "1920 x 1080";
break;
case 3: resolution = "2560 x 1440";
break;
case 4: resolution = "3840 x 2160";
break;
default : resolution = "Wrong input";
break;   
}
return resolution;
}
  
public static double getMultiplierValue(int num)
{
double multiplier;
switch(num)
{
case 1: multiplier = 1.0;
break;
case 2: multiplier = 0.75;
break;
case 3: multiplier = 0.55;
break;
case 4: multiplier = 0.35;
break;
default : multiplier = 0;
break;
}
return multiplier;
}
  
public static double calculatePerformanceScore(int gpuClockSpeed, int cpuClockSpeed, int numOfCores, double multiplier)
{
double gpuPerformance = 5.0*gpuClockSpeed;
double cpuPerformance = numOfCores*cpuClockSpeed*1.0;
double performanceScore = (gpuPerformance + cpuPerformance)*multiplier;
performanceScore = Math.round(performanceScore*1000)/1000.0;
return performanceScore;
  
}
  
public static String getRecommendedQuality(double performanceScore)
{
if(performanceScore > 17000.0)
{
return "Ultra";
}
else if(performanceScore > 15000.0)
{
return "High";
}
else if(performanceScore > 13000.0)
{
return "Medium";
}
else if(performanceScore > 11000.0)
{
return "Low";
}
else
{
return "Unable to Play";
}
}
  
public static void displayInformation(int gpuClockSpeed, int cpuClockSpeed, int numOfCores, String resolution, double performanceScore, String recommendedQuality)
{
System.out.println("GPU Clock Speed: " + gpuClockSpeed + " MHz");
System.out.println("CPU Clock Speed: " + cpuClockSpeed + " MHz");
System.out.println("Number of cores: " + numOfCores);
System.out.println("Monitor Resolution: " + resolution);
System.out.println("Performance Score: " + performanceScore);
System.out.println("Recommended Graphics Quality: "+ recommendedQuality);
}
public static void main(String args[])
{
int gpuClockSpeed, cpuClockSpeed, numOfCores, res;
double multiplier, performanceScore;
String resolution, recommendedQuality;
Scanner scanner = new Scanner(System.in);
System.out.print("Please enter the clock speed (in Megahertz) of your graphics card: ");
gpuClockSpeed = scanner.nextInt();
System.out.print("Please enter the clock speed (in Megahertz) of your processor: ");
cpuClockSpeed = scanner.nextInt();
System.out.print("Please enter the number of cores of your processor: ");
numOfCores = scanner.nextInt();
System.out.println("What is the resolution of your monitor?");
System.out.println("\t1. 1280 x 720");
System.out.println("\t2. 1920 x 1080");
System.out.println("\t3. 2560 x 1440");
System.out.println("\t4. 3840 x 2160");
System.out.print("Please select from the options above: ");
res = scanner.nextInt();
resolution = getResolutionString(res);
multiplier = getMultiplierValue(res);
performanceScore = calculatePerformanceScore(gpuClockSpeed, cpuClockSpeed, numOfCores, multiplier);
recommendedQuality = getRecommendedQuality(performanceScore);
displayTitle();
displayInformation(gpuClockSpeed, cpuClockSpeed, numOfCores, resolution, performanceScore, recommendedQuality);
}
  
  
}

