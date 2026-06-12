---
title: "USB KVM Switch causing X to crash with 2.6.27-11 Kernel"
date: 2009-01-30
forum: Hardware
---

### Post by paul@cyberengel.com on 2009-01-30
So this morning I installed the updates with the 2.6.27-11 kernel on my Lenovo T60 and this odd thing started happening...

I have a IOGear USB KVM switch that I use to switch between my T60 and a desktop system running Windows XP.  After the update, when I switch away from the T60 then back X crashes, (returns to the login prompt).  Not 100% of the time, but almost always.  I'm looking for some info as to what might be going on.

---

### Post by AKADAP on 2009-01-30
What model of IOGear KVM are you using.
I'm using the GCS1204 (DVI). I haven't done a lot of switching since the new kernel came out, so it hasn't crashed yet.
When I previously was using my monitor to switch (displayport), Ubuntu would shut off the display so it could not be turned back on if I switched away for too long. I think the GCS1204 fixed this because it pretends to be the monitor when you have switched the monitor to a different input.

---

### Post by paul@cyberengel.com on 2009-01-31
I've got the 2-port Miniview switch.

It's not that the display blanks, X seems to crash/reset and I'm brought back to the login prompt, (like pressing Ctrl+Alt+Backsapce).  Also, I have a dedicated monitor attached to the laptop, so it's only the USB that's being switched.  And it only happens when I switch back to my laptop, switching away doesn't seem to be a problem, so my guess is something with the USB keyboard & mouse is where the problem is.

---

### Post by Jack Brooks on 2009-02-11
I am experiencing this exact same issue.  Did anyone ever find a fix?

---

### Post by Zenguy on 2009-02-16
I'm seeing this same thing with a Starview KVM switch.

Sometimes I lose the mouse, sometimes the keyboard is lost, other times my Ubuntu system just resets to the login screen (losing all my work in the process). I can usually restore the lost keyboard/mouse by toggling the KVM switch a few times.

This appears to be a new bug with the 2.6.27.11 kernel. Everything was rock solid for me before the last kernel update. When I boot with the 2.6.27.9 kernel, everything appears to work normally.

I don't think there is a bug logged on this yet.

---

### Post by paul@cyberengel.com on 2009-02-17
I'm guessing the problem is with USB... yesterday I was plugging in a USB presentation mouse and guess what?  Yep, X crashed and I had to restart.

---

### Post by Zenguy on 2009-02-17
Yes, I would confirm the USB theory. My KVM switch only does USB for the mouse, keyboard and printer.

Anyone know how to log a kernel bug on this?

---

### Post by Zenguy on 2009-02-17
I just reproduced this bug while running the 2.6.27-9 kernel, it might be something other than just the kernel version.

---

### Post by paul@cyberengel.com on 2009-02-18
Zenguy, by chance are you running the server kernel?

I had seen it with 2.6.27-9 when I had recompiled it with PAE... thought it was something I had done since I didn't see it happen with an unmodified kernel.

---

### Post by Zenguy on 2009-02-18
No, I'm running a stock install of Intrepid Desktop 386. It's current with all updates.

---

### Post by nox216 on 2009-03-03
Same behavior, and it seems like it's been happening for a few kernel revisions. Definitely happening on 2.6.27-11 generic install, though.

---

### Post by redhorse on 2009-03-09
I've had the same problem since I updated to 8.10 (64-bit desktop).  X crashes about 3 out of 4 times when I switch _to_ my Ubuntu box using a Bi-System DVI/USB KVM switch.  The same switch worked flawlessly with Ubuntu from 7.04 (when I first used it) through 8.04.

---

### Post by Drdon on 2011-08-30
Since upgrading to 11.4 my 64 bit system routinely crashes on start up but so far will start at second attempt. I believe it is sensitive to USB mouse being touched. It will immediately crash if I plug in a camera on a USB lead and I discovered today it will not start up with an external USB hard drive connected but will tolerate the drive for a short period if plugged in after login . It is happy with a Samsung USB printer and also a USB Flash Card Reader. Before upgrading from Ububtu 10 is was a very stable system and I have not changed anything. Something very odd is going on!

---

