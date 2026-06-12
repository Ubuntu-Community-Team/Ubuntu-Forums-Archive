---
title: "Add a new hard drive 8.04 server"
date: 2008-08-29
forum: General Help
---

### Post by raptorman on 2008-08-29
Hello and thanks for any help.

I have Ubuntu 8.04 server installed using the command shell only. I tried adding a USB External drive and also a internal IDE drive but can not get it any of them to mount. I have installed this in the past and installed ubuntu desktop and was able to do it through the GUI but I really want to learn using just a shell. Can anyone guide me in the right direction? I have been all over the forums but have not had any success.

Thanks

---

### Post by pofigster on 2008-08-29
First, determine where the drives are using

sudo fdisk -l

Then the command:

mount [type - if it's ntfs, fat, reiserfs, whatever, specify that here] /dev/(whatever you saw from the listing above for the drive) /media/where/you/want/to/mount/it

That should do it for you.

---

### Post by raptorman on 2008-08-29
Thank You pofigster I get the following when I run that command 

But when I try to access it I get access denied even using sudo.
Am I doing something wrong? What I want to do is a backup to the USB drive.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x043c8c79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12068    96936178+  83  Linux
/dev/sda2           12069       12161      747022+   5  Extended
/dev/sda5           12069       12161      746991   82  Linux swap / Solaris

Disk /dev/sdb: 4110 MB, 4110228480 bytes
16 heads, 63 sectors/track, 7964 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x05701db6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7965     4013863+   b  W95 FAT32

---

### Post by pofigster on 2008-09-07
Sorry to take so long getting back to you on this - it looks like you have only two drives total (From your output) one drive (100 Gb) that has a Linux partition of sorts on it and then a swap partition embedded within an extended partition and then a second drive (4 Gb) formatted in Fat32 - is this correct?

What hard drive do you have Ubuntu Server edition installed on?

In any case, to mount the 4gb Fat32 drive, try this:

sudo mkdir /media/backup  <--this is to make the mount point
sudo mount -t vfat /dev/sdb1 /media/backup

If this gives you a permission denied error then I'm in over my head - but it shouldn't.  Let me know if this works.  PM me if I don't reply fast enough (within a day or so)

---

### Post by tvtech on 2008-11-10
I just wanted to say thanks, this post helped out a lot on mounting my drives on my server. believe it or not I couldn't find anything useful like the fdisk -l command in the documentation.  the man page for mount works fairly well though.   

[COLOR="Red"]This is just a side note and can be ignored[/COLOR]  For some reason though, my raid controller shows my drive format as opus and sfs.  The sfs mounted up fine with ntfs but I have no clue what opus is, I think it's nothing as I never formatted the drive.  it's a 3ware raid controller 8000 series if anyone cares.

---

