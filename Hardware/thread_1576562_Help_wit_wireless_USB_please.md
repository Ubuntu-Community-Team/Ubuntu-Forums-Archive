---
title: "Help wit wireless USB please"
date: 2010-09-17
forum: Hardware
---

### Post by dougalkerr on 2010-09-17
Hi folks

I have purchased a cheap and cheerful wireless USB device to use instead of hardwire to the router.
It is a Realtek or Ralink if you like model 2070.
I believe I have installed the software properly and it looks like I should be able to open a GUI to set the wireless up but, for the life of me I can't find the file that will open the GUI.
It seems to have been built using QT if I understand things correctly.
I no nothing about QT which probably doesn't help.

Any way in the Readme there is a whole host of information and examples to apply in Terminal by the looks of it. One example is as follows;

Config STA to Link with Ad-hoc and OPEN/NONE (Authentication/Encryption)
1. iwconfig rausb0 mode ad-hoc
2. iwconfig rausb0 key off
3. iwconfig rausb0 essid "AP's SSID"

Now I think I realize the last line is setting the name of the wireless signal so no problem there but, before I even get to that I can't get past 1. When I enter the code I get the message:
Error for wireless request "Set Mode" (8B06)
Set failed in device rausb0 ; No such device

So, I did lsusb and here is the line for the device;
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp.

It seems the system sees the device but, I don't undestand how to get it working.
Please help guide me through things - anyone.

Thanks.

---

