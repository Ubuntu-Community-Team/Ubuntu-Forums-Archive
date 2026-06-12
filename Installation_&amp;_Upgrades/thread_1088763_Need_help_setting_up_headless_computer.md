---
title: "Need help setting up headless computer"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by twisted_hick on 2009-03-06
Hi I could use some help setting up a headless seedbox. I've gotten ubuntu 8.10 installed and everything is running fine except when it comes to the hard drives mounting. so I have three questions 

1. How do I edit the fstab file to auto mount the hard drives  
Here's the output of fdisk -l
> Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000816ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         978     7855753+  83  Linux
/dev/sda2             979        1027      393592+   5  Extended
/dev/sda5             979        1027      393561   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    b  W95 FAT32

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c6c3c6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4865    39078081    b  W95 FAT32

Disk /dev/sdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x799a8dc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        2434    19551073+   b  W95 FAT32

 and here's the out put of cat /etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a7e5ab9d-0be9-41ef-aef8-df6b5078151a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7e87b511-dcc8-43ce-8723-a969ce04d826 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I've removed the CD-rom and replaced it with a hard drive.

2. I have logged in using vnc and with the monitor connected the resolution was what I set it up to be 1024x768. When I disconnect the monitor and restart the system I end up with 800x600 as the only option. that one I am at a loss as how to even attempt to resolve that issue. 
output from lspci 
> 00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
02:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)

 lspci -v -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
	Subsystem: Compaq Computer Corporation Device 0034
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
	Memory at 44000000 (32-bit, prefetchable) [size=64M]
	Memory at 40600000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [dc] Power Management version 2

Here's the xorg.conf file
> 
Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

3. I was wondering how to I set up a program to run on another hard drive instead of the the main one with the OS on it ? do I just create a file names /usr/shared and install the program there ?

---

### Post by twisted_hick on 2009-03-07
well to all who's read this post  problem #1 is solved  Now it's on to number two.  much love and thanks go out to forestpixie's reply to alan_uk's request made back on dec 5th 2008 worked like a charm to get the hard drives mounted and permissions set.

---

### Post by twisted_hick on 2009-03-09
Well I found a post that answered my third question on how to add a program to start at boot  and it used a gui :) Woo Hoo here's the link if anyone is interested. [http://ubuntuforums.org/showthread.php?t=727881&highlight=add+program+start]("http://ubuntuforums.org/showthread.php?t=727881&highlight=add+program+start")

---

### Post by Neo_The_User on 2009-03-09
> **twisted_hick said:**
> Well I found a post that answered my third question on how to add a program to start at boot  and it used a gui :) Woo Hoo here's the link if anyone is interested. [http://ubuntuforums.org/showthread.php?t=727881&highlight=add+program+start]("http://ubuntuforums.org/showthread.php?t=727881&highlight=add+program+start")

Glad you figured it out. :popcorn::popcorn::popcorn::popcorn::popcorn: :popcorn:

---

