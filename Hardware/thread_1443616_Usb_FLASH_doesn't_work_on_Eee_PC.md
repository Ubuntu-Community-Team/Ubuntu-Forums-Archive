---
title: "Usb FLASH doesn't work on Eee PC"
date: 2010-03-31
forum: Hardware
---

### Post by Pierrot Lafouine on 2010-03-31
Hi
I installed Ubuntu 8.04 on Eee PC 1005HA (not the Netbook Remix, because I didn't know about it).

I have USB problem, when I insert USB stick (2GBytes FAT32), I got a DialogBox saying :
Cannot mount volume, Invalid mount option when attempting to mount the volume.

I tried this
```
sudo mkdir /media/windows
sudo mount /dev/sdb /media/windows -o force
```
Got this error message : 
mount : you must specify the filesystem type

I tried this :
```
sudo mount /dev/sdb /media/windows -o force -t vfat
```

Got this error message : 
mount: wrong fs type, bad option, bad supperblock on /dev/sdb etc...

Doing this code :
```
dmesg | tail
```
I got this error :
UDF-fs:No VRS fonnd
ISOFS: Unable to identify CD-ROM format

I have 2 stick, 2GB and 4GB, they are working on other Ubuntu system, and on Windoz XP system.  Stick are ok.

What is the best way to fix this ?
Can I "upgrade" to UNR ?
My disk is share with Windows XP sp3.

Thanks!

---

### Post by ajgreeny on 2010-03-31
Try a full mount command with other options as here
```
sudo mount /dev/sdb /media/windows/ -t vfat -o ioch****t=utf8,umask=000
```assuming it is definitely fat32, of course. Post any errors back.

What is on the disk(s)?  Just data, or is it an OS installation?

---

### Post by Pierrot Lafouine on 2010-03-31
> **ajgreeny said:**
> Try a full mount command with other options as here
```
sudo mount /dev/sdb /media/windows/ -t vfat -o ioch****t=utf8,umask=000
```assuming it is definitely fat32, of course. Post any errors back.

What is on the disk(s)?  Just data, or is it an OS installation?

Hi
Git error message wrong fs type etc...
USB key is 8GB and contains only data.

Can the USB key have invisible partition ?
Data is visible under Windows and is FAT32 (I just verified it)
Thanks

---

### Post by Pierrot Lafouine on 2010-03-31
Hi
Git error message wrong fs type etc...
USB key is 8GB and contains only data.

Can the USB key have invisible partition ?
Data is visible under Windows and is FAT32 (I just verified it)
Thanks

---

### Post by eltonw on 2010-03-31
> **Pierrot Lafouine said:**
> Hi
Git error message wrong fs type etc...
USB key is 8GB and contains only data.

Can the USB key have invisible partition ?
Data is visible under Windows and is FAT32 (I just verified it)
Thanks
You did not mention what model EEE PC you have, but mine is the EEE 1000PC. I believe that all the EEE netbooks have as "standard" three USB ports. _Unless I am mistaken, _depending on which USB port you use, linux will read the same USB key as dev/sdb, sdc, sdd.

Does this help?

Greets from Montreal (Quebec), Canada;)

---

### Post by Pierrot Lafouine on 2010-03-31
> **eltonw said:**
> You did not mention what model EEE PC you haveEeePC 1005HA

> **eltonw said:**
> I believe that all the EEE netbooks have as "standard" three USB ports
It has 3 USB port.
I try them all with USB FLASH 8GB, and got same behavior for all USB port.

Anything else I can try ?
Cheers!

---

### Post by ajgreeny on 2010-03-31
In ubuntu terminal and with the usb disk attached, see what ```
sudo fdisk -l
``` tells you about it.

---

### Post by Pierrot Lafouine on 2010-03-31
> **ajgreeny said:**
> In ubuntu terminal and with the usb disk attached, see what ```
sudo fdisk -l
``` tells you about it.

It tells me there is only one FAT32 partition on /dev/sdb

Kinda wierd, fdisk detect that but mount is not able to do his job.

---

### Post by ajgreeny on 2010-04-01
Silly me!!

Try the command I gave you last time, but with the full partition name, not just the disk name, so probably 
```
sudo mount /dev/sdb1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
```I hope that does the trick and I don't quite know how I missed that.

You don't, of course, mount a disk, but always a partition.

PS.
It looks to me as if my original command that I copied from a text file was corrupted in my original post, so make sure you copy and use this new one with the word "iocharset", not "ioch****t".  I've no idea how that happened!

---

