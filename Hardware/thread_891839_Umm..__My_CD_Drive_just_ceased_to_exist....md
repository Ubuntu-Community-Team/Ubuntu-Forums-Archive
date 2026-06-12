---
title: "Umm..  My CD Drive just ceased to exist..."
date: 2008-08-16
forum: Hardware
---

### Post by LeoSolaris on 2008-08-16
I just rebooted it after installing sensors, and I noticed an extra mount point on my panel's mount applet. I ignored it for a little while I confirmed that sensors did something. (It just gave me my CPU temps, I feel jipped)

I decided to check it, and low 'n behold, it was my CD drive. I selected mount (which is strange because I have never had to manually mount my CD drive) and it gave me a mount error. It said that my special device /dev/scd0 did not exist!

I am confused as heck about this one. The button does not work while I am in Ubuntu, but it works just fine while the computer is at the BOIS password screen. It stops working in grub. It not the drive, it was working last I checked. (I haven't tested it in Windows yet, and I will here shortly.)

```
02:26 PM on Sat Aug 16 leo-laptop: ~$ lsusb
Bus 007 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
02:27 PM on Sat Aug 16 leo-laptop: ~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

```It's simply not recognized any more. I removed the stuff sensors automatically put in my /etc/modules 

Here is what /etc/modules looks like now:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc

```Edit: I did a search and it did not answer my question, but I can answer the question that was asked (and never answered in the post) about being able to access the CD drive in /media/cdrom. 

I can access the folder. CDrom and cdrom0 are still there, but it will not let me actually open the cd bay. (it is kinda weird that the button will not work.)

---

### Post by LeoSolaris on 2008-08-17
Bump. 

I am still lost. 

I have not been able to find out how to re-create /dev/scd0 so it points towards the cd player and /media/cdrom0

I really hope this is the right spot to put this...

---

### Post by finito on 2008-08-17
I had a problem Like this once, it turned out that one of my wires was loose. I don't know how it got loose but I found that out after getting a new DVD RW and when I went to install it I saw the wire (IDE) was very loose so I pushed it in and it started working. 

I would suggest looking in Bois to see if it's being detected, it could be some mount error.  

It could also be that your CD Drive has given out, How long did you have it and when was the last time you used it.

---

### Post by LeoSolaris on 2008-08-17
It's a 8 month old Dell Inspiron 1520.

To tell ya the truth the last I used it was to try out OpenSuse's LiveCD about 3-4 days ago.

I can still get it to work on boot up. I can load a LiveCD still, so it may be grub...   I need to check Windows on the other partition.

---

### Post by finito on 2008-08-17
in that case can you give me what it says in /etc/fstab

---

### Post by LeoSolaris on 2008-08-17
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=476ca36e-599d-4f02-a5bb-ae8e5bce9f2a / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=afe3194e-1cbf-4baa-a199-ee073062297d /home ext3 relatime 0 2
# Entry for /dev/sda5 :
UUID=4d46e982-9260-4eec-988a-f5d5c87f9172 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```

There's my fstab.  
I have been trying different changes to my fstab that I have found with some google searches, but so far I haven't had any luck.

I tried searching for it with this command... ```
 sudo lshw -C disk
``` but all I got was my hard drive.

---

### Post by LeoSolaris on 2008-08-17
Alright, just back from my windows' partition. Not recognized at all. I noticed on one of the google searches I did that someone was having a similar problem and it turned out to be grub's fault.

I am going to try purging grub with synaptic then reinstalling it.  Maybe that will restructure it's drive list...

---

### Post by LeoSolaris on 2008-08-18
Ok...   I fixed the initial problem. I discovered that for some reason the BIOS had module bays turned off. For the life of me I cannot remember doing that. I discovered, much to my horror, that when I made an attempt to use grub2, it would not boot from the hard drive.

No worries I thought, I can fix it with a LiveCD, BIOS still recognizes the drive...   Ya  LiveCD would not boot....    ok now is a good time to panic for a moment or two.

While combing BIOS, I noticed the module bays, and ticked it back to on. Poof, working.

Now I am stuck...   I have my 8.04 disc on Live, and it will not just install a boot partition alone. I have yanked out my kernel, and I am preparing to labotomize my root partition so I can have a working boot partition.

Aaarg! Why on earth do they have a completely non-working grub avaliable in the repos?

I will get this solved the rest of the way. It will just take re-installing all of the software I will need really swiftly.

Thank you very much, friend!

---

