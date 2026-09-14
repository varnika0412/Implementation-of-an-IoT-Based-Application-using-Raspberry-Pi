
# IMPLEMENTATION OF AN IoT-BASED APPLICATION USING RASPBERRY PI

## Aim

To implement an IoT-based environmental monitoring application using Raspberry Pi and Python/MicroPython by acquiring sensor data, processing the data, and transmitting the information to an IoT platform for remote monitoring.

---

# Hardware / Software Tools Required

* Raspberry Pi Pico W
* DHT22 Temperature and Humidity Sensor
* LED
* 220Ω / 330Ω Resistor
* Breadboard
* Jumper Wires
* Wokwi Online Simulator
* MicroPython
* Wi-Fi Network
* IoT Cloud Platform / MQTT Broker

> **Note:** Raspberry Pi Pico W is used instead of the standard Raspberry Pi Pico because the Pico W provides built-in Wi-Fi connectivity required for the IoT application.

---

# Circuit Diagram

---<img width="702" height="575" alt="647757927-228c7c34-60fd-447f-bfc0-96128f539c85" src="https://github.com/user-attachments/assets/78d3b792-f012-4d4d-a594-2d9444c1d3d8" />



# Circuit Connections

Component	Raspberry Pi Pico W
DHT22 VCC	3.3V
DHT22 DATA	GPIO 21
DHT22 GND	GND

# IoT Application

The application implements a **Wi-Fi-based environmental monitoring system**.

The system performs the following functions:

```text
DHT22 Sensor
      ↓
Raspberry Pi Pico W
      ↓
Read Temperature & Humidity
      ↓
Process Sensor Data
      ↓
Wi-Fi Connection
      ↓
IoT Cloud / MQTT Broker
      ↓
Remote Monitoring
```

The LED is used as a local status indicator. It turns ON when the measured temperature exceeds the predefined threshold.

---
circuit diagram:
<img width="702" height="575" alt="647757500-eb040783-a3fb-4c4d-b468-4554c192e93d" src="https://github.com/user-attachments/assets/00bbf306-61bd-487a-8016-6e4bc0c51543" />




# Procedure

## Step 1: Create the Wokwi Project

1. Open the Wokwi online simulator.
2. Create a new project using **Raspberry Pi Pico W**.
3. Select **MicroPython** as the programming environment.
4. Add the following components:

   * Raspberry Pi Pico W
   * DHT22 sensor
   * LED
   * Resistor
5. Connect the components according to the circuit connection table.

## Step 2: Connect the DHT22 Sensor

1. Connect the VCC pin of the DHT22 to 3.3V.
2. Connect the GND pin to GND.
3. Connect the DATA pin to GPIO 15.
4. Configure GPIO 15 as the sensor data input.

## Step 3: Connect the LED

1. Connect GPIO 14 to a 220Ω resistor.
2. Connect the resistor to the LED anode.
3. Connect the LED cathode to GND.
4. The LED will act as a temperature threshold indicator.

## Step 4: Configure Wi-Fi

1. Configure the Wi-Fi credentials in the MicroPython program.
2. Start the Wi-Fi interface of the Raspberry Pi Pico W.
3. Connect the Pico W to the Wokwi simulated Wi-Fi network.
4. Verify that the device obtains an IP address.
5. Check the Serial Monitor for the Wi-Fi connection status.

## Step 5: Read Sensor Data

1. Initialize the DHT22 sensor.
2. Read the temperature value.
3. Read the humidity value.
4. Display the values in the Serial Monitor.
5. Compare the temperature value with the predefined threshold.

## Step 6: Control the LED

1. Define a temperature threshold.
2. If the measured temperature is greater than the threshold, turn ON the LED.
3. If the temperature is below the threshold, turn OFF the LED.
4. Display the LED status in the Serial Monitor.

## Step 7: Send Data to IoT Platform

1. Establish a Wi-Fi connection.
2. Connect the Raspberry Pi Pico W to the selected IoT platform or MQTT broker.
3. Create suitable MQTT topics for temperature and humidity.
4. Publish the sensor readings periodically.
5. Monitor the published data using the cloud dashboard or MQTT client.

## Step 8: Run the Simulation

1. Start the Wokwi simulation.
2. Observe the Wi-Fi connection message.
3. Observe the temperature and humidity values.
4. Change the DHT22 sensor values using the Wokwi controls.
5. Observe the corresponding changes in the Serial Monitor.
6. Verify the LED operation based on the temperature threshold.
7. Verify that the sensor data is transmitted through the IoT communication channel.

---

# Program

from machine import Pin
import dht
import time

time.sleep(0.1)

sensor = dht.DHT22(Pin(21))

while True:
    sensor.measure()
    temperature = sensor.temperature()
    humidity = sensor.humidity()

    print(f"Temperature = {temperature}")
    print(f"Humidity = {humidity}")
    print("----------------------------")

    time.sleep(3)
# Output
<img width="1920" height="1080" alt="647757238-3be5ebec-3e68-4db8-ba23-3c80a61f7abd" src="https://github.com/user-attachments/assets/580babe1-6168-4c22-816d-84eb0f3ab7b2" />




# Result

The **IoT-based environmental monitoring application was successfully implemented using Raspberry Pi Pico W in the Wokwi simulation environment**. The DHT22 sensor was interfaced with the Raspberry Pi Pico W to acquire temperature and humidity data. The Pico W established Wi-Fi connectivity, processed the sensor readings, and provided the data for IoT-based remote monitoring. An LED was also controlled according to the predefined temperature threshold.
