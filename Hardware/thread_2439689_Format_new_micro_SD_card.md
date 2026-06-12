---
title: "Format new micro SD card"
date: 2020-03-31
forum: Hardware
---

### Post by satimis on 2020-03-31
SanDisk
Extreme PRO
microSDXC UHS-I Card
170 MB/s Read
90 MB/s Write
128GB

Hi all,

My new micro SD card couldn't be mounted/detected automatically.

~$ ls /dev/ | grep sd```

sda
sda1
sdb
sdb1
sdb2
sdc

```

$ sudo fdisk -l | grep sdc
not showing here

~$ lsblk```

......
sda      8:0    0   1.8T  0 disk 
&#9492;&#9472;sda1   8:1    0   1.8T  0 part 
sdb      8:16   0   1.8T  0 disk 
&#9500;&#9472;sdb1   8:17   0   512M  0 part /boot/efi
&#9492;&#9472;sdb2   8:18   0   1.8T  0 part /
sr0     11:0    1  1024M  0 rom 
......

```
also not showing here. 

I suppose it needs to be formatted first ?

Shall I run;
1)
$ sudo mkfs.vfat -F32 -v /dev/sdc

to format it ?

OR
2)
parted "Creating a Partition and Formatting" it as ext4 ?

The new micro SD card shall be used as hard drive of Raspberry Pi 3.  I shall burn Raspberry OS on it.

Please advise.  Thanks

Regards
satimis

---

### Post by slickymaster on 2020-03-31
*Thread moved to **Hardware**.*

---

### Post by CelticWarrior on 2020-03-31
A new 128GB microSD card is likely formatted as exFAT for which support must be installed (there's no native, "out of the box" support in desktop Linux yet).

But, of course, you can format it using a different file system and not install support for exFAT. That said, why FAT32? If the card is to be used only in Ubuntu you can format it as EXT4.

---

### Post by sudodus on 2020-03-31
A micro SD card should be seen by lsblk even if there is no partition and no file system. Otherwise it is not correctly connected (or the card itself is damaged).

By the way, /dev/sdc could be something else, because some USB adapters for SD cards will show up as a device even if no card is connected. How is the card connected? Maybe it is connected via PCI (instead of USB) and seen as /dev/mmcblk0?

---

### Post by TheFu on 2020-03-31
if this will be used as the boot storage for a r-pi, then forget formatting.  The process of a bit-for-bit copy as most r-pi OS installs happen includes the file system and format.

Getting the card to be seen by the OS is a completely different issue. Not all cards are compatible with all card readers. There are lots of fake cards in the world.

---

### Post by him610 on 2020-03-31
You can get the Raspberry Pi imager for Ubuntu, MacOS, and Windows here, [https://www.raspberrypi.org/downloads/]("https://www.raspberrypi.org/downloads/")
I used it twice last week; it works just fine with SD and microSD cards.

---

### Post by satimis on 2020-04-01
Hi all,

Lot of thanks for your advice.

TheFu&#8217;s advice on #5 above is correct.  It doesn&#8217;t need to format the new micro SD card.  Just download Raspbian Strectch package on:

Download Raspbian Stretch
[https://howchoo.com/g/nzc0yjzjy2u/raspbian-stretch-download](https://howchoo.com/g/nzc0yjzjy2u/raspbian-stretch-download)

Decompress it as .img and run usb-creator-gtk to burn it on the micro SD card.  That is all.  The software takes care of the rest.

Start Raspberry Pi 3 with the micro SD card on.  Raspberry guides me to complete all necessary setup.  Now I&#8217;m replying this link on Raspberry.  That is all.

I&#8217;ll start my next adventure on following link;
Homebridge On A Raspberry Pi
[https://ubuntuforums.org/showthread.php?t=2439446](https://ubuntuforums.org/showthread.php?t=2439446)

Thanks again folks.

Regards
satimis

---

