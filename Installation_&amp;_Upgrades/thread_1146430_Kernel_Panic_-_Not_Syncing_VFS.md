---
title: "Kernel Panic - Not Syncing: VFS:"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by JeremyTheGeek on 2009-05-02
Hey everyobdy,
Yesterday I installed Ubuntu 9.04 on my lappy. Today when I went to reboot it I get a error saying...

[HTML]Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)
Dumping ftrace buffer
(ftrace buffer empty)[/HTML]

Seeing as this is a new install and there are no other kernels to boot off of, this poses a major issue for me. 
I also rebooted a few times already without any issues before the error

If you know how to fix, or need some other info please just leave a message

Thanks Much
-Jeremythegeek

---

### Post by JeremyTheGeek on 2009-05-02
Sorry about this. Really need to get this fixed
BUMP!

---

### Post by Jaymoon on 2009-05-04
I'm having the same problem.

Using ext4 if that matters.  I woke up and came to find my computer sitting at this error today too:

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)
Dumping ftrace buffer
(ftrace buffer empty)
```

I was able to boot from the live-cd and eventually mount my normal / partition to a folder.  From there I opened up my normal /etc/fstab file, and compared it with the UUID labels in the Partitioning program (gparted I think).

Well everything checks out.  It's booting from the right partitions on the drive.  (I have /boot, swap, /, and /home on one drive)

So if the kernel updated on it's own, how in the world would we go back to using the one that worked, or make the new one work!

This would really suck for someone trying out Ubuntu for the first time, and as soon as they reboot get a kernel panic error.

:confused:

---

### Post by JeremyTheGeek on 2009-05-05
Solved the issue, But not in the way that I preferred. 
Since it was basically a fresh install anyway I just did a reinstall :/

Always have /home on a separate partition.

(Also May the 4th be with you)

---

### Post by utkjamie on 2009-05-15
> **JeremyTheGeek said:**
> Solved the issue, But not in the way that I preferred. 
Since it was basically a fresh install anyway I just did a reinstall :/


That's too bad. The *scorched earth* "solution" of nuke and rebuild is more fitting for Windows users. There should have been a better solution for you.

---

### Post by mgarrana on 2009-08-10
hi
i have the same problem, but it worked when i rebooted using an older kernel , which is a default option in ubuntu 9.04 , i am using X64 version
everything is working , but if you were running virtualbox on the previous kernel , you'd have to 
sudo /etc/init.d/vboxdrv setup
i will hold on to that untill we get a clear definition of what's happening :)

---

### Post by lunamystry on 2009-08-10
I think i am having a similar problem. My apologies to who started this thread I wanna see if i cant get a solution.

what happend with me is that i tried to install bootgraph but i had forgotten that i didnt have enough space left. I quickly deletd useless files while it was installing but i guess i was too late because after using the acer aspire one ssd for a while i restarted having forgotten about the install issue then i got the error that a whole lot of things in /init: line ... Were not found then i

---

