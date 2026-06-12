---
title: "Shutdown not working"
date: 2009-11-07
forum: Hardware
---

### Post by Ganymedes on 2009-11-07
I have a problem with one workstation, about 6 years old with AMD 64-bit processor, sorry I do not have all the details right now (because I am helping a friend). Anyway, it is a custom built workstation.

The thing is that when I do shutdown, it just stops waiting for processes to terminate. You can actually, while it waits, press alt-control-F1 and it will display the terminal window - if that better explains where it stops (however, you cannot logn in).

So, in the end I always need to shut it down by powering the computer down.

The next boot-up takes quite long, about 2 minutes extra waiting at several stages. It might be because it does not shutdown correctly (however, I do not see any file checking going on for extended  time).

Are there any generic reasons for this and what should I try to do? I already turned off all the power management from BIOS, but that did not help. The computer does not have any special hardware (as far as I know) that would cause these kinds of symptoms.

The computer is just now installed first to 9.04 and then immediately upgraded to 9.10. It is a 64-bit system. As far as I observed it did the same thing with 9.04. With its former OS, Windows XP, it did not have this problem.

---

### Post by Ganymedes on 2009-11-08
Up.

I want to add a related or non-related question, I do not know which, is it normal that boot up with 9.10 takes much longer (perhaps 3-5 minutes longer) compared to anything that I have seen on various other hardware ... I have used Ubuntu since 7.10?

---

### Post by Ganymedes on 2009-11-14
In case somebody is interested, I got this more or less resolved.

I was originally thinking that the slow boot-up time was because of shut down not working. It was not.

The very slow boot time, was due to 2 BIOS settings. They were PCI and PCI_E enabled for wake-up (or something similar). I disabled them and it started to boot up normally. I do not think a motherboard of that age even has PCI-E. Anyway, those settings did not matter when using Windows XP.

The problem of the OS not shutting down, does not seem to matter. It does not do any disk checking in booting up and the boot up does not take a long time. So, I guess it shuts down enough after all.

The last messages on screen are about intel-hda - so perhaps trying with a sound card, instead of using the motherboard sound chip, might correct this problem. However, since this is not up to me, this will probably be left as not investigated.

---

