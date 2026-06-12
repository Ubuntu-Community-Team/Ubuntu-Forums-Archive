---
title: "PC can't boot but LiveCD works."
date: 2010-02-15
forum: Hardware
---

### Post by Uuranor on 2010-02-15
Hello everyone!
I hope someone can help me even if is not an ubuntu related issue (I don't know if this is the most appropriate section to publish this post, anyway, so feel free to move it).

Since two days ago my computer is not able to boot anymore, it gets stuck as if it wouldn't be able to find the hard disk, and it doesn't show grub2.

The 'funny' thing is that I am able to use a LiveCD and access the disks from there (so I suppose it is not a hard disk related issue). I tried to reinstall grub2, to format the whole hard disk and reinstall ubuntu, but nothing happened. I tried also to edit the BIOS options and to clear the CMOS using the jumper. I tried to choose the 'Boot from first hard drive' option on the Ubuntu 9.10 live cd menu. No results at all, black waiting screen.

Using the LiveCD the computer works properly (ok, except for poor performances, but that's normal), so I'd exclude a RAM or CPU related problem. I prefer to avoid to buy random computer pieces until I know what's the problem, and trying to safe the situation via software (also cause I probably have to buy a lot of new pieces if it is - for example - a mobo-issue).

Any idea about what could be and how to recover the boot?
If not, can you suggest me or think any way to force the boot using a floppy or the LiveCD?

Thanks, and sorry for my ugly english :)

---

### Post by acornbrain on 2010-02-16
I hope you find some answers, Uuranor, because I am having a very similar problem:
 
[http://ubuntuforums.org/showthread.php?t=1407927](http://ubuntuforums.org/showthread.php?t=1407927)
 
-brian

---

### Post by acornbrain on 2010-02-16
Can anyone please help with this?

I need to somehow recover my PC using the Live CD !!!

I don't know if it was a faulty update, or apt-get gone wrong, or what caused all this, but I can't boot normally anymore; only from the Live CD as generic "ubuntu" user.

I am on 9.04 Jaunty.

HELP!

-brian

---

### Post by cabbrick1243 on 2010-05-11
Realize this is old, but honestly it sounds as if your hard drive in your computer has kicked the can and stopped working all together.  To check this boot into the live CD and start Gparted, and try to find any partitions.  If none appear than either your hard drive is faulty or there is a problem with the connection to the motherboard.  Please check, and if not afraid to open your computer then simply pop in and format a new drive.

---

