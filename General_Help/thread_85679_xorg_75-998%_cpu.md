---
title: "xorg 75-998% cpu"
date: 2005-11-03
forum: General Help
---

### Post by duffydack on 2005-11-03
I think this is related to the lag i get using Kubuntu 5.10 with the 686-smp kernel.  I installed it with the liveDVD as source and i noticed it installs and uses the 686 kernel by default, when the cd version uses 386.  Last time i installed it and went to 686-smp kernel (i have p4 HT) i experienced some lag while using the Os, moving windows and most noticeably when you goto log off, the grey shade that rolls down goes very slow and stuttery.  Just installed from the liveDVD with just thr 686 kernel and for example when you click and drag a selection box anywhere the movement stutters and my laptop fans kicked in, and when i looked at the task viewer, Xorg was using almost all my cpu.
using just 686 kernel the Os itself doesnt really lag, but 686-smp with ht on it does, a lot.  Hoary with its kernel is fine
has anyone found a fix for this kind of behaviour yet?

---

### Post by sveinn on 2006-01-26
Hello, 

I have the same problem, but when I boot the 2.6.12-9-686 kernel instead of 2.6.12-10-686 on my Dell Inspiron 6000, the issue goes away. 

The other run-of-the-mill application that sucks up a lot of CPU time is Firefox, but usually less than 50% of CPU.

Sveinn

PS after running kernel "9" for a day, it seems that Xorg is just as demanding of cpu time running "9" as with "10". the applications i use most are firefox and thunderbird and skype.

by the by, i am running gnome, guess i should have posted this elsewhere.

lo and behold, this issue is discussed at length in the gnome section of this forum:

[http://ubuntuforums.org/showthread.php?t=120764&highlight=xorg](http://ubuntuforums.org/showthread.php?t=120764&highlight=xorg)

---

### Post by MacV on 2006-01-26
That sounds very odd. Have you tried the terminal command tor? It also shows you system resource use, but without an added gui to distort the readout.

---

### Post by dresnu on 2006-01-27
Try modifying your grub's menu.lst in order to boot the kernel with the "noapic nolapic pci=noacpi" options.

---

