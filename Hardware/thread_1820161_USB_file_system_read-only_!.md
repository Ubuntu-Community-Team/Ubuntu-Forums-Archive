---
title: "USB file system read-only !?"
date: 2011-08-07
forum: Hardware
---

### Post by lucasart on 2011-08-07
my USB key now has a read only file system apparently !? it's a fat32 formatted key.
Ubuntu just did that randomly, somehow. And this is such a stupid and annoying system bug. Now i cant format it, i cant change file permissions and simply cant use it.

So how do i change this property of the fs ?
Otherwise, how do i format it (of course the format option never appears in nautilus, even on gksu nautilus as even sudo rights dont allow anything)

---

### Post by aaitken1998 on 2011-08-07
First make sure it's mounted (obviously) then open a terminal and type:

```
 mount 
```This will give you a list of devices, find your device and note the path on the left side (something like /dev/sr0)

After that type the following

```
 sudo chmod -R 777 /dev/sr0 
```!! Remember to replace /dev/sr0 with what your devices path is !!

This should then let you do whatever you want with the device and its contents

Good luck! :)

---

### Post by lucasart on 2011-08-07
> **aaitken1998 said:**
> First make sure it's mounted (obviously) then open a terminal and type:

```
 mount 
```This will give you a list of devices, find your device and note the path on the left side (something like /dev/sr0)

After that type the following

```
 sudo chmod 777 -r /dev/sr0 
```!! Remember to replace /dev/sr0 with what your devices path is !!

This should then let you do whatever you want with the device and its contents

Good luck! :)
thanks for trying to help, but you don't seem to understand. it's a read only file system !
a chmod doesn't work. your syntax of chmod is incorrect, but even if i do it correctly it gets refused.

i need to modify this stupid file system property that got changed by ubuntu somehow...

---

### Post by hakermania on 2011-08-07
You can try change it/reformatting it via Disk Utility

---

### Post by lucasart on 2011-08-08
> **hakermania said:**
> You can try change it/reformatting it via Disk Utility
Many thanks!
Problem solved

---

### Post by aravind4j on 2012-10-10
i'm having the same problem , i tried the disk utility but it still doesn't show the paste option 

i'm using a pendrive which is in msdos format

---

### Post by alfu on 2012-10-23
Update 121024: My problem was due to plugging the micro SD card into an external USB multicard reader, which sometimes gives me 'read only' problems.  Plugging the card (in its adapter) directly into the computer's card slot allowed me to write to it.  Disturbingly, when changing the permissions in the Ubuntu'properties' dialog, 'read/write' still changes back immediately to '--'.
_____________________________________________________________________
OK, maybe lucasart's problem is solved, but mine isn't.  I formatted a 16GB micro SD (for my Android 4.0 phone) into FAT32 partitions using the Disk Utility.  I was hoping to put some files on the partitions the phone didn't use for its own use.

I think Android itself changed them to 'read only' -- the partitions can be seen in Ubuntu and an old iBook running both MacOS 9.4 and OSX, but nothing can write to it.

I have tried both Disk Utility and gParted to change the R/W permissions, format the partitions, or to even reformat the whole thing from scratch, but nothing will touch the drive.

I have had a similar problem before but it has never been this bad.  One of the reports indicate "MS DOS MAGIC found", whatever that is.  Why can something put mojo on a disk so powerful that nothing in Ubuntu can overcome it?

---

