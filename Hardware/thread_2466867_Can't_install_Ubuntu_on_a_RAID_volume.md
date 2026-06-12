---
title: "Can't install Ubuntu on a RAID volume"
date: 2021-09-08
forum: Hardware
---

### Post by ferran77-u on 2021-09-08
I'm building a server, it has two 120Gb SATA SSDs on an AMD B450 motherboard. I want the two SSDs on RAID 1 (redundancy).
I tried software RAID, but Ubuntu doesn't want to boot from a software raid: if you create a RAID volume, then you can't install Ubuntu because the installer tells you that you can't install the bootloader on a software RAID volume (something I find absurd for a RAID 1 volume).
Then I tried hardware RAID (with the integrated RAID controller from AMD), but there's no included drivers for this RAID controller, and I don't know how to install them. The installer then can't find any disks and doesn't let you go further.
After googling about my problem, I found RCRAID, but if I boot with the install USB, and use the console to add the repository needed and install RCRAID, the install fails because the live-OS has some of the volumes on read-only.
Also I found some drivers from AMD, but they are ancient (for Ubuntu 16.10 LTS), and didn't get to make them work.

I need this server to have RAID 1 for the system disk, I don't care if it's software or hardware RAID. Any pointers to documentation or any help on how to achieve this would be appreciated.

---

### Post by TheFu on 2021-09-11
a) motherboard RAID is almost always "FakeRAID" and a terrible choice.  We get all the constraints of HW-RAID, but none of the performance. I can think of only 1 good reason to use it and a Linux server isn't one.  In the past, there was a separate FakeRAID driver - dmraid? - but I think that code has been merged into mdadm the last few years.  If that is true, then any limitations that mdadm has on boot requirements would likely apply to both SW-RAID and FakeRAID setups.

b) My B450 MB doesn't support using both m.2 SSD slots without stealing 2 of the SATA ports. Also, one is NVMe and the other is SATA.  My point is that reading the motherboard manual VERY carefully will be necessary to understand any issues with using both at the same time.

c) I've never attempted to setup SW-RAID for the OS under Ubuntu.  I don't think it was possible until recently and, if it does work today, I suspect it isn't well tested.  If I were to do it, I'd setup a normal LVM setup, then use LVM to create a RAID1 mirror.  That wouldn't get the non-LVM parts into RAID, however, so /boot/ would likely remain outside the RAID redundancy.

[https://ubuntu.com/server/docs/install/storage](https://ubuntu.com/server/docs/install/storage) has instructions for setting up RAID during the installation.
The sections after "Selecting boot devices" may shed some light.  Seems there is a BIOS issue with booting and the way to address that is to control the boot order of non-RAID devices.  Basically, do an install, then clone the boot area (and after every update to the boot area, re-clone it again), but still maintain the boot order desired.  Perhaps NVMe-A then a USB flash drive?  Depending on how the  clone is made, you may need to force a new UUID for the partitions so the OS doesn't get confused between the different /boot/ and /boot/efi/ mounts.

If I get some time today, I'll try to setup RAID for a VM.

---

### Post by rsteinmetz70112 on 2021-09-12
In the past I have been able to install Ubuntu on a mdadm Raid1 volume using lvm2 successfully. It's been a long time since I did it so I don't remember all of the details but it's still running and has been successively upgraded. If I recall correctly it was then recommended that /boot not be on the araid volume, but I did it any way.  

For what it's worth here is the layout:

```
$ lsblk
sda                 8:0    0   1.8T  0 disk  
&#9492;&#9472;sda1              8:1    0   1.8T  0 part  /backup
sdb                 8:16   0 931.5G  0 disk  
&#9500;&#9472;sdb1              8:17   0  74.5G  0 part  
&#9474; &#9492;&#9472;md0             9:0    0  74.5G  0 raid1 
&#9474;   &#9500;&#9472;thelma-root 253:0    0  39.1G  0 lvm   /files/thelma
&#9474;   &#9500;&#9472;thelma-tmp  253:1    0   9.8G  0 lvm   /files/thelma/tmp
&#9474;   &#9500;&#9472;thelma-var  253:2    0   9.8G  0 lvm   /files/thelma/var
&#9474;   &#9500;&#9472;thelma-swap 253:3    0   7.8G  0 lvm   [SWAP]
&#9474;   &#9492;&#9472;thelma-www  253:4    0   8.1G  0 lvm   /files/thelma/var/www
&#9500;&#9472;sdb2              8:18   0 438.8G  0 part  
&#9474; &#9492;&#9472;md2             9:2    0 438.7G  0 raid1 /home
&#9492;&#9472;sdb3              8:19   0  78.6G  0 part  
sdc                 8:32   0 931.5G  0 disk  
&#9492;&#9472;sdc1              8:33   0 931.5G  0 part  
  &#9492;&#9472;md126           9:126  0 931.4G  0 raid1 
    &#9500;&#9472;system-root 253:5    0    50G  0 lvm   /
    &#9500;&#9472;system-tmp  253:6    0    10G  0 lvm   /tmp
    &#9500;&#9472;system-var  253:7    0    10G  0 lvm   /var
    &#9500;&#9472;system-swap 253:8    0    16G  0 lvm   [SWAP]
    &#9500;&#9472;system-www  253:9    0    10G  0 lvm   /var/www
    &#9500;&#9472;system-home 253:10   0   500G  0 lvm   
    &#9492;&#9472;system-xtra 253:11   0 335.4G  0 lvm   /var/mail
sdd                 8:48   0 931.5G  0 disk  
&#9500;&#9472;sdd1              8:49   0  74.5G  0 part  
&#9474; &#9492;&#9472;md0             9:0    0  74.5G  0 raid1 
&#9474;   &#9500;&#9472;thelma-root 253:0    0  39.1G  0 lvm   /files/thelma
&#9474;   &#9500;&#9472;thelma-tmp  253:1    0   9.8G  0 lvm   /files/thelma/tmp
&#9474;   &#9500;&#9472;thelma-var  253:2    0   9.8G  0 lvm   /files/thelma/var
&#9474;   &#9500;&#9472;thelma-swap 253:3    0   7.8G  0 lvm   [SWAP]
&#9474;   &#9492;&#9472;thelma-www  253:4    0   8.1G  0 lvm   /files/thelma/var/www
&#9500;&#9472;sdd2              8:50   0 438.8G  0 part  
&#9474; &#9492;&#9472;md2             9:2    0 438.7G  0 raid1 /home
&#9492;&#9472;sdd3              8:51   0    77G  0 part  
sde                 8:64   0 931.5G  0 disk  
&#9492;&#9472;sde1              8:65   0 931.5G  0 part  
  &#9492;&#9472;md126           9:126  0 931.4G  0 raid1 
    &#9500;&#9472;system-root 253:5    0    50G  0 lvm   /
    &#9500;&#9472;system-tmp  253:6    0    10G  0 lvm   /tmp
    &#9500;&#9472;system-var  253:7    0    10G  0 lvm   /var
    &#9500;&#9472;system-swap 253:8    0    16G  0 lvm   [SWAP]
    &#9500;&#9472;system-www  253:9    0    10G  0 lvm   /var/www
    &#9500;&#9472;system-home 253:10   0   500G  0 lvm   
    &#9492;&#9472;system-xtra 253:11   0 335.4G  0 lvm   /var/mail
```
It's an older board and BIOS not EUFI an ASRock N68C-GS4 FX. /dev/sda is an external USB drive. The other drives are 1TB Toshiba mechanical hdds.
If I were doing it today I'd do it very differently, but if it ain't broke don't fix it and like I said that was a long time ago.

---

