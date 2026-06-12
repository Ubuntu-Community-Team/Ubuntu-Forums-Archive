---
title: "udev rule for graphics tablet"
date: 2008-09-07
forum: Hardware
---

### Post by johanhartman on 2008-09-07
I am trying to get my graphics tablet working. Its an Aiptek 600u slimtablet. Now it seems that this is a solved problem looking at [this]("http://ubuntuforums.org/showthread.php?t=477287") thread,  especially post #9.

The problem is, I do not have enough experience to get that udev rule working... not even as far as getting the terminal to understand it. Could someone please help me out a little with implementing this rule so I can finally use my graphics tablet.

---

### Post by DoctorMO on 2008-09-11
You need to add the text

> BUS=="usb", KERNEL=="event[0-9]*", SYSFS{idVendor}=="172f", SYMLINK+="input/aiptek", OWNER="root", MODE="0666"

All on one line, to the file /etc/udev/rules.d/66-aiptek.rules

Each rules file contains a list of things to check for a device and thigns to do when it files them. The rule above looks for Vendor 172f (I assume the usb code for Aiptek) and creates an input symlink to /dev/input/aiptek

The rest of the instructions on that page get xorg config to use the aiptek input correctly.

---

