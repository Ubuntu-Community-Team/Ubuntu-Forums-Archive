---
title: "Scanner permissions isuue"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Marcin Pisz on 2009-10-17
I have a problem with my Epson scanner:confused:
   
  I have just installed version 9.1 Beta on my computer to try out for a couple of weeks before the final version comes out. This will give me time to evaluate the software before my hard drive comes in from repair. I am running the 64-bit version of the software. I have installed drivers for the Epson perfection scanner 4490. I downloaded the 64-bit version of the drivers from Avasys. These are designed for version 8.10 and later. They already come as deb packages. I simply downloaded and installed both packages and I can only get the scanner to work perfectly if I run the Iscan software that gets installed with the driver using sudo from the commandline. Both Xsane and the proprietary software cannot access the scanner if I run it the normal way from the menu. If anybody has any suggestions of how to make this work, and have used this software on the distribution please let me know. It would also be great if this bug got fixed before the final release of the software.
   
  This is completely a side note that maybe should not be stated in this thread. But I'm doing it anyway, I wish Ubunu installed the proprietary drivers for the scanner the same way it's able to install NVIDIA drivers for my graphics card.
   
  To be totally off-topic this is the first version of this distribution that the 1.85 NVIDIA drivers do not install properly. After endlessly searching the Internet I found the solution and it simply involves adding the following line to the X. Windows configuration file under the screen section. 
   Device "Default Device"
  it's also interesting to note that if I install version 1.73 of the software the driver seems to work fine. Or at least as fine as a dove or those on my system. I have a dual monitor system with identical to monitors, and ever since he ever received the system the distribution cannot recognize one of the monitors. It sees the monitor but I have to acquire and use the EDID file data generated from the other monitor and forced the driver to see the other monitor as being identical to the first one. I do this by using the following command
  Device Section

Option         "CustomEDID" "DFP-0:/etc/X11/IIncedid.bin; DFP-1:/etc/X11/IIncedid.bin"
   
  If I don't do this, it thinks that one of the monitors is a generic monitor with a 640 x 480 resolution. I'm not sure if this is a hardware problem on the monitor, but when I boot into Microsoft Vista I did not get this problem. Windows seems to recognize both monitors automatically. Since I have a workaround I don't think I need any advice on this problem, I'm just making other people aware of it and of the solution. If you're going to use the solution above make sure you put the sign at the end of the section.
   
  Any help on the permissions would be great thanks.

---

### Post by myoldhouse on 2009-10-30
I have the same scanner (Epson Perfection 4490 Photo) and the same problem with permissions in the release version of 9.10 Karmic.

All worked well in 9.04, a normal user could access the scanner from Xsane or Epson's iScan or (with a bit of jiggery-pokery required on a 64 bit system) VueScan.

In 9.10, it seems the way the scanner is made available to non root users has changed in ways that are not clearly documented. In 9.04, I believe the HAL daemon (hald) used to take care of the detection of the scanner and setting the permissions for normal users but I recall reading somewhere that in 9.10 this method is now "deprecated" and udev is used instead. I don't pretend to know what this means, but it gave me a clue to a workaround that got my 4490 scanner working for normal users again in 9.10 64 bit.

The clue was that udev is now used. I looked in /lib/udev/rules.d and found a rules file "50-udev-default.rules" and it had a line for usb ports that said:

SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"

This was at line 58 in my rules file. I changed the MODE= entry to read MODE="0666" and saved the file (you have to edit this file as the root user as it is a system file). Basically this change makes all usb ports readable and writable by ordinary users. 

I documented this change with comments so the full change now looks like this:

# libusb device nodes
# Changed MODE to 0666, instead of 0664, so scanner would work
# for normal user and not just root. RJ Oct 29, 2009.
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"

You don't have to reboot or logoff for this change to take effect. Just turn your scanner on and off or unplug and replug its usb cord and the system will re-detect the scanner using the new permissions.

I also tried to make a rule in the /etc/udev/rules.d folder, which is normally where one would make changes for a specific device but I couldn't manage to concoct a rule that worked. Only the change to the "50-udev-default.rules" file in the /lib/udev/rule.d worked for me.

Give it a try, it may work for you as well. :)

---

### Post by cpeachey on 2009-10-30
I think I need to do this. My SCX4200 print/scanner only scans via sudo/xsane.
I have found the line to be changed but....
what command do I type in Terminal to edit the file please?
Chris

---

### Post by myoldhouse on 2009-10-30
To edit the file 50-udev-defaults.rules from a terminal use the following:

$ gksu gedit /lib/udev/rules.d/50-udev-defaults.rules

This will prompt you to enter your password and then open the file in Gedit with root privileges. Make the change in the line described in message 2 and save the file and you should be good to go.

---

### Post by myoldhouse on 2009-11-04
Message deleted by author.

---

### Post by axel112 on 2009-12-20
> **myoldhouse said:**
> To edit the file 50-udev-defaults.rules from a terminal use the following:

$ gksu gedit /lib/udev/rules.d/50-udev-defaults.rules

This will prompt you to enter your password and then open the file in Gedit with root privileges. Make the change in the line described in message 2 and save the file and you should be good to go.

Hi there.

Works for me. :)

Ubuntu 9.04
Brother dcp-117c

Xsane worked if running as root "gksudo xsane", but not as a ordinary mortal. Changing the udevrule, switching the printer/scanner on/off, saved the day.

Thanks! /axel

---

