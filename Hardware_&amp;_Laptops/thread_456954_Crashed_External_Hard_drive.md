---
title: "Crashed External Hard drive"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by smartalecks on 2007-05-28
I have a 160 gb Maxtor I use as a backup hard drive. I have in an external hard drive case, via USB.
It recently stopped working when I was installing windows for a dual boot. (odd?)

Anyway,  I turn it on and try to mount it I get this error:

```

Cannot Mount the Volume.

Unable to mount the volume.

Details
mount:wrong fs type, bad option, bad superblock on /dev/sda1,      missing codepage or other error,       In some cases useful info is found in syslog -try    dsmeg|tail

```

From my Google-ing I think this is a recoverable error, but do you have any advice as to where to start? 

Thanks

---

### Post by taurus on 2007-05-28
Is there anything on /dev/sda1 that you need to save because you probably need to reformat it again?

---

### Post by dasunst3r on 2007-05-28
For starters, the drive should have mounted itself when you plugged it in and turned it on.  But to mount the drive, I assume you have created a mount point (in /mnt or /media).  You may need to specify the external hard disk's filesystem, which can be done by passing the -t parameter.
[LIST]
[*]FAT16 or FAT32 -> vfat (mount -t vfat ...)
[*]NTFS -> ntfs
[/LIST]

---

### Post by smartalecks on 2007-05-28
It tries to automatically mount the drive, but that is when I get the error.

I don't want to reformat as I have alot of stuff I would like to get back.

---

### Post by taurus on 2007-05-28
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by smartalecks on 2007-05-28
This hard drive I am using as an external drive, so I don't think I can use fdisk in the way you intend?

I did df instead

```

$ df /dev/sda1
Filesystem           1K-blocks      Used Available Use% Mounted on
udev                    517888       136    517752   1% /dev

```

which isn't right, because I was using at least 70% of the hard drive. So it hasn't even been mounted properly?

Looked at syslog:
EXT3-fs: unable to read superblock


So that confirms that it is a superblock error.

---

### Post by smartalecks on 2007-05-29
*bump*

any suggestions?
anyone?

---

### Post by regomodo on 2007-05-31
mate. I know what you are going through. I have exactly the same problem and have just managed to wipe another drive in the process trying to figure out this problem. I don't think there was any v'important stuff on it, just means i wasted a lot of bandwidth.

i tried a program "dd" but i think it's the wrong app.

I've looked around and there is nothing to be found in this forum. A certain person keeps appearing each time and asks "print the result of sudo fdisk -l" and then the thread dies with no solution.

I have a lot of important stuff and i have only backed-up some of my data. I've been lax recently as my drive is known to be relatively stable. I tried something today and chuffed it up a treat. 

I've partially conceded defeat. Currently running "fsck" and pressing yes to everything. I fear it's going to be bad for me but i'll try and let you know how it goes :cry:

---

### Post by smartalecks on 2007-05-31
Thanks for the post

I have found this blog post, and I will try what he does in a minute.

[http://edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/](http://edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/)

---

