---
title: "How do I access Bios?"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by comradejanus on 2009-03-23
OK. I installed ubuntu one week ago after getting rid of windows once and for all. Today however I think I'd better reinstall windows vista to use a couple of software packages that don't work to well on ubuntu.

Well anyway I was planning on formating (I dont mind losing all my files i've already backed them up), installing vista then dual booting with my ubuntu live CD.

The problem is, I can't seem to figure out what to do next. How do I boot from my vista disk? I used to be able to press F2 on start up to select boot device from the bios. How to do access it now?

Thanks.

---

### Post by Pumalite on 2009-03-23
For a Secondary Menu I think it's F8
To get to BIOS in most computers you press 'Del' at POST

---

### Post by icanfly0307 on 2009-03-23
It all depends on your computer's settings. For VAIO computers, it's F2. Otherwise, try Esc, F3, F4, F5, F10, or F11. DEL should also work.

---

### Post by comradejanus on 2009-03-23
Thanks alot that worked I pressed del and it opened up.

Ok now I have anouther problem. I tried to install windows but it said I need to format the drive as ntfs. I tried doing this using partition editor on my ubuntu live cd. 

However I get the following error when I try to do so:



Create Primary Partition #1 (ntfs, 298.09 GiB) on /dev/sda  00:00:00    ( ERROR )
     	
create empty partition  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 625137344
size: 625137282 (298.09 GiB)
set partitiontype on /dev/sda1  00:00:00    ( SUCCESS )
     	
new partitiontype: ntfs
create new ntfs filesystem  00:00:00    ( ERROR )
     	
mkntfs -Q -vv -L "" /dev/sda1
     	
The device doesn't exist; did you specify it correctly?
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/sda1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.
Error informing the kernel about modifications to partition /dev/sda1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.

---

### Post by comradejanus on 2009-03-23
Ah, I reboot my computer and now it works just fine. Thanks again for your help.

---

