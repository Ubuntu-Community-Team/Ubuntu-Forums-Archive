---
title: "Grub 24 Error on Laptop"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by The Wanlorn on 2006-10-11
I have Dapper Drake installed on my laptop as the **sole OS**.  It **does not boot up** anymore.  Instead, it gives me a GRUB error 24 and then stops.  This is all the information I can give you because this is all that appears on my screen:
```

The AC power adapter type cannot be determined.  This will prevent optimal system performance.

Strike the F3 key (before the F1 or F2 key) if you do not want to see power warning messages again.

Strike the F1 key to continue, F2 to run the setup utility.

Broadcom UNDI PXE-2.1 v8.1.4
Copyright (C) 2000-2005 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
All rights reserved.

Broadcom Base Code PXE-2.1 v1.0.1
Copyright (C) 2000-2005 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM.
[COLOR="Blue"]GRUB Loading stage1.5



GRUB loading, please wait...
Error 24[/COLOR]
```
Does anyone know how to fix this?  I have a lot of important files on there that I haven't had a chance to back up.  It would be incredibly *not good* if I lost them.

](*,)

**ETA:** The stuff in blue's the stuff that is the issue.  The other two things, haven't ever caused me any trouble.

---

### Post by Herman on 2006-10-11
I would use another computer to download [Super Grub DIsk]("http://adrian15.raulete.net/grub/tiki-index.php") and burn it to a CD and boot with that instead.
Super Grub Disk would probably be useful for helping to repair your Grub as well. It is availabe for floppy disks or USBs as well.
Regards, Herman

---

### Post by Herman on 2006-10-11
Quote from the Grub Manual,
> 24 : Attempt to access block outside partition. This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool).  In Super Grub DIsk, after you select your lnguage, try 'Gnu/Linux'-->'Boot Gnu/Linux' to boot by your own Grub menu, or, if that doesn't work, then try 'Gnu/Linux'-->'Boot Gnu/Linux Directly', to boot your kernel and initrd by their symlinks in / (root). If neither of those will work, it looks like you might have some other kinds of troubles. 
if it's a corrupt filesystem, you can try  running fsck on it. It's best to do that from a Live CD, with the filesystem not mounted. [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") is the one I use, because of the way it doesn't mount the hard drive partitions.
```
e2fsck -c -c  /dev/hda1
```

---

### Post by The Wanlorn on 2006-10-11
Well *crap*.  It appears that my issues are way more troublesome.  The two Super Grub Disk things reboot the system and give me the same error.

And then running fsck from GParted gives me the following:
```

e2fsck 1.39 (29-May-2006)
e2fsck: Filesystem recision too high while trying to open /dev/sda1
The filysystem revision is apparently too high for this version of e2fsck.  
(Or the filesystem superblock is corrupt)

The superblock could not be read or does not describe a correct ext2 
filesystem..  If the device is valid and it really contains an ext2 
filesystem (and not swap or ufs or something else), then the superblock 
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
All in all, that does not look good.  Does this mean I have managed to completely destroy my laptop and thus lost everything on it?

---

### Post by azelter on 2006-10-11
Try booting with the dapper live cd. You should then be able to mount your laptop harddrive by hand and read it. Also, as a last resort, you can always pull out your laptop harddrive and connect it to another computer via a external usb adaptor. This will bypass any other hardware issues with your machine.

---

### Post by The Wanlorn on 2006-10-11
This is starting to make me tear my hair out!  Thank you, both, for your suggestions.

Unfortunately, tbe drive can't be mounted when I boot with the Live CD.  After having the computer guys at my uni work on it, it appears as though the drive itself is fine, but the partition is shot to hell and back, somehow.

Their suggestion was that I boot up a Knoppix Live CD and run dd on it to copy an image of my entire drive to my desktop computer, repartition the laptop, and then see what I can get off the image.

Does anyone who has more experience with Linux than me and the guys there know if this will work?  Or, at least, if it has a better chance of allowing me to recover all of my music/pictures/etc. than repartitioning and running the lost-and-found thing that Ubuntu comes with?

---

### Post by Herman on 2006-10-12
That's basically a good idea, it might work, I can offer you some of my most best links on the subject, but you will have to do a little reading as these type of problems are not so common, so it is hard to gain experience in them. 

[Testing Your Hard Drive in Linux]("http://yhslug.tux.org/docs/hdtest.htm")
You should be able to use any Live CD for this, Dapper, GParted, or Knoppix.

[dd_rescue]("http://www.garloff.de/kurt/linux/ddrescue/")
dd_rescue is available in my Ubuntu repositories, but I don't know if it is included in the Dapper Desktop CD or not, it is supposed to be in Knoppix, I'll check.

[GNU ddrescue]("http://savannah.gnu.org/projects/ddrescue/")

[TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")                        Testdisk -->[ Damaged Hard Disk  ]("http://www.cgsecurity.org/wiki/Damaged_Hard_Disk")
TestDisk is included in GParted LiveCD and Knoppix. I am not sure if it is included in Dapper Desktop, but I'll check. It is available in the Ubuntu repositories. 

And you might also like to look over the list of applications in [INSERT,]("http://www.inside-security.de/insert_en.html")  in case you see anything there you like better.

Any information you would care to share with this forum might  be helpful to other users with the similar issues in future, if you feel like reporting what you did and got along. Good luck with it.

Regards, Herman :D

---

### Post by Herman on 2006-10-12
I don't know how you will go using a 'dd' command through your ethernet connection or whatever. I would physiclly remove the hard disk from the laptop and either use an external USB caddy for it or install it in the desktop as hdb, (hard disk number2), and use the 'dd' command in the normal way.

Here's a link that gives an example of how to use a 'dd' command with 'Netcat', but I think you would need to be pretty good with Linux to use it with the degree of confidence needed, especially when the situation is complicated by another problem already. '[All About The 'dd' Command]("http://www.linuxquestions.org/questions/showthread.php?s=&postid=1848770")'  and look for 'If you want to make a partition image on another machine'.

I would make the backup first, then I would keep trying to repair the filesystem with whatever other ideas I could come up with, for example the one your first fsck output suggested:> and you might try running e2fsck with an alternate superblock:e2fsck -b 8193 <device>
debugfs, I have read, in the hands of an expert, can be used to repair a disk that fsck can't. But I don't know how to use it. Maybe you'll be able to get help from someone else around here with that...

---

### Post by xyz on 2006-10-12
Hi-
This is much more a question than any kind of help; however I'd be curious to find out whether DBAN or Digital Dolly would be useful in this case?
Thank you!

---

### Post by Herman on 2006-10-12
DBAN -[Darik's Boot And Nuke]("http://sourceforge.net/projects/dban/")

[Digital Dolly]("http://www.download.com/3000-2248-10220909.html")         |       [Digital Dolly - How do you use it?]("http://www.bleepingcomputer.com/forums/topic35979.html")

I don't know. Every avenue is worth considering.
--------------
Here are four of my favorite links about the e2fs and ext3 filesystems, they require some reading, but they do explain quite a lot of the fundamentals of the subject we are trying to deal with here. 

[5.10. ]("http://www.tldp.org/LDP/sag/html/disk-usage.html")[Filesystems]("http://www.tldp.org/LDP/sag/html/filesystems.html")[SIZE=-1]**  Linux System Administrators Guide**[/SIZE]
     
     [Design and Implementation of the Second Extended Filesystem]("http://web.mit.edu/tytso/www/linux/ext2intro.html")
 [B]
[ EXT3, Journaling Filesystem]("http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html")[/B]

      **[Linux ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html")**


Regards, Herman

---

