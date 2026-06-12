---
title: "DVD drive tray closes automatically"
date: 2010-09-01
forum: Hardware
---

### Post by amr-maro on 2010-09-01
[SIZE=2]Hi, I'm using Ubuntu 10.04 and I have a problem with my [COLOR=Black]SATA "ASUS DRW-2014L1T" DVD drive[/COLOR]. Here are the symptoms:
[/SIZE]
[LIST]
[*][SIZE=2]The tray closes immediately by itself after a full opening by  pressing the eject button.[/SIZE]
[*][SIZE=2]If I  manage to put a CD/DVD disc in the drive (very quickly), [COLOR=Black]nothing happens[/COLOR], as if there  isn't any disc inside the drive.[/SIZE]
[*][SIZE=2]I can see the drive in "Computer" from "Places" menu.[/SIZE]
[*][SIZE=2]I can't [COLOR=Black]eject [/COLOR]or [COLOR=Black]mount [/COLOR]the drive manually using the terminal.[/SIZE]
[/LIST]
[SIZE=2]The same problem existed in Ubuntu 8.04 before I made a clean installation of 10.04 hoping to get rid of the problem. The drive was working properly in Windows XP.

I have another PATA "ASUS CRW-5232AX" CD drive which is working without any problems.

Please help me figure out the reason of this problem.

Thanks!
[/SIZE]

---

### Post by varunendra on 2010-09-03
Okay, I picked your thread up two days ago but didn't reply so that maybe someone more experienced could pick it up. But now that you are repeatedly bumping [a solved thread ]("http://ubuntuforums.org/showthread.php?p=9795973#post9795973")instead of this one of your own, I guess you want me or venturosa to reply you.

But let me declare first that I'm not very confident at this (that's why I didn't reply earlier, it wasn't ignorance :()

So let's begin. Please confirm:

[LIST=1]
[*]Does the drive still work properly with XP?
[*]Is it not able to read any disc at all under ubuntu (and does it read them under XP)?
[*]What do you do in terminal to **eject **or **mount **the drive manually? Does it show any error messages?
[*]If you put a Live CD in the drive & reboot your computer, does it boot from the CD?
[/LIST]
If you don't have XP now, try [HBCD]("http://www.9down.com/Hiren-s-BootCD-10-6-352820/"). It contains live XP besides many other useful tools.

In addition to the answers to above questions, please post outputs of following commands:

(Before running these commands, reboot, then put a cd in the drive, let it stop.)
```
lshw -C disk
``````
dmesg | tail
```

---

