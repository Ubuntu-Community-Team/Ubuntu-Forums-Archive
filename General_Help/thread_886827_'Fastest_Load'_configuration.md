---
title: "'Fastest Load' configuration?"
date: 2008-08-11
forum: General Help
---

### Post by atyar on 2008-08-11
I recently installed Ubuntu on our xp pc at home, via a 2nd hard drive I had already there for backups from XP.

I'd like to try to convince my wife to use Linux vs. XP for day-to-day stuff (emailing, Openoffice stuff (which we already use in XP), web surfing....) which is about 95% of what she uses the computer for anyway.  Remember the days of MS-Dos computers (before the advent of Windows), when your computer would boot up and down nice'n'quick?  I'm thinking I could sell my wife on learning her way through Linux if I could significantly improve on the speed of the computer vs. XP (running a decent machine (Athlon64 3500+, 3.5GB(4 really) PC3200 dual channel, 250GB Sata drive...), but I think the speed at which XP goes up and down, plus multitasking is lame compared to my dual-core pc at work (which also runs XP).  I want to wait to build a new 'puter, since I'm cash strapped, hence I'm looking at Linux.

So far, it seems a bit faster, but not superbly so.  What can I do to compete with those old dos box load times and shutdown,etc.? :)  Thanks!

---

### Post by logos34 on 2008-08-12
Try these links:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://lightningcrash.blogspot.com/2007/08/making-ubuntu-boot-in-19-seconds.html](http://lightningcrash.blogspot.com/2007/08/making-ubuntu-boot-in-19-seconds.html)
[http://lifehacker.com/software/linux-tip/speed-up-ubuntu-boot-and-shutdown-process-267588.php](http://lifehacker.com/software/linux-tip/speed-up-ubuntu-boot-and-shutdown-process-267588.php)

The first might seem a bit old, but much of it is still relevant.  Basically you want to get sysv-rc-conf and go through and turn off anything you don't use (i.e. stuff like Britty, Bluetooth, apm, laptop-related stuff, cups if you don't need printer server service, etc.).  Double check 

system>admin>services
system>preferences>sessions

and maybe install **bum** (bootup-mananger)

Check your Bios too: disable stuff like parallel and serial ports if you don't have any of those type peripherals (everything is usb now), floppy drive seek (who except me still uses one?), RAID, etc.

hope that helps

---

### Post by sub2007 on 2008-08-12
To achieve the best boot time I would go with a minimal distro like Arch or Gentoo. I would then choose Xfce or for the ultimate speed I would use a Window Manager (like Fluxbox, Openbox etc) which would probably achieve everything you would and be very light. On Arch I can boot to Xfce in around 30 seconds, with Compiz Fusion and AWN it takes around 50 seconds. With more tweaking it's possible to get that down even more (and my hardware doesn't exactly fly so 50 seconds for boot is good for me). Shutdown time for me is around 10 seconds. In comparison, with speed tweaking (using readahead and disabling uneeded services) my Xubuntu boot times are around 90 seconds - 2 minutes.

So I'd definitely consider doing that. It's much harder to set up but it's so worth it in the end.

---

### Post by logos34 on 2008-08-12
sub2007,

just curious, have you heard anything about[ initNG]("http://www.initng.org/")?  My boot time is fast enough as it is, but I was considering testing it out.  But I don;t want to screw anything up...

---

