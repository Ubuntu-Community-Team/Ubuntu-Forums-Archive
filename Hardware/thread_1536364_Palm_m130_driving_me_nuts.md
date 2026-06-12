---
title: "Palm m130 driving me nuts"
date: 2010-07-22
forum: Hardware
---

### Post by souta95 on 2010-07-22
I am having two issues with my old Palm m130.  I am using Xubuntu 10.04, and have a USB cradle.  Also, I have loaded the visor module.

The first one is that I can't get "/dev/pilot" to work properly in J-Pilot.

I can sync it when I set the device to /dev/ttyUSB0 or /dev/ttyUSB2 and so on (depending on what it decides to show up as).

I have tried messing around creating a .rules file, and have tweaked it to be this (based on the examples here:  [https://help.ubuntu.com/community/PalmDeviceSetup):](https://help.ubuntu.com/community/PalmDeviceSetup):)

```
BUS="usb", SYSFS{product}="Palm*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"
```

The file name is "custom-palm.rules" but I had also tried "010-custom-palm.rules"

After pressing the hotsync button it shows up in lsusb as:

```
Bus 005 Device 028: ID 0830:0050 Palm, Inc. m130
```

This is the messages that J-Pilot puts out in its litle window on the bottom:

```
****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot No such device
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished.
```

The serial speed is set to 115200, which is what Palm Desktop used for it.

The other issue that I have is that I can't install programs to it using J-Pilot.  After going to File > Install and selecting one or multiple .prc files to install clicking on the hotsync button brings the install program dialog box again, rather than performing a hotsync.  Does having an SD card installed in the palm have anything to do with this?

I also have Evolution and Gnome-Pilot installed but couldn't make much sense of them, though I did get Gnome-Pilot to do an initial sync when configuring it for my device.

Thanks in advance

---

### Post by souta95 on 2010-07-22
I managed to figure out syncing with Evolution :D

My issue was that the palm pilot decided to show up as a different /dev/ttyUSB# than what gnome-pilot was configured to (which goes along with the /dev/pilot issue).

I still am having trouble with installng programs on it.

J-Pilot is still doing weird stuff, and when I tried gpilot-install it gave me a command not found error.

Also, I forgot to mention that I am using 64-bit Xubuntu.

---

### Post by souta95 on 2010-07-22
Well, one problem solved, I can now install files.

THe website that I read about installing using Gnome-Pilot and the command line had a typo.

Its "gpilot-install-file <filename>" not "gpilot-install file <filename>"

I set up a custom open-with command so all I have to do is double-click a prc file then press the hotsync button on the cradle to sync it.  I'll do the same for a pdb file when I have the need.

Now I need help with getting /dev/pilot to work properly.

---

