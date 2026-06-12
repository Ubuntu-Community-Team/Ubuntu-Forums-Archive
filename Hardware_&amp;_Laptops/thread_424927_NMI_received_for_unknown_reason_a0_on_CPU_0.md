---
title: "NMI received for unknown reason a0 on CPU 0"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by hamvil on 2007-04-27
Hi,

After some hours of work I get the following message:

Message from syslogd@Alba at Fri Apr 27 11:28:41 2007 ...
Alba kernel: [ 7887.748000] Uhhuh. NMI received for unknown reason a0 on CPU 0.
Message from syslogd@Alba at Fri Apr 27 11:28:41 2007 ...
Alba kernel: [ 7887.748000] You have some hardware problem, likely on the PCI bus.
Message from syslogd@Alba at Fri Apr 27 11:28:41 2007 ...
Alba kernel: [ 7887.748000] Dazed and confused, but trying to continue

Then the whole system become very slow. 

I'm running Festy on a dell D610 notebook with ati x300 card. I've also noticed that the notebook is very hot. However the fan works properly (i can clearly hear it). I've also tried to use i8k to force the fan to run at the higher speed but i'm still getting the message (and the system slowdown).

Thanks

---

### Post by mertle on 2007-05-04
I have the same error message that pops up -right- before the Kubuntu splash screen starts up while booting. I'm running Kubuntu Feisty (upgrade, not full install) on a Dell i9300. I highly doubt I have a hardware problem, as Edgy was working fine with no messages for quite some time.

I've seen this issue posted a few times, but with no possible explanations or replies- sorry for adding to those without an answer. :/

- mertle

---

### Post by underwater on 2007-07-12
I have received a very similar error(nearly identical except for what it received I beleive) while running Kubuntu 7.04

I strongly believe this to be a software bug that happens with dell laptops.  In the ubuntu chat room on freenode I also ran into someone with the same problem on a Dell Inspiron 6000 (which is the same as my laptop) while they were running xubuntu.


I would go about submitting a bug report and such, but I"m not sure how exactly...

---

### Post by dying_sphynx on 2008-03-13
Hi!

I'm getting the same problem on my Inspiron 6000 running Ubuntu. Here is part of log:

[  683.140000] Uhhuh. NMI received for unknown reason a0 on CPU 0.
[  683.140000] You have some hardware problem, likely on the PCI bus.
[  683.140000] Dazed and confused, but trying to continue
[  732.428000] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks
[  732.664000] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks

Computer just freezes (frequently while running some compiz effects), but mouse can still work. Also I was able to connect to openssh from another box, so my wi-fi adapter works good too.But Ctrl-Alt-Backspace, Ctrl-Alt-F1 do not work. 

Under windows I'm not experiencing any hardware problems, so it seems to be software bug.

---

