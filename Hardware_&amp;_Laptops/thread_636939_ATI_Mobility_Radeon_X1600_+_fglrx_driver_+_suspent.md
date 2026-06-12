---
title: "ATI Mobility Radeon X1600 + fglrx driver + suspent to RAM"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by DoDoENT on 2007-12-10
Hello everyone!

I have installed Kubuntu Gutsy gibbon 7.10 on my HP nx9420 (uses ATI Mobility Radeon X1600). I've also installed the newest ATI propriety driver from ATI's website, and got compiz fusion working almost perfectly (with little issues while playing videos or playing some 3D games). But suspend to RAM does not work. If I choose Suspend to RAM option in KPowersave, my laptop will go to stand-by mode, but monitor will stay turned on, along with the graphic card.

Prior Kubuntu, I used to have openSuSe 10.3 on the same machine, using the same ATI drivers (but compiz fusion didn't work - this could be issue with openSuSe's Sax2 and fglrx's poor AIGLX support). My point is that I was able to suspend the laptop to RAM correctly even while using the newest fglrx driver. Actually, openSuSe uses s2ram program for suspending the computer to RAM, and this program has option "--force --radeontool" which successfully handles with ati graphic cards.

Since I've noticed that Kubuntu does not use this program for suspending to RAM, I would like to ask experts or Kubuntu developers: Which program does Kubuntu use for suspending to RAM? Does this program have such a feature (as s2ram does)? If it doesn't, is it possible to install s2ram on Kubuntu and configure Kpowersave to use it while suspending to RAM (as it is possible in openSuSe 10.3)?

Thank you very much in advance!

P,S. I've switched to Kubuntu only because of the apt-get command <-- excellent feature!

---

### Post by disembodied on 2007-12-10
you can use the same program for suspend that openSUSE uses.

sudo apt-get install uswsusp

sudo s2ram
[that will test to see if it works]
and you can use your extra commands (--force, etc.) as necessary.

check out:
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

for a thread on the issue and more detailed directions. (including how to make your buttons use this command instead of the default one)

---

### Post by DoDoENT on 2007-12-10
Thank you very much, but...

dodo@2nd-of-12:~$ sudo apt-get install uswsusp
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  splashy
The following NEW packages will be installed:
  uswsusp
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/146kB of archives.
After unpacking 455kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package uswsusp.
(Reading database ... 110770 files and directories currently installed.)
Unpacking uswsusp (from .../uswsusp_0.6~cvs20070618-1ubuntu2_amd64.deb) ...
Setting up uswsusp (0.6~cvs20070618-1ubuntu2) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic

dodo@2nd-of-12:~$ sudo s2ram
sudo: s2ram: command not found

How would you comment this?:confused:

---

### Post by scubasteve657 on 2008-02-20
I'm working on a similar problem with a Radeon card.  The ubuntu build of uswsusp sucks, have a look at this post:
[http://ubuntuforums.org/showthread.php?t=697659](http://ubuntuforums.org/showthread.php?t=697659)

---

### Post by DoDoENT on 2008-02-21
Thanks, I've tried it, but it doesn't work. In the meanwhile I've found out what is the problem - it's in the fglrx driver. Suspend works only if compiz desktop effects are disabled (and were not enabled in the current session at all). I reported the problem on the phoronix forums, where people from ATI give support.

---

### Post by scubasteve657 on 2008-02-26
Yeah, I came to the same conclusion.  Turns out the problem is with "slub".  The fiesty kernel was compilled with "slab", but the gutsy kernel uses "slub" and breaks fglrx suspend suport.

[This]("http://blog.vaxius.net/?p=19") page claims to fix the problem, but I haven't been able to do it.  Maybe you'll have better luck then I did.

---

### Post by DoDoENT on 2008-02-27
Since fglrx 7.12 release, SLUB has been supported, but suspend works only if compiz effects are off. Check [this thread]("http://www.phoronix.com/forums/showthread.php?t=7557").

---

