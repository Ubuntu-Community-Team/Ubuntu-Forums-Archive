---
title: "Problems in hotplug subsystem"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by mr_buntu on 2006-03-18
hello,

i am trying to install Ubuntu version 5.10 on an HP Pavillion PC.  Everything goes fine, installation completes, the grub completes, etc.  

When the system reboots to start in Linux mode, the system hangs right after it says "Starting hotplug subsystem."  The only option is to cut the power off, then re-start the pc. 

Does this mean I have an incompatible hardware component so I should just forget about Linux or is it a configuration setting that we can fix?

Thanks in advance for any help!

---

### Post by BJT on 2006-03-18
I have the same problem using the install or the live CD. ASUS P5RD1-VM mother board - 1 gig RAM - 80 Gig HD - ATI Radion Express 200 Series video on mother board.

I have also tried Dapper Flight 5 install which loads but the video resolution is messed up and cannot read any of the GIF.

---

### Post by al108 on 2006-03-18
> trying to install Ubuntu version 5.10 on an HP Pavillion PC. Everything goes fine, installation completes, the grub completes, etc.

>When the system reboots to start in Linux mode, the system hangs right after it says "Starting hotplug subsystem." The only option is to cut the power off, then re-start the pc.

Same thing happens when I do install on my Asus laptop, but I didn't investigate it.

>Does this mean I have an incompatible hardware component so I should just forget about Linux or is it a configuration setting that we can fix?

No, it's most probably some config. Ubuntu 5.04 works just fine on my laptop. Good luck.

---

### Post by jtp51 on 2006-03-19
mr_buntu: Did you ever solve this issue? I have a similar machine as well. I have a Logitech USB mouse and I just used a usb -> ps2 adapter until I found the real reason.

Thanks,

---

### Post by mr_buntu on 2006-03-19
Hello,

No, I have not resolved it yet.  It is funny; at boot up, if I don't select windows, it goes directly to Linux, but hangs at the hotplug subsystem.

Do I understand that you solved the issue by using a different mouse?  I also have a Logitech mouse that came with the PC, and it was using the USB->ps2 adapter.  I got a new mouse yesterday made by Microsoft.  I will try again.

---

### Post by al108 on 2006-03-19
I've instaled Dapper from a daly build CD of 19-Mar-06 didn't hang at the hotplug and everything seems to be working just fine. So you might want to try downloading a live CD and see if it works for you. It would be interesting to know how it works out for you. Let us know when you fix the problem.

---

### Post by ugarth on 2006-03-20
probably this might help you
[http://www.nabble.com/Re:-hangs-on-%22starting-hotplug-subsystem%22-p2300638.html](http://www.nabble.com/Re:-hangs-on-%22starting-hotplug-subsystem%22-p2300638.html)

---

### Post by al108 on 2006-03-21
That's sounds like a solution. The only problem I see is that I'd have to boot it fist or maybe use a CD to get access to the config files. Because it will not even load into a single user mode. I'm happy with Dapper on my laptop though. Video resolution seems to be fine too.

---

### Post by SteveHoffmanUK on 2006-03-22
Same problem here on a Dell Latitude laptop with Breezy -- hangs at 'Starting hotplug subsystem'. This is a re-install, and I didn't have this problem last time with this install disk. Have run Killdisk as well before the install to make sure it wasn't affected by previous installs.

Will try one more Killdisk, then Breezy install, then I think I'll wait for Dapper to be released, unless anyone else can suggest something?

---

