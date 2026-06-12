---
title: "Palm woes: udev not working properly (bug?)"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by In Pog Form on 2008-04-10
Related threads to this issue lack replies and details

Running Ubuntu 7.10
udev fails to create the proper symlink for the Palm device:

Tailing /var/log/messages I can see the device connect when I hit the HotSync button:

[I]Apr 10 10:33:24 fileserv kernel: [129475.386409] usb 2-2.2: new full speed USB device using uhci_hcd and address 38
Apr 10 10:33:24 fileserv kernel: [129475.521476] usb 2-2.2: configuration #1 chosen from 1 choice[/I]

How some ever udev fails to create the proper /dev entries

[I]$ ls /dev/ttyUSB* ; ls /dev/pilot
ls: /dev/ttyUSB*: No such file or directory
ls: /dev/pilot: No such file or directory[/I]


Despite lsusb seeing it:

*Bus 002 Device 039: ID 0830:0061 Palm, Inc.*


**Okay this part maybe classified as a bug:**

The line in /etc/udev/rules.d/60-symlinks.rules is as follows:

[I]# Create /dev/pilot symlink for Palm Pilots
KERNEL=="ttyUSB*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", \[/I]<carriage return here>
<35 instances of white space  here>*SYMLINK+="pilot"*

NOTES: 
[LIST]
[*]<notes thus by me since BB Code removed the white space>
[*]included carriage return, making it in fact two separate line.
[/LIST]
 
Changing that line to read...

*SUBSYSTEMS=="usb" , KERNEL=="ttyUSB*", ATTRS{product}=="PalmHandheld*|Handspring *|palmOne Handheld", SYMLINK+="pilot"*

... and subsequently restarting the udev daemon (*sudo /etc.init.d/udev restart*) accomplishes exactly nothing, leaving me where I started: without a working connection to my Palm device.

Why? 

Were the Palm devices left out of the kernel config?

---

