---
title: "Laptop reboots instead of shutdown"
date: 2011-03-22
forum: Hardware
---

### Post by hookdump on 2011-03-22
So, 1 week ago I bought an Asus EEE PC 1215p. The first days everything worked perfectly.

[COLOR="Red"]But then, -I THINK after doing **echo "mem" > /sys/power/state**, the problems started.

When I power off the machine (touching the power button or with ubuntu menu), it powers on automatically after 1 or 2 seconds.[/COLOR]

If I hold the button pressed for 5 or more seconds, it powers on immediately after I release it.

So, this happens with any operating system (Win7, and Backtrack4 from a USB drive). 
**BUT I think it's a Linux problem, since the problem started with this "suspend to ram" command.**

It's like the computer has stored somewhere "Hey, as soon as you power off, wake up".


I'll copypaste the info I put on EEE forums:
[http://forum.eeeuser.com/viewtopic.php?id=93043](http://forum.eeeuser.com/viewtopic.php?id=93043)

> I'll tell you everything I've already tried:
- I tried pressing the Power Off button, also holding it for 5-10 seconds, using Ubuntu menu, or doing "sudo shutdown -P now". No Luck.
- So I thought "Okay, I broke Ubuntu". I tried with Windows... and the same thing happens.
- I also tried botting "Linux Backtrack 4 R2" from a USB Drive... and the same thing happens.
- I googled A LOT, but find almost no one with this exact problem.
- I logged into Win7, disabled "Restart on system failure".  No Luck.
- I tried doing a dry reboot (unplug AC, unplug battery, and hold Power button for 60 seconds). No Luck.
So, nothing works. I did a System Recovery...
It put Win7 to factory state... so when I booted it, it was just like the 1st time I used the machine. It installed Windows, etc.
I tried every option of recovery / repair / etc. offered by the system, and now Windows will not boot at all.
It shows a blue screen of error while loading.
So.... Things I would do, but I'm afraid that would break the warranty.
- I would format the entire HD, and install ubuntu.
- I would try upgrading the BIOS somehow.
- I would open the case and find any switch or jumper to clear the CMOS.


Anyone has any ideas before I send it to the warranty support?

What could cause the laptop to power on itself after 2 seconds it's powered off? regardless of which OS shuted it down.

---

### Post by jalmargyyk on 2011-10-27
Sorry to reply to an old post.

I'm experiencing exactly the same problems with Asus EB1501P. I have tried multiple different Operating Systems (Puppy, Kubuntu 11.10, Ubuntu 11.04) booted from USB Live and every single one of them has had the same symptoms.

Here's what I have tested:
- Clear BIOS to factory default.
- Upgrade BIOS.
- Deactivate ACPI 2.0 from BIOS.
- Deactivate Wake On Lan
- Deactivate SATA Drive (so there's only the Live USB)

I think the problems started, when I was trying to get xbmc (openelec) suspend to work with remote. 

Any ideas are welcome.

---

### Post by jalmargyyk on 2011-10-27
Ok, I figured this out. I cleared the CMOS by detaching power adapter and pressing power button for one minute. After that the box didn't restart after shutdown.

---

