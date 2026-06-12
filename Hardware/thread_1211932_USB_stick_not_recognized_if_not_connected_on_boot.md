---
title: "USB stick not recognized if not connected on boot"
date: 2009-07-13
forum: Hardware
---

### Post by b0wter on 2009-07-13
Hey,
I've been using Ubuntu for some time now and there is one thing that bothers me. I don't remember that this happened from the beginning.
Whenever I connect a USB stick it is not recognized and /media/usbdisk is empty. It does not matter what kind of USB stick it is (so far I've tried 4) oder which USB slot I use. To use the device I have to plug in the USB device and then boot my laptop.

My laptop is a Thinkpad T400 (2765-TDG) and I'm using Ubuntu 9.04 (upgraded from 8.10).

---

### Post by PsyMonkey on 2009-07-13
I have the same problem with my desktop with my USB flash stick and USB 3G dongle.  Have to unplug and plug in again to get it to work/mount.

---

### Post by lncoll on 2009-07-13
To help we'll need more data, this is how to get some data to post here:

Open a terminal: Applications -> Accesories -> terminal, here you must execute some commands and post the results, first with the stick pluged on boot and working:

```
lsusb
```
```
blkid
```

The first one shows all the usb devices, and the second all the block units (disk partitions)

Unplug the device, wait a little, plug it again, wait a minute and do the same.

Post the results in this thread and we'll try to help you.

---

### Post by PsyMonkey on 2009-07-14
Looks like my USB Flash disk is working fine but my 3G is still giving the error.  Will post in separate thread since I don't think it is related to this issue.

---

### Post by b0wter on 2009-07-17
Ok... for some time the USB stick seemed to work fine, but today after trying to plug it in without booting it i got the following output:

**lusb**
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 17ef:1004 Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a5c:2145 Broadcom Corp. 
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**blkid**
```

/dev/sda1: UUID="ba27514d-b175-4c26-9813-70e64d3ed9fc" TYPE="ext3" 
/dev/sda5: UUID="3805f013-af02-4cb9-84ae-aab32f9c678b" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

```

When booting with the USB stick i get the following output:

**lusb**
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 17ef:1004 Lenovo 
Bus 001 Device 002: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a5c:2145 Broadcom Corp. 
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**blkid**
```

/dev/sda1: UUID="ba27514d-b175-4c26-9813-70e64d3ed9fc" TYPE="ext3" 
/dev/sda5: UUID="3805f013-af02-4cb9-84ae-aab32f9c678b" TYPE="swap" 
/dev/loop0: TYPE="squashfs"

```

Did I do something wrong or why is the output for blkid the same? Shouldnt there be at least another partition?

---

### Post by varun1786 on 2009-07-19
hey b0wter,

have you tried mounting the usb drive. When the device is connected at boot time it gets mounted automatically i think.

Click on the usb drive in ur file manager it should mount automatically else if your using gnome desktop click on** places on the top panel** and the usb drive will be listed just clik it.

else try this,

Open a terminal

$sudo mkdir /media/USB
$sudo mount /dev/sdb1 /media/USB

---

### Post by b0wter on 2009-07-21
Tried that but it didnt work. Gave me the following error mesg:

```
mount: special device /dev/sdb1 does not exist
```

:/

---

### Post by ak71vie on 2009-12-03
> **b0wter said:**
> Tried that but it didnt work. Gave me the following error mesg:

```
mount: special device /dev/sdb1 does not exist
```:/

I had the same problem, but could solve it by

> sudo apt-get install linux-backports-modules-`uname -r`

---

