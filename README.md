# TEMPERATURE-MONITORING-SYSTEM
TASK 1 (EMBEDDED SYSTEMS INTERNSHIP)

COMPANY: CODTECH IT SOLUTIONS

NAME: TEJAS KAILASH BHOYARKAR

INTERN ID: CTO8NSD

DOMAIN: EMBEDDED SYSTEMS

BATCH DURATION: January 20th,2025 to February 20th,2025 (4 Weeks)

MENTOR NAME: Neela Santhosh Kumar
TASK:--
Temperature sensor(LM35) with esp32 module to display  current temperature data on serial monitor.
ESP32 Temperature Monitoring with LM35
# Overview

This project uses an ESP32 microcontroller to monitor the temperature through an LM35 temperature sensor. The temperature data is read from the LM35 sensor and displayed on the serial monitor in real-time. The system continuously provides temperature readings, which can be used for further processing or data logging.
Features

    Real-Time Temperature Monitoring: Displays temperature data in Celsius on the serial monitor.
    Easy to Set Up: Simple hardware setup with the ESP32 and LM35.
    Continuous Monitoring: Continuously monitors the temperature and displays updates at regular intervals.

Hardware Requirements

    ESP32 Microcontroller (e.g., ESP32 Dev Kit v1)
    LM35 Temperature Sensor
    Jumper Wires
    Breadboard (optional)

Software Requirements

    Arduino IDE (or PlatformIO) to program the ESP32.
    ESP32 Board Package installed in Arduino IDE.

Installation
1. Clone the Repository

Clone this repository to your local machine:
https://github.com/tejasbhoyarkar/TEMPERATURE-MONITORING-SYSTEM/edit/main/README.md


2. Hardware Setup

    Connect the LM35 temperature sensor to the ESP32:
        VCC of LM35 to 3.3V (ESP32).
        GND of LM35 to GND (ESP32).
        Vout (analog output) of LM35 to GPIO 34 (or any available ADC pin on the ESP32).

3. Arduino IDE Setup

    Open the Arduino IDE.
    Install the ESP32 board package:
        Go to File > Preferences.
        In the Additional Boards Manager URLs field, add the following URL:

        https://dl.espressif.com/dl/package_esp32_index.json

        Go to Tools > Board > Board Manager, search for "ESP32", and install it.
    Select the ESP32 board:
        Go to Tools > Board > ESP32 Dev Module (or the appropriate ESP32 variant).
        Select the correct COM port under Tools > Port.

4. Upload the Code

    Open the temperature_monitoring.ino file from the repository in Arduino IDE.
    Upload the code to your ESP32 by clicking the Upload button (right arrow).

5. Monitor the Output

    After uploading, open the Serial Monitor from the Tools menu (or press Ctrl+Shift+M).
    Set the baud rate to 115200 (or as specified in the code).
    The temperature readings from the LM35 sensor will start displaying in Celsius on the serial monitor.

Code Explanation

The provided Arduino code reads analog values from the LM35 sensor and converts them into temperature in Celsius. The result is then displayed on the Serial Monitor.

// Define the analog input pin
const int lm35Pin = 34;  // Change if using a different pin

void setup() {
  // Start the serial communication
  Serial.begin(115200);
  // Configure the LM35 sensor pin
  pinMode(lm35Pin, INPUT);
}

void loop() {
  // Read the analog value from the LM35 sensor
  int analogValue = analogRead(lm35Pin);
  
  // Convert the analog value to temperature in Celsius
  float voltage = (analogValue / 4095.0) * 3.3;  // ESP32 ADC is 12-bit (0-4095)
  float temperatureC = voltage * 100.0;  // LM35 outputs 10mV per degree Celsius
  
  // Print the temperature to the Serial Monitor
  Serial.print("Temperature: ");
  Serial.print(temperatureC);
  Serial.println(" °C");

  // Wait for a while before reading again
  delay(1000);  // Delay in milliseconds (1 second)
}

Key Points:

    analogRead(): Reads the analog value from the LM35 sensor.
    voltage: The analog value is converted to a voltage by dividing by the ADC resolution (4095 for a 12-bit ADC) and multiplying by the reference voltage (3.3V for the ESP32).
    temperatureC: The LM35 outputs 10mV per degree Celsius, so the voltage is multiplied by 100 to get the temperature in Celsius.

#OUTPUT

![image](https://github.com/user-attachments/assets/eaaa0862-bca6-4bd2-8b5b-e387cb78eb43)

Troubleshooting

    No Output on Serial Monitor: Ensure that the correct COM port is selected and that the baud rate in the Serial Monitor matches 115200 (or whatever is specified in the code).
    Incorrect Temperature Values: Verify that the LM35 is connected properly. Ensure that the ESP32's ADC pin is used for analog input and that the sensor is powered correctly.

Conclusion

With this project, you can easily monitor temperature in real-time using an ESP32 and LM35 sensor, with readings displayed on the serial monitor. This setup can be expanded to include data logging, cloud integration, or alert systems for temperature thresholds

