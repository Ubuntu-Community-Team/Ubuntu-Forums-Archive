---
title: "System freezes at logo boot screen (how can i diagnose?)"
date: 2008-07-22
forum: General Help
---

### Post by azo313 on 2008-07-22
I have a dual boot Ubuntu 8.04 and Windows XP. Windows XP boots and loads just fine... no problems. Ubuntu worked for the first two days, but now freezes at the boot Ubuntu logo screen.

Is there any way to show what's going on behind that screen so I can try to see what's causing it to freeze?

How would you diagnose this issue without re-installing the entire OS.

---

### Post by Dr Small on 2008-07-22
First off, you would have to mount the drive while in a LiveCD so you can edit /boot/grub/menu.lst and remove:
```
ro quiet
quiet
```

From the kernel lines. Then, save it, and reboot.

---

### Post by Locutus_of_Borg on 2008-07-22
at grub, highlight the ubuntu line, press e, highlight the kernel line, press e, delete at the end of the line the word "quiet" press enter, press b, observe messages

alternatively, if you do get it to boot, enter dmesg into terminal

---

### Post by dez93_2000 on 2011-09-03
hi, coming to this thread late, but have same problem.
In natty, menu.lst no longer exists.
1. does a differentially named file now do the same/similar job?
2. since i can get it to boot if i restart (it only hangs after hibernation) do i still have to liveCD or can i edit it as root (or sudo or whatever. still quite noobish)
3. using dmesg, i don't really know what i'm looking for. The vibe i get from this ([http://linuxgazette.net/issue59/nazario.html](http://linuxgazette.net/issue59/nazario.html)) is that eth0, the ethernet functionality, is the last thing on the kernel to-do list, and thus if it gets to there the kernel has booted. So
3a. if it doesn't get to there i have my culprit, i guess, but if it doesn't get to there, i.e. it hangs, i have to restart then find the hang point which will precede the subsequent restart & boot. Is there a 'restart / boot button' event i can look for, or any tips for helping me find this?
3b. if it DOES get there, then subsequently hangs, either immediately or after doing some other stuff, is there a secondary dmesg-style logger i should be looking at?
3c. or what if the problem is that it's hanging BEFORE the ilnux kernel is initiated, e.g. if the problem is that somethign in the hibernation sequence causes something in the 
   Load BIOS > Load kernel > enjoy ubuntu
sequence to be edited so it doesn't work?

Huge thanks in advance. I've had this for at least 3 previous versions of ubuntu.

---

