---
title: "Battery Problems"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by corvax on 2005-11-08
Hello i upgraded my wifes HP laptop  from 5.04 to 5.10 and now the battery seems to only last 30 to 45 minutes it used to last  an hour or longer but that was still far less than it lasted in xp. It is a ze4315us running an amd athlon. She uses it at schools and connects to the wireless there but says she cant get anything done because the battery life is horrid.  Any help is appreciated thanks. :)

---

### Post by 23meg on 2005-11-08
Is powernowd running? Type ```
ps aux |grep powernowd
``` and tell me the output. 

Also see if you have the packages laptop-mode and laptop-detect installed.

---

### Post by corvax on 2005-11-08
here's the output:
root      6954  0.0  0.2   1552   532 ?        SNs  21:06   0:00 /usr/sbin/powernowd -q
laptop1   9033  0.0  0.3   3064   760 pts/0    S+   23:01   0:00 grep powernowd

laptop-mode and laptop-detect are both installed

---

### Post by corvax on 2005-11-09
Is there a place to look for power management settings or somthing?

---

### Post by 23meg on 2005-11-10
Try manually starting laptop mode on startup and see if battery life improves at all. Here's how: ```
sudo laptop-mode start
```

---

### Post by towsonu2003 on 2005-12-18
Does not look that nice: ```
Caveats
-------

* The downside of laptop mode is that you have a chance of losing up
  to 10 minutes of work. If you cannot afford this, don't use it! It's
  wise to turn OFF laptop mode when you're almost out of battery --
  although this will make the battery run out faster, at least you'll
  lose less work when it actually runs out. I'm still looking for someone
  to submit instructions on how to turn off laptop mode when battery is low,
  e.g., using ACPI events. I don't have a laptop myself, so if you do and
  you care to contribute such instructions, please do.

* Most desktop hard drives have a very limited lifetime measured in spindown
  cycles, typically about 50.000 times (it's usually listed on the spec sheet).
  Check your drive's rating, and don't wear down your drive's lifetime if you
  don't need to.

* If you mount some of your ext3/reiserfs filesystems with the -n option, then
  the control script will not be able to remount them correctly. You must set
  DO_REMOUNTS=0 in the control script, otherwise it will remount them with the
  wrong options -- or it will fail because it cannot write to /etc/mtab.

* If you have your filesystems listed as type "auto" in fstab, like I did, then
  the control script will not recognize them as filesystems that need remounting.

* It has been reported that some versions of the mutt mail client use file access
  times to determine whether a folder contains new mail. If you use mutt and
  experience this, you must disable the noatime remounting in the control script
  by setting DO_REMOUNT_NOATIME=0.
```

---

