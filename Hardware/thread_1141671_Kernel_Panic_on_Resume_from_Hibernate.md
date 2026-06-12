---
title: "Kernel Panic on Resume from Hibernate"
date: 2009-04-28
forum: Hardware
---

### Post by greyfox1 on 2009-04-28
I'm having trouble resuming from hibernation on my IBM x40.  What will happen is the system freezes while showing the Ubuntu Logo and the progress bar with the message "Waking up, please wait".  The fact that the caps lock light begins to flash when the freeze occurs leads me to believe that this is a kernel panic.

I was waiting for Jaunty to land, hoping that the updates would take care of the problem.  Sadly that is not the case.

I had a look at [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume) and have included the info asked for in the "hibernate specific information" section.  That article advises to submit a bug report, but I thought I'd try here first.  I'd like to make sure it's not just my problem before I go filing a bug report.

dmesg: attached

proc/cmdline: ```
root=UUID=bf3ca28d-cc5c-4a2b-8d49-21335d6f06e5 ro quiet splash 
```

/etc/initramfs-tools/conf.d/resume: ```
RESUME=UUID=ef1f9b22-b064-4395-a0d9-a0bc21a7e765
```

(I checked and the resume UUID matches my swap UUID in fstab).

Additional info:

1.  This has been a problem since I first installed Ubuntu on this machine.  I have experienced the same problem in Hardy, Intrepid, and now Jaunty.

2.  Sometimes resume will work after a clean start-up.  It will then continue to work, provided I don't unplug the laptop.  If I start up on AC power and continue to use AC power, it works fine.  I'll get the lockup on resume if I start up on AC then switch to battery power.  It's very strange.

Help would be greatly appreciated!

---

### Post by greyfox1 on 2009-05-01
Nobody here has any ideas nor did the guys in #ubuntu on freenode, so I have filed bug #[370471]("https://bugs.launchpad.net/ubuntu/+bug/370471")

---

