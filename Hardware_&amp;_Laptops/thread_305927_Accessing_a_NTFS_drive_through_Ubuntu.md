---
title: "Accessing a NTFS drive through Ubuntu"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by Ballymena Pete on 2006-11-24
HI,

I'm new to Ubuntu and require some help.  I have successfully installed Edgy on a 40gb hard drive (hda) and now i would like to take a second drive which contains data (MP3 video etc), this drive has a NTFS file system.  I would like to find a way to do this so i won't lose any of the data on this second drive. 
I have connected up this drive and it is regognised by the BIOS and from using the command GNOME partition manager i can see that this second drive is hdab.
How do i go about accessing the files on this drive????

All advice is greatly appreciated.

---

### Post by Sandriman on 2006-11-24
Hello!

Everything is more or less automagic on a Vaio I use, and I'm surprised it doesn't work for you. Here's some instructions though:

You need to load the *ntfs* kernel module to be able to read such disks. I load it on system startup by putting it to my list of automagically loaded modules. If you don't already have it there, you can say:

```
sudo echo "ntfs" >> /etc/modules
```

**NOTE:**
[INDENT]If you're not sure on whether you have the NTFS module or not, you can say:
```
find /lib/modules/2.6* -type f -iname '*.ko' | grep 'ntfs'
```
Even if **find** discovers the *ntfs.ko*, make sure that the kernel version of the path is correct, i.e. if your kernel version is 2.6.17-10, then the output should be something like:
```
/lib/modules/2.6.17-10-generic/kernel/fs/ntfs/ntfs.ko
```
[/INDENT]

Ok, that was thorough :) If you reboot now, **ivman** should be able to (auto)mount your NTFS drive the next time you log in.

The alternative method is to load the *ntfs* driver manually, but this is not as "clean". Anyway, you can do like this:

```

sudo modprobe ntfs
mount -t ntfs /dev/hdb1 /mnt/Windows

```

A couple of notes on this. First, the **/mnt/Windows** is a directory I have created specifically for quick'n'dirty mounting of NTFS partitions. You should create that, or anything you feel is suitable, if it doesn't exist. Secondly, I was kind of curious about the hard drive symlink. As far as I'm concerned, a hard drive symlink _can't_ be */dev/hdab*. It can be either */dev/hda* or */dev/hdb*, and you need to figure this out. I just assumed it is */dev/hdb1*, which means the first partition of the second hard disk in your computer. In case you have no clue as to how to figure this out, you can say:

```
sudo fdisk -l /dev/hd*
```

And a list of all the hard drives (IDE ones, not SCSI or SATA) and their partitions will be dumped in the form:

```

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3495    28073556   83  Linux
/dev/hda2            3496        3648     1228972+   5  Extended
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris

```

This is just my partition table, so don't be confused. Your NTFS disk appears in such a list as HPFS/NTFS. Find the /dev symlink from there, insert it into the **mount** command I gave before and you should be set.

To summarize, I still recommend you try the first option, which is adding the *ntfs* module to */etc/modules* and hope it will automount.

**WARNING**
In general it is a very bad idea to _write_ anything to a NTFS partition in Linux. The driver is good enough for reading, but not writing. Consider yourself warned.

:)

---

### Post by Ballymena Pete on 2006-11-24
Thanks Sandriman i'll try that tonight, and thanks for getting back so quickly

---

