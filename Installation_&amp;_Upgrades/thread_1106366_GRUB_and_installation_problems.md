---
title: "GRUB and installation problems"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by Muboo on 2009-03-25
Hi!
I recently decided to install Ubuntu on my desktop on a separate partition (I'm sorry if I am mistaken on technical terms, but I am pretty much a newbie when it comes to any low-level or hardware/BIOS. Also sorry for odd characters, I haven't configured my keyboard as I am running on a live CD).

I previously had
[LIST]
[*]Internal HD
[LIST]
[*]Windows Vista
[*]Windows 7
[/LIST]
[*]External HD
[LIST][*]Just some files[/LIST]
[/LIST]

And now, for some reason, I have
[LIST]
[*]Internal HD
[LIST]
[*]Windows Vista
[*]Windows 7
[*]A strange ubuntu-looking partition
[/LIST]
[*]External HD
[LIST][*]Just some files[*]My GRUB and my ubuntu files[/LIST]
[/LIST]

Since I'm probably wrong or not descriptive enough, I'll post screenshots, wherein SDA is my internal hard drive and SDB is my external hard drive, from GParted. Now this is seen from a live CD, remember, not from my real Ubuntu installation.

[IMG]http://localhostr.com/files/88ccac/SDA.png[/IMG]

[IMG]http://localhostr.com/files/6f54ff/SDB.png[/IMG]

Errors I'm getting:
-I cannot boot without my external hard drive working and connected, since the GRUB is on it (Error 21 at stage 1.5, if this means anything to any of you (it doesn't to me))

Now what I'd like:
-Move my GRUB to my internal hard drive (SDA), so that I don't need my external hard drive (SDB) to be plugged in and working to boot.
-Delete/remove anything, as long as I can reinstall Ubuntu and 7 after on 2 partitions of my SDA.


I'm sorry for such a big question, but I dumbly forgot to unplug my external hard drive before installing Ubuntu and I probably messed up somewhere else in the wizard.<

Thanks for your help,
Lazlo

---

### Post by Muboo on 2009-03-25
Sorry, but B.U.M.P.? If no one knows a solution, could someone please tell me if it's at least possible? Thanks!

---

### Post by warchief_ryan on 2009-03-26
From the pics posted it looks like there's no Ubuntu installation on /dev/sda, only on /dev/sdb(the external drive).

So you could just delete /dev/sda3 and /dev/sda5 and repartition those and install Ubuntu there, which will install GRUB also.


If Ubuntu was even installed on /dev/sda then you might have been able to do something like, sudo grub-install /dev/sda* (* being Ubuntu's partition) to install grub on the internal drive.  Not sure haven't had to do it.

---

