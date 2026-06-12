---
title: "how to disable webcam &amp; bluetooth"
date: 2009-07-21
forum: Hardware
---

### Post by cihanoz on 2009-07-21
Hi everyone,
I need to disable my USB webcam and bluetooth because I am doing some bandwidth tests with a specific USB device. What I want to do is to remove them from the output of lsusb so that I am sure all the bandwidth is allocated for the device I am testing. Current output of lsusb gives:
[B]Bus 005 Device 004: ID 05e1:0501 Syntek Semiconductor Co., Ltd WebCam, Chipset DC-1125 similar to 174f:a311 - Asus F2F, F2J, F3J, F3T, G1, Z53JA
Bus 003 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter[/B]
for the two devices. Note that neither of these devices are connected to any USB ports, they are both integrated to my notebook. I have searched the net and none of the tricks did not work me. For disabling bluetooth I tried:
hciconfig hci0 down
rmmod hci_usb
(could not find module hci_usb)

and for disabling webcam I tried the tricks at [http://ubuntuforums.org/showthread.php?t=502064](http://ubuntuforums.org/showthread.php?t=502064),
"echo 0..." simply doesn't work for me, and 
"modprobe -r gspca" can't find gspca module. 
Also [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1211371](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1211371) doesn't work because 
dmesg | grep *address* doesn't otput anything.

My Kernel version is 2.6.30, distro Ubuntu Ibex, and Notebook model is Asus F3JC.

---

### Post by cihanoz on 2009-07-22
just a quick correction, kernel version is 2.6.29, and it's compiled to run at 1000Hz timer frequency.

---

