---
title: "T60p no audio after suspend"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by gr83 on 2007-04-26
anyone else with a Lenovo T60p w/ Ubuntu 7.04 lose their audio after a suspend-to-disk?  reloading modules and reboots don't help, have to do a complete power down :( 

didn't have this issue in 6.10 and quick CentOS 5 tour before installing 7.04

---

### Post by ezaton on 2007-04-26
Check my post here:
[http://ubuntuforums.org/showthread.php?t=423734](http://ubuntuforums.org/showthread.php?t=423734)

Same problem with X41, however, in my case reboot doesn't help.

Hope it helps.

Ez

---

### Post by gr83 on 2007-04-27
> **ezaton said:**
> Check my post here:
[http://ubuntuforums.org/showthread.php?t=423734](http://ubuntuforums.org/showthread.php?t=423734)

Same problem with X41, however, in my case reboot doesn't help.

Hope it helps.

Ez

reboot didnt help in my case either.  anyway got suspend-to-memory working w/ sound.  so much for suspend-to-disk...

---

### Post by ezaton on 2007-04-27
I will try to combine them both, depending on the expected length of time the computer is to enjoy the compartment of my bag. If I can anticipate it to be short, I will use suspend-to-ram, and if not, I will use suspend-to-disk. In both cases, after suspend-to-ram, the system can play sound, so I could restore from hibernation, suspend-to-ram immediately, and then restore to fully functional level.

Far from being perfect. I wonder if it's BIOS or software issue...
I might open a bug about it.

Ez

---

