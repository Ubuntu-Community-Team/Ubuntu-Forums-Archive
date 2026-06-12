---
title: "GRUB is not working."
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by Tea on 2006-02-01
Hi, 

I Recently tried to create a FAT32 partition in windows, and I really regret it now.

First, GRUB lost the harddrive (I *think*) no options for loading an OS came up when it loaded, just gave me Error 17

So, I travel over to [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=GRUB+Error+17]()  and do as it instructs, working from the live CD. 

So, now I have GRUB loading, but still giving "Error 17" whenever I try to load an OS. It says the file system is unknown. When I edit the "root" option in grub to (hd0,1) it will start loading kernel, then die after a "kernel panic".

To add insult to injury, Windows still works through all of this.

Please help me rescue my system!

(Edit: Ive used Ubuntu for about a month now, just thought that im more likely to get Gruby help in the installation forum.)

---

### Post by az on 2006-02-01
In general terms, I think you created an extra partition before your linux ones.  That bumbed all the partition names up.  For example, hda5 would now be hda6.  This is what I suspect happened.  

You need to boot a live cd (or the install cd), fix your grub boot.list to point to the correct partition, and change your fstab, too.  Then chroot into that partition and do a grub-install /dev/hda again.

---

### Post by Tea on 2006-02-01
I understand what your saying, but im not too sure what to do, I have live CD up now, where do I start, I'm guessing im going to need to mount a partition then edit the files?

EDIT: Ok, using the disks tool, I now have my Ubuntu partiton mounted, now what?

EDIT2: Thank you Azz, after a bit of fooling around, I got it, thanks again! All i needed to do was change a line from hda3 to hda2.

EDIT3: Thanks!

---

### Post by classem2003 on 2006-02-01
I think that your problem is the grub.list. Take into account this: In /dev the counting begins in 1 /dev/hda1(windows), /dev/hda2 but the fisical partitions in the disk begin in 0, so you have (hda0,0), (hda0,1). I am not an expert but I have a fat32 partition on my disk without problems. May be you can check this document,
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

in the section "rescue mode".

and if you can read spanish, 

[http://www.guia-ubuntu.org/](http://www.guia-ubuntu.org/)

---

