---
title: "Internal TB wont mount"
date: 2010-02-03
forum: Hardware
---

### Post by MiceMiceRabies on 2010-02-03
The other day I formated my new TB to ext4,  I transfered all my media to the new drive  this was all done with fedora live.   

I now have ubuntu 9.10 installed on my primary drive and I want to access my secondary drive. This is an internal drive

my problem now is that when I try to mount with the GUI it requests my password then the drive disappears and nothing happens.  So go to my /media/function double click and it says I dont have permission to view the files.  

Then i tried mounting via terminal 

chlorine@chlorine-desktop:~$ sudo mount /dev/sdb /media/function
mount: /dev/sdb already mounted or /media/function busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/function



When I run "sudo fdisk -l"




Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8a8a8a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38539   309564486   83  Linux
/dev/sda2           38540       38913     3004155    5  Extended
/dev/sda5           38540       38913     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000047cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux


any help is appreciated!

---

