---
title: "Portable SSD?"
date: 2016-03-10
forum: Hardware
---

### Post by jim_deadlock on 2016-03-10
My day-to-day desktop computer runs 15.10 + Nvidia graphics (nouveau driver) on a SSD. I've just bought a USB adapter for the SSD and it boots/runs via USB on my desktop PC no problem. So I took it over to my friend's house and plugged it into his laptop (which has Intel 965 GPU) and tried booting it but it won't load the DE (shows low-graphics mode dialogs for which I've tried all the various options). I can get to GRUB and recovery mode and I've tried various things like purging nvidia drivers, booting with nomodeset etc without success. I know that the laptop is capable of running Ubuntu because that's what it normally runs on its own SSD.

My question is, before I continue on my quest to boot my SSD from various different computers, will it be necessary to mess around with configurations every time I plug it into a different computer (in which case I'm not going to bother), or is there a way around it like installing a generic driver or having it choose the driver at boot time, so that I can just plug it in anywhere?

---

### Post by weatherman2 on 2016-03-10
I'd guess if you uninstall the Nvidia driver, it will boot on other computers without this problem.

---

### Post by jim_deadlock on 2016-03-10
Well I did try that (below) and rebooted but it made no difference, I still kept getting the low-graphics dialogs

```
apt-get purge nvidia*
```

---

### Post by weatherman2 on 2016-03-10
Then I'm not sure what to tell you.  I routinely boot different hard drives on different computers, often in exactly the same way you are trying to do with a USB adapter.  However, I usually don't install custom graphics drivers.

---

### Post by mc4man on 2016-03-10
do you know if this Intel 965 machine can run 15.10? Maybe bring over a 15.10 live usb & see what happens, ie. can it run a live session ok.

---

### Post by jim_deadlock on 2016-03-10
OK thanks, it helps to know that it's possible in theory :)

---

### Post by jim_deadlock on 2016-03-10
@mc4man Yes it runs 15.10 normally from its built-in SSD so it's not a hardware problem. I'm pretty sure it's related to the graphics driver.

---

### Post by mc4man on 2016-03-10
While I don't know firsthand it seems a 965 is a bit old, quite possible it can't support Ubuntu (unity) graphic requirements, if it doesn't then Xubuntu or Lubuntu may be ok

---

### Post by jim_deadlock on 2016-03-10
It is fairly old but it has Unity and Gnome Shell installed on its own SSD and runs both without any problems.

---

### Post by sudodus on 2016-03-11
Does your friend's computer need a proprietary driver for the graphics (another driver than what you use in your own computer)?

Does it work with a live session booted from a USB pendrive (not installed like yours, only a flashed system for installation)? An alternative for a portable system is a ***persistent live*** system. The live system has a few extra graphics drivers and wifi drivers, that makes it easier to run with various hardware compared to an installed system.

But as has already been said in this thread, often an installed system in a USB drive is portable enough. It works in many different computers as long as you avoid proprietary drivers. Maybe the problem in your case is that something is left from your proprietary nvidia driver system or from a proprietary wifi system, and it is creating problems in your friend's computer.

Maybe you get some idea from the following link or links from it:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by jim_deadlock on 2016-03-11
Yes the laptop does work with a live session and it doesn't have any proprietary drivers - I know these things because I installed his system for him. My SSD doesn't have any wifi drivers on it because it normally has a wired connection. As you say, I think it probably has leftover driver configurations somewhere, so I think what I'll do is try reinstalling the system from scratch and see if that works. Thanks everyone for your feedback.

---

