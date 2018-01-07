# Smoothed
An Arduino library to store and smooth sensor inputs using various methods including:
* a simple linear recursive exponential filter
* an average of the last x sensor readings
Uses a template class to sensor readings in any numerical data type.

## How to Install
For details on how to install libraries in the Arduino IDE, please see the [Arduino website](https://www.arduino.cc/en/Guide/Libraries).

## How to Use
A full example is provided with the library and can be found in the Arduino IDE under "File->Examples->Smoothed".

Firstly, you must include the library in your sketch:
```cpp
#include <Smoothed.h> 
```

Next, create an instance of the class defining what data type to use. The example below uses a type of float:
```cpp
Smoothed <float> mySensor;
```
You can replace float with any numeric data type to suit your sensor readings and desired accuracy. See the included library example for a full list of supported data types.

Within the setup function, initialize the instance defining the smoothing method and accuracy:
```cpp
mySensor.begin(SMOOTHED_AVERAGE, 10);	
```
In the above example we are using a simple average of the last 10 sensor readings.

And finally, write in a new sensor value and read the smoothed result:
```cpp
// Read a sensor value from analogue pin 0
mySensor.add(analogRead(SENSOR_PIN));

// Output the smoothed sensor value to the serial
Serial.println(mySensor.get());
```

## Planned Improvements/Changes
1. Add a multi-sample method. Calls a passed function to obtain the sensor value x times and averages out.