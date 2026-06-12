---
title: "USB flash drive (Read only)"
date: 2013-09-11
forum: Hardware
---

### Post by lekevinio on 2013-09-11
Hi there,

I've got an USB flash drive that is mounted Read only. If I use the Disks utility it does see the size but not the contents is unknown. I'm only able to Create a disk image and Benchmark the drive.
Windows does see the drive but cannot open it. It also sees one partition (it should have 5   fat32, ntfs,* /SWAP, ext4/ *ext4    / / = extended) but cannot preform a format.

After allot of Google'ing I found that the Magic number might be broken. So I tried the following
[http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.howtos/doc/howto/HT_baseadmn_badmagnumber.htm](http://publib.boulder.ibm.com/infocenter/pseries/v5r3/index.jsp?topic=/com.ibm.aix.howtos/doc/howto/HT_baseadmn_badmagnumber.htm)

But when I use
**dd count=1 bs=4k skip=31 seek=1 if=/dev/sdc of=/dev/sdc**
It just gives the output:
dd: opening ‘/dev/sdc’: Read-only file system.

Here are some couple of commands I also used. I used some other command too but I forgot which ones that where.
**sudo hdparm -r0 /dev/sdc**
/dev/sdc:
 setting readonly to 0 (off)
 readonly      =  0 (off)

But the drive is still read only

**fdisk -l**
Disk /dev/sdc: 7862 MB, 7862353920 bytes
242 heads, 62 sectors/track, 1023 cylinders, total 15356160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb27402d4

Disk /dev/sdc doesn't contain a valid partition table


**sudo mount -w -t vfat -o remount,rw /dev/sdc /mnt/usb**
mount: /mnt/usb not mounted or bad option

**sudo mount -w -t vfat -o rw /dev/sdc /mnt/usb**
mount: block device /dev/sdc is write-protected but explicit `-w' flag given

**sudo mount -t vfat -o rw /dev/sdc /mnt/usb**
mount: block device /dev/sdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I sure hope the flashdrive is not broken beyond repair.
Thanks in advance.

---

### Post by sudodus on 2013-09-11
The pendrive might be broken. It it typical, that write fails before also read fails.

But you might have better luck if you try in another USB port and above all, ***try the pendrive in some other computers***, because it might be a problem with the computer, not the pendrive, or with the combination of computer and pendrive.

---

### Post by lekevinio on 2013-09-11
Thanks for the quick reply :).
The flashdrive isn't mine but from a co-worker of a friend of mine. It was tried on at least 4 different computers all 4 at least with 2 ports (3.0 and 2.0).

---

### Post by sudodus on 2013-09-11
***hdparm*** is the most powerful tool of those you have tried. If hdparm can only see it read only (and cannot change that), I think there is little hope, but maybe you can do something with it. But before doing that, let the owner decide if you should try that strong and dangerous tool.

Read carefully ```
man hdparm
```

You can have a closer look not only at the -r option, but also -c and some of the others.

---

### Post by lekevinio on 2013-09-12
Could you give me a bit more details in what command I should use with man hdparm?
I don't quite know what to do with that. I know the terminal a bit but not so much that I can figure out an entire command from just 2 words. Sorry.

---

### Post by sudodus on 2013-09-12
If you run ```
man hdparm
``` in a terminal window, you will get the manual of the command. I promise there are more than two words ;-)

But I must admit, that I feel also quite unsure about hdparm, so it is only as a last resort, that you should try it.

---

### Post by philinux on 2013-09-12
While the drive is still readable make sure you back up the contents while you still can, if you've not done so already.

---

### Post by lekevinio on 2013-09-18
Sorry for the late respond. I've been ill for some time.

I tried man hdparm and I used a few commands but nothing helped. Not even the -w (erase) function

> 
kingkong@kingkong-buntu:~$ hdparm -w /dev/sdc

/dev/sdc:
 resetting drive
 HDIO_DRIVE_RESET failed: Invalid argument
kingkong@kingkong-buntu:~$ sudo hdparm -w /dev/sdc


Is there any combination of parameters for the hdparm command that I could use as last resort?
If there is nothing else to try then the USB drive is just broken and that's that.

---

### Post by sudodus on 2013-09-18
Well, I 'm sorry, but I think the pendrive is broken. Do what *philinux* suggests: 	 	> While the drive is still readable make sure you back up the contents while you still can, if you've not done so already. 		


---

### Post by lekevinio on 2013-09-18
Ok. Then it's to bad.
There were no really important information on it. But it isn't/wasn't readable in the first place.
Oh well :p
Thanks for the effort guys :).

---

