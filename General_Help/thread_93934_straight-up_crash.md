---
title: "straight-up crash"
date: 2005-11-23
forum: General Help
---

### Post by dmwit on 2005-11-23
I have what I consider to be a pretty serious problem: my computer crashes every 48-96 hours.  Most of the time, it occurs while I am away from the computer.  I have only witnessed the process once.  Here is what happens:

* CPU usage shoots up to 100% for about a tenth of a second (and may stay there during the crash)
* Keyboard input is ignored, including Ctrl-Alt-Backspace, Ctrl-Alt-F1, etc.
* Mouse input is accepted; the mouse moves around the screen
* Nothing else happens; I can't change which program has focus, close programs, switch desktops, anything
* Of course, if this happens during the screen saver, I can't end that either

I have no idea how to find out what is going wrong, since it is kind of rare and the warning signs are so close to the problem.  I've had to hard reboot my computer four times in the last week...

How can I find out what is happening and how to fix it?
~d

---

### Post by 23meg on 2005-11-23
Take a look at your system logs for suspicious activity just before the crash time. Applications / System Tools / System Log.

Please give more info on your hardware and kernel version.

---

### Post by dmwit on 2005-11-23
Ah, that log is a nice resource, thanks!  I guess a couple hundred attempts to log in via ssh from the same IP address qualifies as suspicious, huh?  Still, I thought ssh was supposed to be pretty well secured, right?  I'm using mostly the default settings; are there any I should change?

I've set Firestarter to allow ssh only from the local network; hopefully that will help.

> more info on your hardware and kernel version
Okay:
Dell Inspiron 5150, Pentium IV (2.8 GHz, Hyperthreading available), 512 MB RAM, using the package linux-image-2.6.10-5-686.  Nothing else that's all that special, except an NVidia 5200 graphics card.

Thanks!
~d

---

### Post by dmwit on 2005-12-03
Well...

I thought it was fixed, but I've just had another crash.  This time, no messages in the system log.  Any other ideas of how I can investigate?

~d

---

