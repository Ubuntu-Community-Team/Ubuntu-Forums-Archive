---
title: "Dual-Boot problem on Raid0 Setup"
date: 2008-10-11
forum: General Help
---

### Post by zero-Q on 2008-10-11
hi,
I have a problem with dual-boot installed on raid0 setup. I m using now 8.10 ubuntu beta, and I installed ubuntu according to the this [website]("http://wiki.auzigog.com/My_Ubuntu_(7.10)_Installation"), and now there is no problem with ubuntu boot but after grub selection of xp entry, in only 1sec. the boot screen froze as a black screen and the windows boot progress never appears. I tried too many grub entry for xp, but I could not manage to boot xp, only 1 way to boot that windows cd and fixmbr :) but in this grub is over :)
thx
kind regards

---

### Post by zero-Q on 2008-10-14
++up++

---

### Post by zero-Q on 2008-10-15
+++up+++ :)

---

### Post by zero-Q on 2008-10-16
++++up++++ till replied or solved XD

---

### Post by zero-Q on 2008-10-19
up :(:(:(

---

### Post by Cresho on 2008-10-19
raid0?  are you running raid like 2 hard rives stripped or mirrored?  If you are using a motherboard raid system, It will not work on Ubuntu.  Windows and drivers will see it but Ubuntu will not

Ubuntu works on "TRUE" raid systems and not pseudos.  The  market is flooded with this.  I suggest you unbind your raid system and run each drive on its own.  Do not believe on the benchmarks and do not believe in the hype.  I have 2 systems, one raid, the other not for Linux purpose and I do not wish to buy a real raid system.  In a pseudo system, you get a 10% increase and that is it!  I booted both systems with similar specs and both boot at identical speeds raid or not.

Ubuntu will only work on True raid.  I did a research on this and I suggest you either get a true pci raid card or forget it.  I tried raiding stripped on 2 500gb hardrives.  After I got windows working, I just noticed a 10% increase but benchmarks stated better but of course transfering files was what I tried and it ran the same but probably 5% increase in performance only.  Then I installed ubuntu and it would not install.  I could not get ubuntu to see my raid system. this is just one link even this guy says or mentions a "fake system" [http://ubuntuforums.org/showthread.php?t=600410](http://ubuntuforums.org/showthread.php?t=600410)

you said you have your Ubuntu booting?  well I am just stating something here since nobody has and it is actually a bumb  8)  You may be a victim of a fake raid system.  I tinker alot and I did not see a benefit from a fake system so i left my main pc without raid which is still fast or faster than most raid0 systems.

---

### Post by zero-Q on 2008-10-20
well thanks for suggestion but firstly indeed I m pleased about the raid0 performance against non-raid systems, I had tried both and there is visible performance difference. secondly my raid0 has huge archive and I dont wanna spend my time to back up all. thirdly because of 1-2 reasons I should go on with fake raid with both linux and windows :). and finally I used ubuntu on raid0 fake raid while 6.10 days :), but after 7.04(at all other linux releases) there was a buf with fake raid but now with 8.10 the bug is over but a new 1 appeared about the boot loader problem. as I said now there is no problem between ubuntu and fakeraid, ubuntu has been already installed on raid0 and it works perfectly, windows xp booting from grub is only problem with fakeraid.

and I have a new info about my broblem, if I try to boot windows in safe mode, it hangs in loading of ntoskrnl.exe, maybe the last info may give a clue about the problem.

---

### Post by Cresho on 2008-10-20
ahh i see..your windows is not booting from grub.

then you need to post your fstab here.

sudo gedit /boot/grub/menu.lst

you also need to state if you are using S ata or reguler ide.  Reason is because grub does not recognise sata and treats it as hdo or hd1 instead of sda1 or sda2 etc.  If your windows xp is mounted, then please post what its mounted as!

do a 

df in terminal and post output  If I don't get to you, someone will.

---

### Post by zero-Q on 2008-10-20
today I thought I tried all grub entries but for 10mins I hade made it be over :), I used this grub entry now, both OSs work and boot perfectly with grub :) this is my new grub xp entry
title XP
root (hd0,0)
chainloader (hd0,0)+1
makeactive

the old 1 was:
title XP
root (hd0,0)
chainloader +1
makeactive

---

### Post by Cresho on 2008-10-20
windows loves to be ontop.  If it is a second partition, it will refuse to boot.  that is why you had to do the top modification!

:KS:KS:KS:KS:KS

---

### Post by zero-Q on 2008-10-20
yeah but it is on the first partition but just I wanna try this entry and then shocked :) it worked...

---

### Post by Cresho on 2008-10-21
yep!  that is exactly what your entry says.  hd 0,0  Interesting to see grub didnt catch any of this or set it up right.

---

