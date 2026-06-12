---
title: "Dude where's my hard drive?"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by Professorb on 2007-05-13
I've got the live CD, i've done the md5sum and the CD is fine. I've had it running in live mode... enjoyed a few games of Su Doku and I'm ready to install.

I'm trying to dual boot, I click install and I enter my language, my timezone, my keyboard layout and then the partitioner comes up.

I have the option of manual only and the on the prepare partitions screen, I have a blank box, with nothing to partition.

I click on computer and it seems I have no hard drive...

It's a S-ATA which I know can be problematic

What do I do?

---

### Post by smithman89 on 2007-05-13
Well, usually it should show something like sda1 as your harddrive when you use sata drives.  But this is pretty weird, maybe you should try the "Largest Continuous Space"  option on the partitoner.  If you cant do that, and you dont want to reformat the whole thing, try going through the terminal on the disc and type in```
sudo mount /dev/sda1
--or--
sudo mount /dev/sda
```
Im not certain this would work, im just guessing since i dont have the problem in front of me, but once the computer recognizes the hard drive, then the installer should too.

---

### Post by Professorb on 2007-05-14
I don't have a largest continual space option, it only gives me the option of manual.

I tried those and the result was: "mount: can't find /dev/sda in /etc/fstab or /etc/mtab

Thanks for trying though.

---

### Post by spudtheimpaler on 2007-05-14
I have the same problem. I have a new HDD (Part number WD1200UE, Western Digital, EIDE) which ubuntu can't see. I've got no way to test to see if the hdd is dead, nothing else to test it in, and i can't see any way to find it. it's not in /dev/ ... what other commands can i issue to try and find it?

I've also posted this in linuxquestions.org ([http://www.linuxquestions.org/questions/showthread.php?t=553837](http://www.linuxquestions.org/questions/showthread.php?t=553837)) with my listing for lspci...

Any ideas?

Thanks

Mitch

---

