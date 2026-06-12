---
title: "My laptop doesn't power off"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by sylvaticus on 2007-03-01
hello.. I installed my first xubuntu on a old laptop, hovewer it doesn't automatically power off when asked so (it require to manually switch it off).
Previously it was installed a Mandrake Linux that was doing that, so I presume there must be a trick to force the laptop to switch itself off automatically... 

..any suggestion??? thanks... /Sylvaticus

---

### Post by radiocognition on 2008-02-23
I am experiencing the exact same problem.  Help on this would be nice

---

### Post by kevmitch on 2008-02-24
There are probably a million different ways to achieve this. There may be something within gnome/kde power manager, but I'm not too familiar with those and really don't think that you should have your desktop environment controlling such low level things anyway. On my laptop, I use sleepd. You can install it with
aptitude install sleepd
Essentially, this program watches for mouse or keyboard usage and when it decides that the laptop has been inactive for a configurable amount of time, it executes a command. This is really handy, because it can be any command you want, but if its a complete poweroff you want, you'll probably want it to execute /sbin/poweroff.

Here is a howto for configuring it: 
[http://www.thinkwiki.org/wiki/Installing_Debian_Lenny_on_a_ThinkPad_T60#automated_sleep](http://www.thinkwiki.org/wiki/Installing_Debian_Lenny_on_a_ThinkPad_T60#automated_sleep)

---

