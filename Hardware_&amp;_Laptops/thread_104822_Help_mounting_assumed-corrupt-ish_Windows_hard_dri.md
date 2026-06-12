---
title: "Help mounting assumed-corrupt-ish Windows hard drive"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by TomPreuss on 2005-12-16
Hi all.

I'm attempting to mount and recover some files from a friend's old Windows hard drive.  He tells me it just stopped working for him a few months ago and he all but forgot about it.

I'm attempting to access it with a Breezy Live CD.  Here's what's happened so far:
```
sudo fdisk -l
Disk /dev/hda: 30.0 GB, 30060527616 bytes
225 heads, 63 sectors/track, 3654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start        End      Blocks   Id  System
/dev/hda1   *          1        3654    29350723+   c  W95 FAT32 (LBA)
```

I can't seem to mount the drive (I already did the mkdir /media/windows):
```
sudo mount /dev/hda1 /media/windows/ -t vfat -o umask=000
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail   or so
```
That returns the following relevent lines:
```
[4299840.585000] FAT: bogus number of reserved sectors
[4299840.585000] VFS: Can't find a valid FAT filesystem on dev hda1.
```

Any help would be appreciated, and I thank you greatly in advance.

---

### Post by TomPreuss on 2005-12-19
Sorry to bump like this, but I was just wondering if anyone had any ideas or any suggestions at all.

Thank you very much in advance.

---

### Post by gbkyle on 2005-12-19
Try using a Knoppix LiveCD, see if it can mount it for you.

---

### Post by towsonu2003 on 2005-12-19
looks like a corrupt partition to me but it may as well be bad blocks or something like that... if corrupt partition,

found this when googled (keyword: mount corrupt harddisk), but is way advanced for me. May be you can figure this out? [http://www.linuxjournal.com/article/8366](http://www.linuxjournal.com/article/8366) 
Hopefully, at least it can be a starting point for you if it's a partition problem...

There was also this one [http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html) but I am not sure if you can use the info in there as it is about MBR...

as for knoppix, I found this on slashdot [http://linux.slashdot.org/article.pl?sid=04/10/15/2127244](http://linux.slashdot.org/article.pl?sid=04/10/15/2127244) but that won't help you till you manage to mount the drive :(

oh, and, attach the drive before booting with knoppix.

---

### Post by TomPreuss on 2005-12-19
[QUOTE=gbkyle]Try using a Knoppix LiveCD, see if it can mount it for you.[/QUOTE]
Any particular reason you suggest Knoppix over the Ubuntu live CD I'm using?

[QUOTE=towsonu2003]looks like a corrupt partition to me but it may as well be bad blocks or something like that... if corrupt partition,

found this when googled (keyword: mount corrupt harddisk), but is way advanced for me. May be you can figure this out? [http://www.linuxjournal.com/article/8366](http://www.linuxjournal.com/article/8366) 
Hopefully, at least it can be a starting point for you if it's a partition problem...[/quote]
It looks like his USB drive was mounted at ```
/dev/sda
```, which enabled him to ```
# dd if=/dev/sda of=/tmp/r1 bs=512
``` if I'm reading that correctly.  I can't even seem to get that far and mount the drive.

[QUOTE=towsonu2003]There was also this one [http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html) but I am not sure if you can use the info in there as it is about MBR...[/quote]
This also needs the drive to be mounted already.

[QUOTE=towsonu2003]as for knoppix, I found this on slashdot [http://linux.slashdot.org/article.pl?sid=04/10/15/2127244](http://linux.slashdot.org/article.pl?sid=04/10/15/2127244) but that won't help you till you manage to mount the drive :([/quote]
Exactly.

[QUOTE=towsonu2003]oh, and, attach the drive before booting with knoppix.[/QUOTE]
Yes, I have the drive already attached.

Thank you both for your suggestions, but as of now I'm still stumped.

---

### Post by poptones on 2005-12-19
did you try running an fsck? Run dosfsck on the drive and see what it tells you about the state of the fs. dosfsck -a will automatically try to fix it but be warned that might just end up with the data further obliterated.

---

### Post by TomPreuss on 2005-12-19
[QUOTE=poptones]did you try running an fsck? Run dosfsck on the drive and see what it tells you about the state of the fs. dosfsck -a will automatically try to fix it but be warned that might just end up with the data further obliterated.[/QUOTE]
```
sudo dosfsck -a /dev/hda1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Logical sector size is zero.
```
That doesn't sound good.  But is it just saying that because the drive isn't mounted?

---

### Post by TomPreuss on 2006-02-03
Okay, so here's a recent attempt:
```
$ sudo mount /dev/hdb1 /media/cbdrive/ -t vfat -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
So I try that:
```
$ dmesg | tail
[4295461.895000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4295461.896000] FAT: bogus number of reserved sectors
[4295461.896000] VFS: Can't find a valid FAT filesystem on dev hdb1.
```So I'm not thinking this is not sounding good either.

Any suggestions?

---

