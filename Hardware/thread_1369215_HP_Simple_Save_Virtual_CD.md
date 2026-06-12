---
title: "HP Simple Save Virtual CD"
date: 2009-12-31
forum: Hardware
---

### Post by zean on 2009-12-31
I have an HP Simple Save storage backup device, and it has this very very very very annoying virtual CD, that automatically mounts when I plug in the device.

Now, it does not ruin the effect and power of the device. It's still got 1 TB (or more accurately when read, 930 GB) of storage, and that's fine. However, I really, really, really hate this virtual CD that automatically mounts every time I load the device. It's meant so that, if plugged into a windows computer, it automatically loads the proprietary software that came with the hard drive. This is very annoying. I don't use windows, and I don't appreciate it loading a virtual CD drive.

Does anyone know how to get rid of this virtual CD Drive?

---

### Post by unsungboxer on 2010-01-17
im having the same issue.  I checked hidden files on the simplesave drive to see if there was an ISO thats being mounted.  no dice.  Any thoughts?

According to properties it it has 0mb filesize, no contents, and a isofs filesystem.  Its location is in /media

---

### Post by muckz on 2010-02-05
The Virtual CD is in the control board's firmware, not on the hard drive itself. I deleted the partition, formatted the drive, and the CD drive still mounts.

In Windows, I disabled it through the Device Manager. Not sure how to do this in Linux, though I'm sure there's a way not to automount this particular unit.

---

### Post by Bremm on 2010-03-03
> **muckz said:**
> The Virtual CD is in the control board's firmware, not on the hard drive itself. I deleted the partition, formatted the drive, and the CD drive still mounts.

In Windows, I disabled it through the Device Manager. Not sure how to do this in Linux, though I'm sure there's a way not to automount this particular unit.

I solved this problem today with a nice tool: usb-modeswitch

$ usb_modeswitch -W -v 03f0 -p 4607

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Taking all parameters from the command line

DefaultVendor=  0x03f0
DefaultProduct= 0x4607
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent= not set
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 105 on 002
skipped 1 class/vendor specific interface descriptors
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 104 on 002
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 002 on 002
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 115 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device

Looking for default devices ...
 Found default devices (1)
Accessing device 115 on bus 001 ...
Using endpoints 0x02 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: HP      
 Product String: External HDD    
Revision String: 1028
-------------------------

Device description data (identification)
-------------------------
Manufacturer: HP
     Product: External HDD
  Serial No.: 574341563533383830373534
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

---

### Post by darjeeling on 2010-06-02
> **Bremm said:**
> I solved this problem today with a nice tool: usb-modeswitch

$ usb_modeswitch -W -v 03f0 -p 4607

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Taking all parameters from the command line

DefaultVendor=  0x03f0
DefaultProduct= 0x4607
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent= not set
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 105 on 002
skipped 1 class/vendor specific interface descriptors
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 104 on 002
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 002 on 002
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 115 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device

Looking for default devices ...
 Found default devices (1)
Accessing device 115 on bus 001 ...
Using endpoints 0x02 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: HP      
 Product String: External HDD    
Revision String: 1028
-------------------------

Device description data (identification)
-------------------------
Manufacturer: HP
     Product: External HDD
  Serial No.: 574341563533383830373534
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

You are officially the man.

---

### Post by chaeron on 2010-06-07
> **Bremm said:**
> I solved this problem today with a nice tool: usb-modeswitch

$ usb_modeswitch -W -v 03f0 -p 4607



Tried that...didn't seem to work....here is what I got as output:

```

* usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Taking all parameters from the command line

DefaultVendor=  0x03f0
DefaultProduct= 0x4607
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
MessageEndpoint= not set
MessageContent= not set
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 003
usb_os_find_busses: Found 011
usb_os_find_busses: Found 009
usb_os_find_busses: Found 001
usb_os_find_busses: Found 010
usb_os_find_busses: Found 008
usb_os_find_busses: Found 004
usb_os_find_busses: Found 002
usb_os_find_busses: Found 007
usb_os_find_busses: Found 006
usb_os_find_busses: Found 005
usb_os_find_devices: Found 007 on 003
skipping descriptor 0x21
skipped 1 class/vendor specific endpoint descriptors
usb_os_find_devices: Found 006 on 003
usb_os_find_devices: Found 004 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 003 on 003
usb_os_find_devices: Found 002 on 003
usb_os_find_devices: Found 001 on 003
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 002 on 011
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 011
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 009
usb_os_find_devices: Found 002 on 001
usb_os_find_devices: Found 003 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 010
usb_os_find_devices: Found 001 on 008
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 004 on 002
usb_os_find_devices: Found 003 on 002
usb_os_find_devices: Found 002 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 007
usb_os_find_devices: Found 003 on 006
skipped 1 class/vendor specific interface descriptors
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 002 on 006
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 006
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 001 on 005

Looking for default devices ...
 No default device found. Is it connected? Bye.

```

Any ideas why it's not finding the HP drive?  It's definitely connected.

Thanks!

---

### Post by chaeron on 2010-06-07
Nevermind.....I had to use a different product code for my HP drive as follows:

usb_modeswitch -W -v 03f0 -p 4507

That did the trick!

Thanks!

---

### Post by chaeron on 2010-06-07
OK...so how to easily make this permanent across reboots?

It requires sudo to run, so it's kinda hard to script it at the user level on startup

---

### Post by simosx on 2010-06-15
The idea is that when you install the program properly, it will be called automatically by the system when your hard disk is connected to your computer.

Here is the project page,
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Ubuntu comes with a version of the 'usb-modeswitch' which you can install and configure. Install using your package manager, package 'usb-modeswitch'.
You need to configure the device ID for this external hard disk; you need to put those command line parameters in the configuration file of usb-modeswitch and you are done!

---

### Post by chaeron on 2010-06-18
OK...after puzzling over the rudimentary documentation on the web site for usb_modeswitch, I finally got it to run automatically for the HP Simple Save Drive.

I edited  /lib/udev/rules.d/40-usb_modeswitch.rules and added a new rule 
and then created a new device file in /etc/usb_modeswitch.d called 03f0:4507 with the appropriate content.

So now it runs automagically when the device is plugged in or the machine is rebooted. Cool!

However, when I run this automatically or with the manual command

```
sudo usb_modeswitch -W -v 03f0 -p 4507

```

It also seems to detach the driver and dismounts the actual USB drive, not just the virtual cd.

Any ideas on how to configure usb_modeswitch to only detach the usb driver and/or dismount the virtual CD image ONLY and leave the actual usb drive in place?

Thanks!

---

### Post by Luke2891 on 2010-10-24
This is probably an easy question, but where are you getting the product IDs from?  I can't find anything for HP sd320a.  Also I'm using 10.10, which already has usb_modeswitch installed and still nothing works.  

Any suggestions?

---

### Post by chuckiv on 2013-04-26
> **Luke2891 said:**
> This is probably an easy question, but where are you getting the product IDs from?  I can't find anything for HP sd320a.  Also I'm using 10.10, which already has usb_modeswitch installed and still nothing works.  

Any suggestions?

^^^bump^^^

I also would like to know how to use usb-modeswitch

The authors website does not have an explanation that a novice can follow :(

I have done apt-get install usb-modeswitch

Now what???

---

### Post by oldos2er on 2013-04-26
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

