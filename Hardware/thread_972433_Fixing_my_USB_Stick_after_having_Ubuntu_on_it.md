---
title: "Fixing my USB Stick after having Ubuntu on it"
date: 2008-11-05
forum: Hardware
---

### Post by nrthguy on 2008-11-05
Hello all! 
I installed ubuntu live usb (8.10) on my usb stick, and after i didnt need it anymore (i installed ubuntu under windows, safe fast n easy) I did the silly thing to format the USB under windows, what i had left was 1 GB stick instead of its initiall 2 GBs, I booted into linux and when i plug it in I get another device poping up "casper-rw", though the fat32 part of the stick is readable by both OS i cant get to my other Gigabyte.

How can i fix this, i was thinking somekind of format on the whole USB but have no idea how. (for end result i want my 2GB back, in fat or fat32 readable by both systems)

Maybe this can help a bit?:
[http://img248.imageshack.us/img248/8285/ntfsny0.png](http://img248.imageshack.us/img248/8285/ntfsny0.png)

---

### Post by zwygart on 2008-11-05
You have to repartition your USB drive. 
Windows only can read the first partition of a flash drive.
I have 7 partitions on my drive and Linux read all the partition, Windows the first.
So delete the second partition, resize the first to the whole size. 
I don't know if windows can do that, but I suggest using gParted (from CD, Linux, or anywhere).

If you have a installed Linux it will be easy. Do have access to any Linux distro or something?

If not I think the easiest way will be to backup your datas, format the whole key, restore the datas. (1G is not as big as that)

---

### Post by nrthguy on 2008-11-06
Yeah I have linux on my machine. I installed gparted but no idea what t odo next, looking at the screen above I suppose the usb device name is sdb but i get 
$ gpart sdb

*** Fatal error: open(sdb): No such file or directory.

More details please?

---

### Post by timcredible on 2008-11-06
> **nrthguy said:**
> Yeah I have linux on my machine. I installed gparted but no idea what t odo next, looking at the screen above I suppose the usb device name is sdb but i get 
$ gpart sdb

*** Fatal error: open(sdb): No such file or directory.

More details please?

run it from the menus (system->administration->partition editor) - if you run it from command line, you need to put sudo in front of the command so you can run it with root permissions.

---

### Post by Coreigh on 2008-11-06
With the USB drive attached to the computer, but not mounted. (To un-mount, right click on the disk icon for the USB drive and select unmount.)

Run gparted and choose the /dev/sd* that is the USB drive 

(* will be a letter. Each physical drive will take a letter. The main hard drive is usually 'a' then depending on your system each device takes the next letter. The second disk takes 'b' or 'c', and the CD/DVD and so on. On my sysstem the USB drive goes all the way down to 'f' i.e. /dev/sdf)

When you are sure you have the right one then select one of the partitions and choose delete, and then the other and choose delete and then click the "New" button and create a new partition. If you are sharing with a windows computer I suggest fat32, if Ubuntu only then go ahead with ext2 or ext3. Finally click apply changes.

Keep in mind that these step will purge ALL data that is on the drive so empty it be for you start.

---

### Post by nrthguy on 2008-11-07
Great, worked perfectly, thanks!

---

