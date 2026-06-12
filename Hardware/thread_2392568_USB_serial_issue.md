---
title: "USB serial issue"
date: 2018-05-22
forum: Hardware
---

### Post by aidanrtaylor on 2018-05-22
Hello - I am definitely new so sorry if I miss any forum etiquette and please let me know if I do so! I believe this is a "hardware" issue, not sure how to proceed:

I'm running Xubuntu 18.04 - I'm fairly new to Linux but have learned a lot over the last few months.

I am working with a Teensy microcontroller in the Arduino IDE, and to cut the story short I'm getting very poor results using USB as a serial interface - it does work, it displays data correctly, but whether a message is large or small I can only seem to send about once per second. Any greater frequency than this will freeze up the port and I have to reset the Teensy. It's a very normal thing to do with Arduino like devices and I should be able to transfer data by serial at a much greater rate than this.

I have tried a number of Teensy boards (and I have used Teensy for a long time across a variety of computers) so I'm sure the MCU is not at fault, and the problem exists on every USB port on my laptop (some are 3.0 and others are 2.0). 

I have tried opening the port with the built-in Serial Monitor in the Arduino IDE and also with screen in Terminal, the problem is the same on both.

I don't want to assume anything here - I would really appreciate any advise on how to further diagnose this. Please and thank you!

---

### Post by aidanrtaylor on 2018-05-22
I found a work around which gets me a lot closer to normal behaviour - to only start printing serial messages once the port is opened - this isn't a particularly ideal solution but I can work with it. I'm not sure if that sheds any light on the issue?

```

int counter;

void setup() {
  Serial.begin(115200);

  while(!Serial);

}

void loop() {
  counter++;
  Serial.println(counter);
  delay(10);
}

```

---

