---
title: "Cant see mobile phone USB"
date: 2008-11-08
forum: Hardware
---

### Post by theduffman on 2008-11-08
Fresh install of Intrepid with all updates.  I have an external usb powered hard disk that works fine.  I have a sony ericsson W980 mobile phone with 8gb memory and when i plug in to usb and select mass storage mode, to copy content to/from it as a usb stick nothing happens, nothing is mounted.  It works fine in windows.  Any clues?

---

### Post by skiold on 2008-11-14
Hi, exactly the same trouble here. I have a Nokia 3500c.
You can join to this thread [http://ubuntuforums.org/showthread.php?t=975622](http://ubuntuforums.org/showthread.php?t=975622) and find together a solution.

---

### Post by WWSmith36 on 2008-11-14
I think that this may be a permission issue.  Typical these devices(phones) are handled by udev.  

Create /etc/udev/rules.d/60-cell.rules
Then add similar code to this, obviouly replacing with your phone info

```
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end" 
# LG Phone 
SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6000", MODE="0666" 
LABEL="cell_rules_end" 

```
1004 and 6000 should of course be replaced with the relevant VID and PID.

To determine your VID/PID try lsusb

Hope this helps

---

### Post by mac.ryan on 2008-11-15
Although not the original poster, I tried that and did not solve the problem, unluckily. :(

---

