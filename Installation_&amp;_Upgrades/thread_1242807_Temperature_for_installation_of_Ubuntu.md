---
title: "Temperature for installation of Ubuntu"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by zenlunatics on 2009-08-17
I recently tried to install ubuntu, as well as xubuntu on my aunt's computer. 

I managed to delete windows, but ubuntu doesn't fully install I get the message:

The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

I've ruled out the cd being the problem, and Im going to try a usb install to rule out a cd/dvd reader problem. It is really hot right now, maybe 90 degrees, would this be enough to make the installation fail?

---

### Post by presence1960 on 2009-08-17
[http://ubuntuforums.org/showthread.php?t=1207755&page=2](http://ubuntuforums.org/showthread.php?t=1207755&page=2)

see post #20

---

### Post by zenlunatics on 2009-08-17
I just followed the advice, and could not get the command to work I get the message " command not found" .

---

### Post by presence1960 on 2009-08-17
```
ubiquity --no-migration-assistant
```

My bad, I forgot they spelled ubiquity incorrectly.

If that does not work try ```
sudo ubiquity --no-migration-assistant
```

---

### Post by zenlunatics on 2009-08-17
Oops, I scewed up too. That error message I pasted from the internet I thought it was the error I'm getting but it actually isn't. Here it is:

The following file did not match its source copy on the CD/DVD:

/target/lib/modules/2.6.28-11-generic/kernel/drivers/media/dvb/ttusb-budget/dvb-ttusb-budget.ko

This is often due to a faulty CD/DVd disk or drive, or a faulty  hard disk. It may help to clean... 
( the rest is the same message as before)

Thank you for any assistance

---

