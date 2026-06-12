---
title: "Acer Predator Helios 300 - Advanced Touchpad doesn't work"
date: 2018-06-09
forum: Hardware
---

### Post by amcsi2 on 2018-06-09
I have the latest Acer Predator Helios 300 laptop with Intel's hexa core processor in it, running Ubuntu 18.04.

Unfortunately the touchpad doesn't work at all.

I've already tried pressing the fn+touchpad button in case it was disabled by default.
In the BIOS I have the setting as "Advanced" touchpad which I needed for my dual-booted Windows to be able to use 2 finger scrolling.

What can I do to fix this and make the touchpad work?

---

### Post by schmolli-christian on 2018-10-18
Hi,

if you are still interested in a solution.

Switch the Touchpad mode in BIOS back to "Basic". Install the following driver in Windows 10 via Device Manager:
[https://drivers.softpedia.com/get/KEYBOARD-and-MOUSE/Elantech/ELAN-Touchpad-Driver-21-2-16-2-for-Windows-10-64-bit.shtml](https://drivers.softpedia.com/get/KEYBOARD-and-MOUSE/Elantech/ELAN-Touchpad-Driver-21-2-16-2-for-Windows-10-64-bit.shtml)

Just download and extract it. After that right click on the Windows button and choose Device-Manager. There search for your Touchpad and right click on it and choose "Update driver". Now choose driver from your PC and "Device...". Paste the path to the extracted driver and press ok. Accept and close the following alerts and restart the PC.
Now you can use two finger scoll on Windows (and the other standart actions) and you also can use the touchpad in Ubuntu.

---

