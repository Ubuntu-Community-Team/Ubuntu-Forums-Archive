---
title: "Hard lock ups in fresh intrepid install"
date: 2008-11-01
forum: General Help
---

### Post by Afkpuz on 2008-11-01
Hey guys, I've been using ubuntu since dapper and just upgraded to intrepid. Intrepid has been giving me problems I've never encountered before.   I've been getting hard lockups at seemingly random times.  Once when I was installing a .deb package, another time when suring via firefox.  I can still move the mouse, but nothing else works including alt+f4 and ctrl+alt+backspace.  Any ideas?  Anyone else having this problem?

---

### Post by userundefine on 2008-11-02
Yes, I am also having this problem.  Check your kernel log at /var/log/kern.log and see if there are errors at the time when the lockup occurs.  For me, every time this has happened (at least 6 times since I installed Intrepid two days ago), these lines always appear in the kernel log:

```
Nov  2 19:16:24 nomadsland kernel: [  598.734960] Uhhuh. NMI received for unknown reason b1 
on CPU 0.
Nov  2 19:16:24 nomadsland kernel: [  598.734970] You have some hardware problem, likely on 
the PCI bus.
Nov  2 19:16:24 nomadsland kernel: [  598.734973] Dazed and confused, but trying to continue
```

When this locks up (can be any time, while browsing something in Firefox or mounting a hard drive), I can still move my mouse but I cannot use the keyboard, and any clicks do not register.  I can't even change to a TTY to kill X, and I'm forced to press the power button and shut down manually.  There's nothing special about my setup.  I'm using an Inspiron 6000 with wifi on the intel 2200 card.  I'm using standard Compiz as installed by default by Intrepid install (a fresh Intrepid install of the final version, not an upgrade), and AWN from the official repos.  I've never experienced this before with Hardy or Gutsy or older.

This may be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/116752").  I'm reading more about it now to see yes or no.

---

### Post by userundefine on 2008-11-02
I've opened [a new bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292751") for this.

---

### Post by Bil-E-daKid on 2008-11-08
Hey guys,

I, too, have been having actual hard locks with Intrepid since installing fresh a couple of days ago.  When I say 'actual', I mean, actual hard lock, no mouse movement, video output stops (screen goes to sleep), keyboard lights don't work etc.

Only way out is press and hold power button or press reset.  System starts normally and then runs fine.  Seems quite random - one time, no one was even logged in, system was waiting at GDM screen.

Historically, have not had any issues like this with Ubuntu on this system - has been running 8.04 since release without issue (and back to original 4.10 release).  

What sort of thing should I be looking for, in which /var/log file do you think?

Thanks in advance

---

### Post by Afkpuz on 2008-11-08
reinstall fixed it for me

---

### Post by Bil-E-daKid on 2008-11-08
Thanks Afkpuz, I shall give that a try and see if it makes a difference.  I'd like to know why, but at this stage, I also need to stop this having to switch the machine off and on every day.

---

### Post by Bil-E-daKid on 2008-11-14
Wow - who would have thought.

I did the reinstall - still had the problem.  I removed the nvidia driver on the off chance it was that - still the same problem.

Then, I managed to pin it down to happening at a certain time, in line with some cron jobs.  Turns out, it's this command that is now freezing up my machine:

tar --bzip2 -cvf /mnt/backup/systembackup.tar.bz2 --exclude="/proc/*" \
    --exclude="/lost+found/*" --exclude="/dev/*" --exclude="/home/*" \
    --exclude="/mnt/*" --exclude="/media/*" --exclude="/sys/*" \
    --exclude="/tmp/*" --exclude="/var/*" / >/home/user/tmp/sysbackup.log

The funny thing is, this same command runs on my Hardy box at work, which is now locking up each night when it does this as well.

Is there perhaps some new part of the filesystem (that isn't being excluded in the above list) that could cause a full hard lock?  

I never would have imagined a tar command bringing the whole system down.

Any ideas?

---

