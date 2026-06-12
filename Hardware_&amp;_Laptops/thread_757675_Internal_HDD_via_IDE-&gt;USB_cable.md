---
title: "Internal HDD via IDE-&gt;USB cable"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by PouncingAnt on 2008-04-17
I've been trying for some time, with the help of information in these forums, to get the HDD from my old notebook, to mount into my existing ubuntu 7.10 installation.

I've had no luck, but I come prepared with the following information!

firstly, I tried getting it to work on Windows, no luck. And it doesn't auto-boot. However, I know the HDD is still intact since I can get it to work in the notebook I extracted it from (before the the poor thing overheats on me).

OK, so heres some info on the HDD in question, according to my new notebook....

lsusb output, before and after unplugging the USB/IDE cable from the device
notice the first entry for bus 3 displays a different nubmer after device once being plugged in

```
chris@FlamingBull:~$ lsusb
Bus 003 Device 013: ID 152d:2338 
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04bb:0113 I-O Data Device, Inc. 
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
chris@FlamingBull:~$ lsusb
Bus 003 Device 016: ID 152d:2338  
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04bb:0113 I-O Data Device, Inc. 
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

Removing the USB cable completely gives us:

```
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04bb:0113 I-O Data Device, Inc. 
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

sudo lshw relevent output (ie. this is the bit missing when unplugging the cable)
```
*-scsi:1
          physical id: 2
          bus info: usb@3:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             configuration: ansiversion=2
```

My searching on the forums has given me no good info on what to do next.
I've tried mounting, but fdisk doesn't show the device at all.

I welcome any help ^^, but try be patient with me, I'm on JST (thats Japanese Standard Time, not some kind of drug, btw :) )

---

### Post by daengbo on 2008-04-17
What operating system did this notebook hold? NT? What's the laptop model? Is the drive produced specifically for the notebook? Could the drive be encrypted?

Insert the drive and type 
> ls /dev/sdc*
sudo fdisk /dev/sdc
What do they say?

BTW, KST time here. ;)

---

### Post by PouncingAnt on 2008-04-17
```
chris@FlamingBull:~$ ls /dev/sdc*
/dev/sdc
chris@FlamingBull:~$ sudo fdisk /dev/sdc
[sudo] password for chris:

Unable to read /dev/sdc
chris@FlamingBull:~$ 
```

My old notebook was originally winXP, but I loaded up Ubuntu 7.10 on it, so the HDD in question should have a windows partition and Ubuntu partition (and swap too, I seem to recall being on a different partition)

The laptop was an evesham technologies machine. I dont have any of the manuals with me (they're still in England), so I can say any more than that.

Unfortunately I have no clues as to weather the HDD was specifically designed for it. But considering Evesham was a piddly little English company (that I think just went bust) I have an element of doubt about that.

---

