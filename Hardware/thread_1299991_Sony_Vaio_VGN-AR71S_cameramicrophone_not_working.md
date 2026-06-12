---
title: "Sony Vaio VGN-AR71S camera/microphone not working"
date: 2009-10-24
forum: Hardware
---

### Post by rofed69 on 2009-10-24
Well, I have a Sony Vaio VGN-AR71S laptop which I bought last year and was forced to switch to Ubuntu only since I used to have both Ubuntu and Vista installed, but Vista needed formatting every 3-4 months and I just got tired. Now however, I can't seem to get the integrated camera working and I don't want to buy another one (I tend to move around a lot and it would be a pain).... Anyone got any ideas on how to get it working?

---

### Post by lensman3 on 2009-10-24
If you do from a command text window "mesg | more", do you see somewhere in the list the camera?  This should dump out the hardware specifics.  You are looking for something like "usb-??" and then a description of your camera.

If the camera is a usb device then doing the command "/sbin/lsusb" should show the device.

If it doesn't show up as a usb device it probably is on the pci bus, so do the command "lspci" and (hopefully) it should show up there.  The first number is the lspci for the device need written down.  Then do "lspci -n" and find the number you wrote down.  In that line of number there will be a number that is of the form "10ec:8168" (4 numbers - : -4 numbers).  Take those 8 digits and do a google search for "linux 10ec:8168".  Those 8 numbers are a device/manufacture unique number.  The google search should find the driver that will need to be installed.  You can't be the first person to have this problem,  somebody else will have solved it (for you).

---

