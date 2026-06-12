---
title: "Crashing"
date: 2008-07-26
forum: General Help
---

### Post by melenor on 2008-07-26
My installation of ubuntu 8.04 seems to crash every so often, sometimes, i can go a month without a crash, other times, i have 4 a day. I have tried reinstalling, i did this twice, My system is

ubuntu 8.04.1 64-bit
ATI X1800
Athlon X2 3000+
nforce 4
Audigy 1 ES
750GB-Data
250GB-Ubuntu
Logitech MX610
Belkin Wireless G USB Network Adapter F5D7050

several people i know have looked at it, and seem to think that the cause might be the Belkin adaptor or the Logitech MX610, I am wondering how i can find the exact cause of my crash, and how i could go about fixing it.
Also a side note, when ever it crashes the Caps Lock on my keyboard blinks.__

---

### Post by ryanhaigh on 2008-07-27
I would try running memtest from the livecd to check whether your ram may be defective. The caps lock key thing is a little weird though.

---

### Post by perlluver on 2008-07-27
When I have a kernel panic, my caps lock and number lock key flash.  So it sounds like a kernel panic.  Most likely is a hardware issue.

Come to think of it, when I tried to put a Belkin card in the computer, I didn't get past the kernel panic.

---

### Post by melenor on 2008-07-28
i tried memtest and checked all hard drives and checked the ATI card the only thing that me and my friends could narrow it down to were either the Belkin or the logitech. If it is the Belkin is there any way to fix this?

---

### Post by melenor on 2008-07-28
I am pretty sure that it is the Belkin Wireless Adaptor does anyone know of a way to make sure i don't have anymore random crashes?

---

### Post by melenor on 2008-07-30
Anyone help would be very useful. Please?

---

### Post by ryanhaigh on 2008-07-30
I guess you could look at replacing the driver with a more recent version or maybe using ndiswrapper but the obvious solution is to replace the wireless adaptor in favour of something better supported. Unfortunately you might do this and find out its not the issue (the times between crashes being so long makes diagnosing difficult).

---

### Post by melenor on 2008-07-30
well, most of the time when i shut down (I just noticed this because i forgot to turn off the screen first) is that the logo, goes away leaving just text saying something about the network something, next time i shut down i am going to copy it. and i will post it here. Anyone know of any good WiFi Adaptors (peferably PCI) that are compatibly with ubuntu?

---

### Post by poet_imp on 2008-08-18
I too am experiencing the system halting with the caps lock flashing. Only a power off/on rectifies the situation. 

I found this old thread: 

[http://www.backports.ubuntuforums.org/showthread.php?t=421542](http://www.backports.ubuntuforums.org/showthread.php?t=421542)

that describes my problem fairly closely. is this the same thing you all are seeing?

---

