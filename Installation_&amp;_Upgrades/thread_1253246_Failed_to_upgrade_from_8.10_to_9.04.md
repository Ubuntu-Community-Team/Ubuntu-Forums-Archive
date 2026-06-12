---
title: "Failed to upgrade from 8.10 to 9.04"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by new_to on 2009-08-29
Hello,

I've been using 8.04 for the last year or so till last night, when I upgraded to 8.10. Apparently it's a necessary step on the way to get 9.04. Well, the problems started after finalizing the new installation (8.10) and booting the system, it got stuck and didn't let me login. It froze just after finishing with the initial Ubuntu progress bar.

So, I restarted the machine and went to the menu under "Esc", ran some tests, fixed some problems (I really don't know what :)) and the system was fixed. Then I was able to login, all my staff was there and I could continue the journey to 9.04. Long story short, it wont let me in again after upgrading, and like before it freezes after the initial load bar. 

More details:
* It shows weird screen (on the 8.10 is was completely black) like it's f@*&ed up, (sorry but I have no better desc. but here's a picture). [IMG]http://i28.tinypic.com/2wn7jlt.jpg[/IMG]

* On the way to the menu under "Esc" I noticed that I got [fail] for "activating swap ...", when looking for a solution online I have found the following instructions:```
sudo -s
swapoff -a
dd if=/dev/zero of=/host/ubuntu/disks/swap.disk bs=1M count=265
mkswap /host/ubuntu/disks/swap.disk
swapon -a
exit
```(for some reason I can't this thread any more), when submitting those lines into my system I get that "swap.disk" is not there and/or something like "the disk is busy".

I have no idea what to any more as well as how to test what's causing the system to fail, please advise.

---

### Post by new_to on 2009-08-30
If it's not clear enough please let me know ...

---

### Post by new_to on 2009-08-30
Can anyone give me direction/hint/something?

---

### Post by new_to on 2009-08-30
OK, I got the drift ... going to install windows so I guess this is post should be marked as resolved (and with the best solution if I may add).

---

### Post by overdrank on 2009-08-30
> **new_to said:**
> OK, I got the drift ... going to install windows so I guess this is post should be marked as resolved (and with the best solution if I may add).

Hi and what is the model of the graphics card?
Have you tried booting into recovery mode which is usually the second choice from the grub and using the xfix option. After selecting and running xfix you should be given the option to boot normally.

---

### Post by new_to on 2009-08-30
> **overdrank said:**
> Hi and what is the model of the graphics card?
Have you tried booting into recovery mode which is usually the second choice from the grub and using the xfix option. After selecting and running xfix you should be given the option to boot normally.

Hi,

Thanks for your response!

I did try recovery mode, I even wrote it in the initial post but with lame description as I'm not familiar with the exact terminology, sorry.

I also try the xfix option ... it didn't help with 9.04 (I think this option solved the problem with 8.10). The name and model of the video card is: "MSI Radeon HD 3650 Graphics Card - ATi Radeon HD 3650 750MHz - 512MB GDDR3 SDRAM - PCI Express".

---

### Post by brett- on 2009-08-30
Read my post.  Same problem.  Same graphics card.  No solution, even with fglxr.  Though I did get further than you in the upgrade.  I also have minor graphics problems on a laptop 9.04 fresh install though not as crippling.  I think 8.10 is stable, 9.04 is buggy.

---

### Post by new_to on 2009-08-30
> **brett- said:**
> Read my post.  Same problem.  Same graphics card.  No solution, even with fglxr.  Though I did get further than you in the upgrade.  I also have minor graphics problems on a laptop 9.04 fresh install though not as crippling.  I think 8.10 is stable, 9.04 is buggy.

So, how do I go back to 8.10 then?

---

### Post by brett- on 2009-08-30
Pop in 8.10 and re-install.  If you have a separate /home partition, specify that the partition manager not format but use as /home.  If you don't have separate /home then boot with a live CD and try to copy your data files to another hard drive.  The problem will be permission and not having access to sudo from the live CD.  Someone here may surely know a work around that.  Other method may be to connect the 9.04 HDD to another linux box (or windows with ext3 capability) and move the files.

---

### Post by running_rabbit07 on 2009-08-30
Burn the 9.04 intsall and do a clean install. 

If there are files you need to back up first, then you can boot via the LiveCD and back them up.

If you dan't already have one, when you do your install be it 8.10 or 9.04 you should make a /home partition to make upgrades and clean installs easier.

Honestly I have yet to here anyone say they upgraded from 8.10 to 9.04 without having major issues. I have tried it with 2 different machines and both failed to upgrade.

Please be aware that this is a voluntary help forum. Sometimes on the weekend the person who knows a fix to your problem may not be online.

---

### Post by running_rabbit07 on 2009-08-30
> **brett- said:**
> Read my post.  Same problem.  Same graphics card.  No solution, even with fglxr.  Though I did get further than you in the upgrade.  I also have minor graphics problems on a laptop 9.04 fresh install though not as crippling.  I think 8.10 is stable, 9.04 is buggy.

Other than the upgrade process, I have had no problems with Jaunty. I have installed it on multiple machines and it has ran greatly.

---

### Post by new_to on 2009-08-30
> **brett- said:**
> Pop in 8.10 and re-install. If you have a separate /home partition, specify that the partition manager not format but use as /home. If you don't have separate /home then boot with a live CD and try to copy your data files to another hard drive. The problem will be permission and not having access to sudo from the live CD. Someone here may surely know a work around that. Other method may be to connect the 9.04 HDD to another linux box (or windows with ext3 capability) and move the files.

I would like to keep same settings/applications/etc. as I had it before, if I re-install 8.10 is it going to overwrite all of my data? 

> **running_rabbit07 said:**
> Burn the 9.04 intsall and do a clean install. 

If there are files you need to back up first, then you can boot via the LiveCD and back them up.

If you dan't already have one, when you do your install be it 8.10 or 9.04 you should make a /home partition to make upgrades and clean installs easier.

Honestly I have yet to here anyone say they upgraded from 8.10 to 9.04 without having major issues. I have tried it with 2 different machines and both failed to upgrade.

Please be aware that this is a voluntary help forum. Sometimes on the weekend the person who knows a fix to your problem may not be online.

Thanks, I saw the thread going to the second page  each time before I replied, I guess because it's the weekend I have too much spare time and was ignoring the fact experts might have life outside the board :P.

I'll try to look for this LiveCD everybody's talking about and continue from there ... I really don't want to go back to Windows.

---

### Post by new_to on 2009-09-02
I didn't do anything yet as I can't backup the data, LiveCD wont boot on that machine (I get the same screen), I even tried to disable the Video Card and work with the one on board ... with no success.

Is there any other solution that can "FIX" the current installation? Do you think they're going to release a working version of 9.04?

---

### Post by brett- on 2009-09-05
If the live CD won't boot and you have the optical drive set in the BIOS as first boot device then you may have a problem with your machine.  If it is an older machine, clear the CMOS and set optical drive to boot first in BIOS.  If that does not work, replace the small battery on the mother board.

I prefer the Ubuntu i386 alternate install CD (you don't need the live overhead as you've seen it all before).

---

