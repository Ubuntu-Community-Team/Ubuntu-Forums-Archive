---
title: "GRUB error 17 after deleting linux partition"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by Pontoola on 2009-07-10
I have no clue why this error comes up on my screen after the ACER logo comes up its weird : / can someone help me out please?  That would be wonderful :)

---

### Post by mikewhatever on 2009-07-10
The main body of GRUB resides under /boot/grub in the root partition. If you delete such a partition, GRUB can't find the files it needs for booting, and complains.

---

### Post by bernied on 2009-07-10
You need to be clearer about the rest of your system before others can help you, else we will just be guessing.

Why did you delete the partition?
Do you still have a linux distro installed?
Are you trying to get rid of linux and revert to using some other operating system? (Windows??)

This might help (but I'm just guessing):
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Pontoola on 2009-07-10
> **bernied said:**
> You need to be clearer about the rest of your system before others can help you, else we will just be guessing.

Why did you delete the partition?
Do you still have a linux distro installed?
Are you trying to get rid of linux and revert to using some other operating system? (Windows??)

This might help (but I'm just guessing):
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)
I deleted it cuz I never used it lol no offense to linux or anything but I wasn't ready to dive into it cuz I'm basically a gamer and not into that stuff really atm lol.  What I did was I deleted the Linux Partition on my computer when I had vista running normally and then that happened : /

---

### Post by Pontoola on 2009-07-10
Bump!

---

### Post by bernied on 2009-07-10
There are plenty of answers in that thread I linked to. 
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

You've deleted the bootloader, which although you couldn't see it, was booting Windows. I suggest you reinstate the windows bootloader. There are at least three ways to do that described in that thread.

Herman explains it better than me, and also provides solutions, here:
[http://members.iinet.net.au/~herman546/p18.html#STEP_ONE](http://members.iinet.net.au/~herman546/p18.html#STEP_ONE)

---

