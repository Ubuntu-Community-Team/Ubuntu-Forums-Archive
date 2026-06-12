---
title: "Fresh Kubuntu install wont recognize a USB audio converter"
date: 2015-04-16
forum: Hardware
---

### Post by Socinus on 2015-04-16
Simplistic problem. I have a USB audio converter to give me an audio jack but when I installed Kubuntu it stopped recognizing the device. I uplugged it and replaced it but the problem persists.

---

### Post by gordintoronto on 2015-04-17
Kubuntu 14.04? What USB audio converter? Run this command: lsusb
Copy/paste one line into your message, the one which is for the audio converter.

Eg. for my webcam:
Bus 008 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

You say it stopped recognizing the device. What OS was recognizing the device previously?

---

### Post by Socinus on 2015-04-17
> **gordintoronto said:**
> Kubuntu 14.04? What USB audio converter? Run this command: lsusb
Copy/paste one line into your message, the one which is for the audio converter.

Eg. for my webcam:
Bus 008 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

You say it stopped recognizing the device. What OS was recognizing the device previously?

Bus 006 Device 002: ID 0d8c:0008 C-Media Electronics, Inc. 

I ran XP on this machine before and it worked with no issues.

FIXED: I had to go to the Systems App and tell it to prefer the installed audio hardware over the onboard hardware in the Multimedia tab.

---

