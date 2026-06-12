---
title: "Re-structuring Partition layout"
date: 2008-10-24
forum: General Help
---

### Post by texas.chef94 on 2008-10-24
Using the latest gparted live CD I have shrunk NTFS partition as I am attempting to free up some space so I end up with following
NTFS
ubuntu
Extended
Swap
Home partition
Iam told that I must delete logical partitions within the extended prior to deleting the extended itself.
Ok I am not the sharpest knife in the drawer in this gparted and restructure so when I right click on this extended I only see an opportunity to resize. Delete even is not available. Am I missing something and do I not need to create a new extended.
Please advise and thanks

Allen

---

### Post by prshah on 2008-10-24
> **texas.chef94 said:**
> 
when I right click on this extended I only see an opportunity to resize. Delete even is not available.

First, post the gparted screenshot here if you can; otherwise, open a Terminal (Applications-Accessories-Terminal) and post back the results of the following command```
sudo fdisk -l
```

This will give us a more accurate picture of what your current setup is.

You can have a maximum of four primary partitions. If you need more than 4 partitions, you can replace any _one_ primary partition with an extended partition, and then you can create more "logical" partitions within that extended partition.

Is there any specific reason that you want to create a new extended partition and not use the one you already have?

---

### Post by cyberdork33 on 2008-10-24
Are you on a Mac?

---

### Post by texas.chef94 on 2008-10-25
Not on a Mac and would have nposted a snapshot, but gparted saves in root and I had little difficulty but will try again. In answer to the extended question I simply thought when I resize or restructure I needed a new extended  If that is not the case please advise. In meantime here are fdsk results, and thank you so much.
llen@allen-laptop:~$ sudo fdisk -l
[sudo] password for allen: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99d799d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1688    13558828+   7  HPFS/NTFS
/dev/sda3            2433        4762    18715725    5  Extended
/dev/sda5            4561        4748     1510110   82  Linux swap / Solaris
/dev/sda6            2433        4053    13020619+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1006 MB, 1006632960 bytes
31 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 1922 * 512 = 984064 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
allen@allen-laptop:~$ 

size

---

### Post by texas.chef94 on 2008-10-25
If I am editing my original reply in error please excuse. Went back to gparted took a screen shot and screen shot appeared and indicated it was saved in root. Booted back in went to dolphin+root and all I found was text results. Where is actual screen shot and how do I access? advise and thanks

Allen

---

### Post by texas.chef94 on 2008-10-25
[http://s427.photobucket.com/albums/pp352/76yrold/](http://s427.photobucket.com/albums/pp352/76yrold/)

Screenshot from installed gparted package might help

This from actual live CD in root

Libparted 1.7.1

 
Grow /dev/sda5 from 7.84 MiB to 1.44 GiB  00:01    ( SUCCES ) 
      
   calibrate /dev/sda5  00:01    ( SUCCES ) 
      
  path: /dev/sda5
start: 73256400
end: 73272464
size: 16065 (7.84 MiB) 
   calculate new size and position of /dev/sda5  00:00    ( SUCCES ) 
      
  requested start: 73256400
requested end: 76276619
requested size: 3020220 (1.44 GiB) 
  new start: 73256400
new end: 76276619
new size: 3020220 (1.44 GiB) 
   check filesystem on /dev/sda5 for errors and (if possible) fix them    ( N/A ) 
      
  checking is not available for this filesystem 
   grow partition from 7.84 MiB to 1.44 GiB  00:00    ( SUCCES ) 
      
  old start: 73256400
old end: 73272464
old size: 16065 (7.84 MiB) 
  new start: 73256400
new end: 76276619
new size: 3020220 (1.44 GiB) 
   check filesystem on /dev/sda5 for errors and (if possible) fix them    ( N/A ) 
      
  checking is not available for this filesystem 
   grow filesystem to fill the partition  00:00    ( SUCCES ) 
      
   create new linux-swap filesystem  00:00    ( SUCCES ) 
      
  mkswap /dev/sda5 
      
  Setting up swapspace version 1, size = 1546346 kB
no label, UUID=a2b9b8d8-2651-4291-b948-85292335e16a

---

### Post by mabovo on 2008-10-25
You need to reformat all disk and reorganize your computer.

It looks messed up.  : )

---

### Post by texas.chef94 on 2008-10-25
That was quite informative thanks so much for the detail

Allen

---

### Post by cyberdork33 on 2008-10-25
> **texas.chef94 said:**
> Not on a Mac

This is the Apple Users forum ;)

I will request it is moved.

---

### Post by bapoumba on 2008-10-26
Moved to General Help.

---

### Post by tayhe on 2008-10-26
if you want to delect the extended partition, just delect all logic partitiongs ,which belongs to the extended one.
and then the extended one could be delected .:guitar:

---

### Post by texas.chef94 on 2008-10-26
I appreciate that latest on deleting the Extended, but it seems advice thus far becomes a moot point. I am sending this from my desktop only windows based because when I attempted to boot the laptop to begin what I had planned as just starting over I face a new crisis. Grub loading Stage1.5 Please wait error 22. So how do I get out of this latest mess
Please advise and thanks to all for patience with this 76 yr old relic  

Allen

---

### Post by rolnics on 2008-10-26
Well I might be able to help on this one, as I came across you post while I had the same issue! Grub 22 error!

I have a supergrub live cd so I managed to fix it using supergrub to boot my main partition, I'm going to assume you haven't got that but you will have your ubuntu live cd. Boot from that, once you've got there start up the terminal (Applications -> Accessories -> Terminal)

Then enter
```
sudo fdisk -l
``` 

Then you need follow [this howto]("http://ubuntuforums.org/showthread.php?t=224351")

---

