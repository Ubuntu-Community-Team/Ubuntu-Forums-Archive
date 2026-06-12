---
title: "Unpredictable system freeze"
date: 2012-07-15
forum: Hardware
---

### Post by Kristof A on 2012-07-15
Hi all,

Since I installed Linux on my laptop (Dell e6410, first Ubuntu 10.04 LTS, now Xubuntu 12.04 LTS) I have had unpredictable system freezes.  

It happens while working on the laptop and suddenly everything freezes: mouse does not move anymore, screen does not update, Ctrl+Alt+F1/F2... to go to terminal does not work anymore, closing laptop lid does not make system go in suspend,...  only remedy is holding power button to shut down laptop and restart it.  Once I also tried to ssh into the box from another machine and that also did not work. There is also nothing in syslog, kernel.log etc that indicates freeze as far as I can see.

Sometimes this happens twice a day, sometimes once every 5 days but it always comes back. I'm using my laptop about 8 hours a day during weekdays for more than 1 year already. I keep it up to date with the provided LTS updates but this issue keeps on being there.  I like the speed and usability of my system but It is just annoying not to be able to trust the stability of my machine.   (I had suspend/hibernate/resume issues before but those are solved now)

I do not seem to be the only one who has this issue. See [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187"), [here]("https://bugs.archlinux.org/task/29276") and [here]("http://partiallysanedeveloper.blogspot.be/2012/05/ivy-bridge-hd4000-linux-freeze.html").

In some of those pages the solution seems to be upgrading to kernel 3.3.x (3.3.6 or higher) which improves support for the I5/I7 processors.  Before I try this, and go away from the kernel that is supported by the LTS release, I would like to know if there is a clear description somewhere (fixed bug, changelog) that indicates that the problem is solved and in which kernel or whatever component version.

Hope somebody can help. Thanks!

---

