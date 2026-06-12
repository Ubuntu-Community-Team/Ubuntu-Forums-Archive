---
title: "[SOLVED] After Formatting Windows &amp;amp; Ubuntu - Ubuntu Disk Space Missing"
date: 2008-08-01
forum: Hardware
---

### Post by sandrasagra on 2008-08-01
Everything was working fine w/ Ubuntu and Windows as a dual boot until the IT guy touched it. 

My original configuration was 
DELL INSPIRON 6400 
Centrino Duo 2.0Ghz 
1GB 
80GB 
Windows 55GB
Ubuntu 25 GB

He had to change my domain on Windows so after removing the domain he forgot to reset the Administrator password and he or I couldn't log into the laptop. So after many attempts going through linux bootable cd's to reset the password we had to format the computer. :(

Anyway, I finally got my computer back and ubuntu is missing. So I assume he formatted the whole drive. But when I go into Windows it only reports a total of 55 GB and not 80GB. :confused:

I load the Ubuntu live cd and fdisk -l and it notices only the 55GB partition. What happened to the 25GB that ubuntu was installed on ? 

I know he didn't switch out my drive, so where do you think it is and how can I restore it either through windows or ubuntu. Because I really want to reinstall ubuntu and I definitely can't install it on a total 55GB hard drive (too little space for work and ubuntu).

Help.

---

### Post by LowSky on 2008-08-01
Most Likely Ubuntu wasn't touched. Downlaod the Super Grub CD and have it reconfigure the Boot up process. otherwise try Gparted and see if it notcies the missing space.

---

### Post by Sef on 2008-08-01
> I load the Ubuntu live cd and fdisk -l and it notices only the 55GB partition. What happened to the 25GB that ubuntu was installed on ?

Could you post the results of ```
sudo fdisk -l
```.  Thank you.

---

### Post by coffeecat on 2008-08-01
I can't be sure but it sounds as though when you reformatted the drive, the IT guy erased the whole lot and then created only a 55Gb partition for Windows and left the rest unformatted (unallocated). That's why fdisk -l is only showing the 55Gb partition. Or at least I guess so. It's a long time since I've used fdisk on a HD with some unallocated space and I can't remember what the output should be.

Boot up with the live CD again and go to System > Adminstration > Partition Editor and see what that says. Hopefully it will show the 25G as unallocated and you will be able to format it for Ubuntu.

---

### Post by sandrasagra on 2008-08-05
> **Sef said:**
> Could you post the results of ```
sudo fdisk -l
```.  Thank you.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        7112    57086977+   7  HPFS/NTFS

Disk /dev/sdb: 4103 MB, 4103938560 bytes
128 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         992     3999649    b  W95 FAT32

---

### Post by sandrasagra on 2008-08-05
> **coffeecat said:**
> I can't be sure but it sounds as though when you reformatted the drive, the IT guy erased the whole lot and then created only a 55Gb partition for Windows and left the rest unformatted (unallocated). That's why fdisk -l is only showing the 55Gb partition. Or at least I guess so. It's a long time since I've used fdisk on a HD with some unallocated space and I can't remember what the output should be.

Boot up with the live CD again and go to System > Adminstration > Partition Editor and see what that says. Hopefully it will show the 25G as unallocated and you will be able to format it for Ubuntu.
[B]
Unallocated is only showing as 7.84MB. :([/B]

[IMG]http://i37.tinypic.com/23k4uv.png[/IMG]

---

### Post by sandrasagra on 2008-08-05
> **LowSky said:**
> Most Likely Ubuntu wasn't touched. Downlaod the Super Grub CD and have it reconfigure the Boot up process. otherwise try Gparted and see if it notcies the missing space.

Gparted nor Super Grub (USB) does not notice the missing space. Any more suggestions ?

---

### Post by coffeecat on 2008-08-05
Both fdisk and Gparted are in agreement. Your hard disc is under 60GB in size, either 58.5 or 54.49, depending on whether you are measuring in gigabytes or gibibytes. This whole business of what a gigabyte refers to is fraught. If you're really interested, see [Wikipedia Binary Prefix]("http://en.wikipedia.org/wiki/Binary_prefix") and [Wikipedia Gibibyte]("http://en.wikipedia.org/wiki/Gibibyte").

The important thing is that you do not have an 80G hard disc there. At 54.49/58.5, that would be what the manufacturer would refer to as a 60G, and according to the information I can find about the Dell Inspiron 6400 is that it comes with a 60G hard disc. Why did you think you had an 80G disc?

One thing that confuses me - the Dell Inspiron 6400 is a laptop, so what is that just under 4GB sdb? Did you have a USB device plugged in when you did fdisk?

The bad news is that you have no Linux partition at all - just a tiny Dell utility partition, a ~55GB Windows partition, and a little under 8MB free.

---

### Post by sandrasagra on 2008-08-05
> **coffeecat said:**
> Both fdisk and Gparted are in agreement. Your hard disc is under 60GB in size, either 58.5 or 54.49, depending on whether you are measuring in gigabytes or gibibytes. This whole business of what a gigabyte refers to is fraught. If you're really interested, see [Wikipedia Binary Prefix]("http://en.wikipedia.org/wiki/Binary_prefix") and [Wikipedia Gibibyte]("http://en.wikipedia.org/wiki/Gibibyte").

The important thing is that you do not have an 80G hard disc there. At 54.49/58.5, that would be what the manufacturer would refer to as a 60G, and according to the information I can find about the Dell Inspiron 6400 is that it comes with a 60G hard disc. Why did you think you had an 80G disc?

One thing that confuses me - the Dell Inspiron 6400 is a laptop, so what is that just under 4GB sdb? Did you have a USB device plugged in when you did fdisk?

The bad news is that you have no Linux partition at all - just a tiny Dell utility partition, a ~55GB Windows partition, and a little under 8MB free.

Thanks for the info, I am going to corner the IT guy and ask him if he switched drives on me... I am sure that I had a 80g drive on my computer. 

The 4gb was a usb flash which I used super grub (booted usb) on. 

Thanks for the help, I will update when I get more info.

---

### Post by Jordanwb on 2008-08-05
> **coffeecat said:**
> The important thing is that you do not have an 80G hard disc there. At 54.49/58.5, that would be what the manufacturer would refer to as a 60G, and according to the information I can find about the Dell Inspiron 6400 is that it comes with a 60G hard disc. Why did you think you had an 80G disc?

Perhaps he got a bigger hard drive installed? He seems pretty sure that he had an 80GB hard drive, considering he says he had a 55GB and a 25GB partition on it.

> **coffeecat said:**
> Did you have a USB device plugged in when you did fdisk?

Um so?

> **sandrasagra said:**
> Thanks for the info, I am going to corner the IT guy and ask him if he switched drives on me... I am sure that I had a 80g drive on my computer.

If you had proof you had a 80GB drive and you ended up with a 60GB, I think there may be something you could do in the law department.

---

### Post by sandrasagra on 2008-08-06
I went online to dell.ca and checked with my service code the original configuration and it looks like I always had a 60gb drive.

:lolflag:

---

### Post by coffeecat on 2008-08-06
> **sandrasagra said:**
> I went online to dell.ca and checked with my service code the original configuration and it looks like I always had a 60gb drive.

I'm glad the mystery is solved, but sorry that you lost your Ubuntu install. Will you be reinstalling Ubuntu? Good luck with it if you do.

---

