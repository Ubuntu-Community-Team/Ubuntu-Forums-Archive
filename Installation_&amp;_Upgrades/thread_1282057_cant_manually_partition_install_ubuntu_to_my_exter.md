---
title: "cant manually partition /install ubuntu to my external harddisk"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by Meow27 on 2009-10-03
so ive read these threads and i dont see a solution here
([http://ubuntuforums.org/showthread.php?t=1069951&page=4](http://ubuntuforums.org/showthread.php?t=1069951&page=4))
([http://ubuntuforums.org/showthread.php?p=6754885#post6754885](http://ubuntuforums.org/showthread.php?p=6754885#post6754885))

my issue is the following set of pictures (in order, screenshot -> 1 -> 2)

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdf: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x515ccb5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       33387   268181046    7  HPFS/NTFS
/dev/sdf2           33388       38913    44387595    5  Extended
/dev/sdf5           33388       34024     5116671    b  W95 FAT32
/dev/sdf6           34025       34828     6458098+  83  Linux
/dev/sdf7           34829       35089     2096451   82  Linux swap / Solaris
/dev/sdf8           35090       38913    30716280   83  Linux

```


so as you can see, im using the beta of karmic. i want to install karmic (NOT AS A LiveCD!)on sdf8 (im being specific just to get to the point) 

as you can see there, i cant manually partition this drive as i could with a normal internal one. i want my data ntfs drive as is, and have a couple of livecds in the smaller partitions

ubuntu will only let me wipe out my external drive to proceed. i dont know how to get past this problem. its been like this ever since i tried it with intrepid

ive tried it with my internal intact, but due to some advice, this time i tried it with just my external attached (attached by usb)but the same problem is still there, it wont let me manually install ubuntu to one specific partition




is there any way to get rid of this problem? if there isnt any clear way, can i install it from the terminal, can someone show me a guide or teach me how?

thanks in advance. 
-meow
(if i havent given enough data, please indicate it)

edit--------------- every output and screenshot im posting is from a livecd
(for wins and lulz ill post this just in case)
```
ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
04:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
```

---

### Post by Meow27 on 2009-10-04
i have the same problem using the alternate cd

---

### Post by Habboblob on 2009-10-04
Good luck with fixing this problem.

Maybe you should try to format that to an ext3 with GParted.
That's only my guess.

Hope you get it fixed.:P

---

### Post by drs305 on 2009-10-04
I sent a PM to Meow27 but will post it here as well.

First, I wanted to check to see if he was using "gksu gparted" or "gksudo gparted". gksu/gksudo are preferred to "sudo" for invoking graphical apps as 'root'. Here is a link explaining it:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Secondly, I wondered if mounting a specific partition rather than the entire disk might allow gparted to work. I have many partitions, and often I mount only the partition I'm interested in for speed in loading. I suggested trying to mount one partition (i.e. the one he wanted to load Ubuntu on) to see if that particular one would mount - bypassing other partitions that might be causing problems.
The command to do this would be:
```

gksudo gparted /dev/sdXX

```
with XX being a specific partition, such as sdf1, sdf2, etc.

These were more "wonderings" than solutions, which is why I didn't post them here first.

---

### Post by Bucky Ball on 2009-10-04
Are you unmounting the partition? The only way to unmount an OS partition is with a Live CD (you can't unmount a drive when you are using the operating system on it).

---

### Post by Meow27 on 2009-10-04
> **drs305 said:**
> gksudo gparted /dev/sdXX


see the attached photo

so..... let me ask this: i remember seeing a guide for installing backtrack 4 beta, which had to me manually installed via the terminal. partitioning was done via commands, and so was the installation. 

is there anything of the sort someone can link to me please?
edit----
there is no difference if i run gksudo or sudo or gksu

---

### Post by oboedad55 on 2009-10-04
Have you tried Parted Magic? It's available as an iso and boots from a CD. You may be able to format the drive with this: [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by Bucky Ball on 2009-10-04
> **Bucky Ball said:**
> Are you unmounting the partition? The only way to unmount an OS partition is with a Live CD (you can't unmount a drive when you are using the operating system on it).

? It is a waste of time invoking gparted to work on the partition your OS is running on. (it is in System->Administration->Partition Manager so don't bother with 'gksudo' in a terminal as you will be asked for your password when you invoke the GUI anyhow).

The ONLY way to resize the partition (your currently running OS is on) is to use the Gparted live cd or the Ubuntu one.

---

### Post by Meow27 on 2009-10-04
> **Bucky Ball said:**
> ? It is a waste of time invoking gparted to work on the partition your OS is running on. (it is in System->Administration->Partition Manager so don't bother with 'gksudo' in a terminal as you will be asked for your password when you invoke the GUI anyhow).

The ONLY way to resize the partition (your currently running OS is on) is to use the Gparted live cd or the Ubuntu one.
im using the livecd..... resizing is irrelevant to what im trying to do. im trying to install ubuntu in 'sdf8' 

> **oboedad55 said:**
> Have you tried Parted Magic? It's available as an iso and boots from a CD. You may be able to format the drive with this: [http://partedmagic.com/](http://partedmagic.com/)

id normally try not flaming, but please re-read the post
that drive you see empty, is what you see in this terminal output, which is a part of this whole problem

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdf: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x515ccb5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       33387   268181046    7  HPFS/NTFS
/dev/sdf2           33388       38913    44387595    5  Extended
/dev/sdf5           33388       34024     5116671    b  W95 FAT32
/dev/sdf6           34025       34828     6458098+  83  Linux
/dev/sdf7           34829       35089     2096451   82  Linux swap / Solaris
/dev/sdf8           35090       38913    30716280   83  Linux
```

---

### Post by Meow27 on 2009-10-05
[http://www.offensive-security.com/documentation/bt4install.pdf](http://www.offensive-security.com/documentation/bt4install.pdf)

i finally found this. will following this guide work for what im trying to do?

do i need to move my first partition to make some empty space?

---

### Post by Meow27 on 2009-10-05
well, i was able to get it installed in the partition i wanted (finally,) but now am looking for solutions as to how to get grub installed to the external drive, not the main HD

---

