---
title: "External hard drive not properly disconnected no longer detected"
date: 2009-02-12
forum: Hardware
---

### Post by burbanom on 2009-02-12
Hello, 
I've been an Ubuntu user for about 3 years now and so far I've been able to solve all issues that have arisen by looking around the web. This problem, however, I cannot find a solution for. 
I turned off the external hard drive while shutting down my laptop (Ubuntu 8.04), because I was in a hurry. Next time I tried to use it the drive wouldn't mount. I have looked around and seen that it's recommended using a number of commands for which I give the output I got:

```
burbanom@machine2:~$ dmesg | tail
[ 4911.770627] usb 5-1: configuration #1 chosen from 1 choice
[ 4911.772792] scsi9 : SCSI emulation for USB Mass Storage devices
[ 4911.776978] usb-storage: device found at 10
[ 4911.776987] usb-storage: waiting for device to settle before scanning
[ 4912.077078] usblp0: USB Bidirectional printer dev 10 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1722
[ 4912.077097] usbcore: registered new interface driver usblp
[ 4916.771977] usb-storage: device scan complete
[ 4916.773979] scsi 9:0:0:0: Direct-Access     Canon    MP220 series     1050 PQ: 0 ANSI: 2
[ 4916.779794] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 4916.779881] sd 9:0:0:0: Attached scsi generic sg2 type 0

```

```

burbanom@machine2:~$ lsusb
Bus 005 Device 010: ID 04a9:1722 Canon, Inc.
Bus 005 Device 009: ID 059b:0370 Iomega Corp.
Bus 005 Device 006: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 005: ID 050d:0013 Belkin Components
Bus 005 Device 004: ID 046d:0992 Logitech, Inc.
Bus 005 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 002: ID 0424:2514 Standard Microsystems Corp.


```

```
burbanom@machine2:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              20G  7.2G   12G  39% /
varrun               1009M  320K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   72K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M   39M  970M   4% /lib/modules/2.6.24-23-generic/volatile
/dev/sda3              76G   42G   30G  59% /home
/dev/sda2              15G   12G  2.0G  86% /home/burbanom/Windows

```

The lsusb output is the only one that shows that the drive is still recognized (Iomega 1TB). 

I have rebooted the computer, plugged the drive to a Vista laptop, an XP laptop, used Puppy Linux (I generally use it for recovery purposes) and also came across the program testdisk, which seems pretty good from what I've read, but it doesn't detect the drive either. Anybody have any suggestions? This drive is big (at least for me) and it has all my music, films, photos, system backups, virtual machines other distros that I play with in my spare time, etc. Can't emphasize how important it is to me to get it working once more. 

Thanks in advance

---

### Post by burbanom on 2009-02-13
Some help, please??
I would say that if I can't solve this I will change to a Redmond based OS to attract attention, but there's no risk of that happening any time soon. I just need my media back.

---

### Post by Gramps on 2009-02-13
So your saying that if you plug it into a Vista computer that it didn't see the drive either? How is the drive formated?

---

### Post by burbanom on 2009-02-14
Yeah, I've plugged it into XP and Vista computers as well as another linux distro called Puppy and it doesn't work with any of them either. I have two partitions of about 500MB each on the drive. Both are ext3.

---

### Post by burbanom on 2009-02-14
Help please

---

### Post by Gramps on 2009-02-15
With the file system being ext3 I don't know if XT or Vista will see it at all.

From a terminal install usbview using sudo apt-get install usbview
then at the prompt enter usbview a gui screen will come up with a list of all the usb devices that are seen by the system. Is you drive listed? If you highlight it the right screen will give you all kinds of info about the device.

You might also want to download the 8.10 live-cd and boot with it to see if the results are different.

---

### Post by burbanom on 2009-02-16
Thanks for the reply, 
I got usbview and this is the output from it

```

External HD
Manufacturer: Iomega
Serial Number: 152D20329000
Speed: 480Mb/s (high)
USB Version:  2.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 059b
Product Id: 0370
Revision Number:  0.00

Config Number: 1
	Number of Interfaces: 1
	Attributes: c0
	MaxPower Needed:   2mA

	Interface Number: 0
		Name: usb-storage
		Alternate Number: 0
		Class: 08(stor.) 
		Sub Class: 06
		Protocol: 50
		Number of Endpoints: 2

			Endpoint Address: 81
			Direction: in
			Attribute: 2
			Type: Bulk
			Max Packet Size: 512
			Interval: 0ms

			Endpoint Address: 02
			Direction: out
			Attribute: 2
			Type: Bulk
			Max Packet Size: 512
			Interval: 0ms

```

I have not yet tried one of the live distros because I had used Puppy, but I will give 8.10 a go when I get back from college. Thanks for the advice.

---

### Post by Gramps on 2009-02-16
I know there are some auto mounting problems with external usb devices on 8.04 that are supose to be fixed in 8.10. I have 8.10 and am not experiencing any problems with any of my usb devices.

At least it appears that you external usb hd is alright so you music should be intact.

I will assume that you tried mounting it manually.

Look in this file and see what's there. /proc/sys/kernel/hotplug mine on 8.10 is empty and 0 bytes it stays that way even if I plug an usb device in. I don't know what it should be on 8.04

---

### Post by burbanom on 2009-02-17
I tried the live 8.10, but it didn't detect the drive either. I have not yet tried to mount it manually. The thing is that I had the drive for several months and never had any problem with automounting on 8.04. Will check the file you recommended. Thnaks

---

### Post by zgembo on 2009-02-25
This is the output of "usbview":

"Can not open the file /proc/bus/usb/devices
Verify that you have USB compiled in your kernel, have the USB core modules loaded and have the usbdevfs file system mounted."

My comp. doesn't recognize my external HD. Any idea what to do?

---

