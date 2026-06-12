---
title: "touchscreen/gpsdevice on ultramobilepcs MIVVY um400+gigabyte U60"
date: 2008-11-22
forum: Hardware
---

### Post by gizmo_the_greater on 2008-11-22
MY PROB IS ABOUT GETTING USB-TOUCHSCREEN AND GPS-DEVICES TO WORK ON LETS SAY EXOTIC HARDWARE

im really getting crazy about that device and getting its componetns to work, its a mivvy ultra mobile pc (via C7-M, via cx700 graphics, touchscreen, bluetooth, wireless ... 

its technically (i assume) nearly the same like gigabyte u60 (if it had the same firmware i had tried the fuckking linuxdrivers from gigabyte) [the main difference seems to be that gigabyte supports firmware/bios updates and mivvy not ... i dont want to flash my mivvy with gigabyte firmware so i leave them where the are)

by the way, all the other people on the net reported about probs with the vga-chipset (they all have used vesa). my unit is running quite well with the openchrome drivers (when i've got all usable i'd like to create a independent manual for that hardware, if its mivvy or gigabyte)

i have 2 problems and my head is smoking about them:

[B]
1.) touchscreen[/B]

u need that piece, forget about mice or the integrated touchpad! I WANT A WORKING TOUCHSCREEN.

None of the two following HOWTOS worked:

THE SUPPORT FROM MIVVY:
[http://www.mivvy.eu/de/index.php?page=linux](http://www.mivvy.eu/de/index.php?page=linux)

THE UBUNTU U60 SOLUTION:
[http://ubuntuforums.org/archive/index.php/t-627679.html](http://ubuntuforums.org/archive/index.php/t-627679.html)

my xorg.conf+modprobe.d/blacklist is attached

thats the lsusb-output for the touchscreen:

Bus 003 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen


additional info: 

i've had installed ubuntu twice, first it crashed after messing around with xorgconf [my window-borders vanished, i'not shure why but i was playing around with  and after 4 hours of research i decided to reinstall because it was a fresh install]) but that time the touchscreen worked (i was not able to calibrate it but it worked!!!!!!!!!!!)

[COLOR="Red"]I DONT EVEN HAVE AN IDEA TO SEARCH FOR A PROBLEM[/COLOR]
[B]
2.) GPS-module not working[/B]

how can i find out, which usb-device (device-node) is the attached gps-device (its a addon-module from mivvy and labeled "n-gps iGPS-EB-310A"

thats my lsusb-output for the device:

Bus 001 Device 006: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device

if tried to find its usb-device with "ls -lt /dev but none of the devices worked when i tried to use with "sudo gpsd /dev/****_of_and_die" 

my /proc/bus/usb is empty

[COLOR="Red"]HOW CAN I FIND OUT WHICK USB-DEVICE IN /dev IS LINKED TO A CORRESPONDING OUTPUTLINE (DEVICE/VENDOR-ID) FROM lsusb[/COLOR] (and if it is ... within windows it was marked as bridge so i dont even know if i can get that ******* device to work)
...

---

