# TASK 4: Speech Recognition System

## Objective
To build a basic speech recognition system for command-based control of devices using an embedded system.

## Components Required
- Arduino Uno
- Voice Recognition Module / Mobile Voice App
- Bluetooth Module (HC-05)
- Relay Module
- LED / Appliance
- Jumper Wires

## Working Principle
Voice commands are given through a mobile application. The commands are converted into text and sent to the Arduino via Bluetooth. The Arduino processes the command and controls the connected device.

## Circuit Description
- Bluetooth TX → Arduino RX
- Bluetooth RX → Arduino TX
- Relay connected to digital pin 8
- Device connected through relay

## Arduino Code
```cpp
char command;
int relayPin = 8;

void setup() {
  pinMode(relayPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  if (Serial.available()) {
    command = Serial.read();

    if (command == 'O') {
      digitalWrite(relayPin, HIGH);
      Serial.println("Device ON");
    }
    else if (command == 'F') {
      digitalWrite(relayPin, LOW);
      Serial.println("Device OFF");
    }
  }
}
