---
title: "upgrade failure or slow upgrade?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by coolclassic on 2009-10-30
At present my system appears to be upgrading but it is taking a lifetime. I started the upgrade last night at 8ish. When I got up this morning the system was installing packages this is still happening with cpu usage at a constant 10% on one cpu. 

What I don't have is any indication of progress of upgrade. Upgrade window is blank no progress bar or anything. So my guess is 

1: has the upgrade hung
2. Due to absence of active window is it awaiting further prompt from me.
3. Or this does take a long time

Is there any way to see progress of install from shell? and/or is it safe to reboot?

---

### Post by ajgreeny on 2009-10-30
Are you sure there is not a dialog box open behind one of your windows waiting for some input from you?  It occasionally happens, though generally pops up in front of everything else.

---

### Post by henryfarbles on 2009-10-30
having a similar problem. started the upgrade yesterday update-manager -d. it took a long time to download everything but it seems to have grabbed all the data. i let it run overnight and this morning it was still installing the upgrades. The terminal just prints out 'y' over and over. same thing today with apt-get.

---

### Post by coolclassic on 2009-10-30
The dialog box is all grey out, it is the only window open on desk top.

---

### Post by coolclassic on 2009-10-30
Decided to reboot this then caused a problem with fstab and uuid.

I read somewhere to "sudo mount -o rw,remount /" in safe mode then "sudo update-grub" whether this is necessary I don't know.

then: sudo dpkg --configure -a


System fixed

---

