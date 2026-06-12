---
title: "Brown screen booting syndrome"
date: 2011-01-20
forum: Hardware
---

### Post by Alcareru on 2011-01-20
Hi all

I have recently experienced some very weird behaviour. I've had/am having trouble with internet getting up and running (see my other thread) and another issue I call "brown screen booting syndrome". Once I get the computer properly on I have no problems. I can reboot, I can turn off the screen, I can let the screensaver kick in. However, if the computer is idle (screen off) or completely shut down for a long period of time. It's hard to say how long exactly, but shutting down and waiting for 10 seconds and booting seems to not be long enough.

Anyhow when the screen has been off for long enough time and I put it on it is totally light brown. Like milk coffee brown or perhaps beige. However, otherwise the computer works normally, I can log in (blind folded) and do what ever I want as long as it doesn't require me to see anything. And the weirdest thing is that the screen is brown right from the start. When I'm powering on the computer at the morning, the first thing I will see on the screen is light brown. At no point it is black, or shows anything else (like press f2 to get bios for instance).

At first I thought that perhaps it's a hardware failure or driver failure. However this seems to not be the case. I have tried the onboard integrated intel graphics card as well as my nvidia graphics card with and without the proprietary drivers. Also the issue eventually always wears off. When I've been more or less "randomly doing stuff" with the computer for a while and periodically powering on and off the screen it will at some point start working.

This issue might or might not relate to this _[networking issue](http://ubuntuforums.org/showthread.php?t=1632973)_ I'm experiencing. Though, that issue has only been bugging me with 64-bit installation. This brown screen issue however has been troubling me with 32 bits as well as 64 bits. In case it might matter I've been booting off from a software raid partition in all cases (that meaning, I've used the alternate installation cds).

---

### Post by Alcareru on 2011-01-20
Updating bios didn't help. Anybody having some other ideas? Help? It's really killing me that getting the computer working if I let the screen rest a bit takes like tens of minutes of work.

---

### Post by Alcareru on 2011-01-20
BIOS update didn't help. Anybody having some other ideas? Help? It's really killing me that getting the computer working if I let the screen rest a bit takes like tens of minutes of work.

---

### Post by Alcareru on 2011-01-20
BIOS update didn't help. Anybody having some other ideas? Help? It's really killing me that getting the computer working if I let the screen rest a bit takes like tens of minutes of work.

---

### Post by Alcareru on 2011-01-28
Bump. Help? Anything? The new kernel 2.6.35-25-generic didn't help. I think I have managed to pinpoint the "solution" to a bit more simple one. I have recently started to abuse me-tv for this purpose. It seems to provide enough of "doing randomly stuff" so that if I'll just start me-tv (alt+F2, me-tv, enter) wait for like 5 to 10 minutes and then turn the screen off and back on again I can see again.

---

### Post by mharrison on 2011-01-28
I tried to read carefully so if I missed this I apologize...

But, have you tried a different monitor on the machine to see if possibly you are having a monitor failure.

---

### Post by Alcareru on 2011-02-02
> **mharrison said:**
> I tried to read carefully so if I missed this I apologize...

But, have you tried a different monitor on the machine to see if possibly you are having a monitor failure.

Hmm.. a monitor failure.. I sort of dismissed the possibility because the screen eventually always starts to work and continues to work for days (as long as you never leave it inactive for an extended period of time). Now, after you said it I see that such a dismissal is not well grounded. Unfortunately I do not have another screen. However I do have a laptop. I quickly experimented using the screen with my (linux) laptop a couple of days ago and had similar issues. However with that laptop and linux I've always experienced some great difficulties when it comes to plugging it to external display devices so I'll have to dig into it bit more (damn ATI graphics drivers...).

I'm just checking in to let you guys know I'm still working on this. It's just very time consuming problem to debug. I'll try to cough up some more time to spend on this hopefully today or tomorrow and report if it seems the problem is actually a HW failure of the screen.

---

### Post by mharrison on 2011-02-02
Understood.  The only reason I even mentioned it is because I had a similar issue with a monitor a few years ago.  Once you got it on it would run for days, but if you turned it off you would have a heck of a time getting it back on.

Good luck!

---

### Post by Alcareru on 2011-03-23
To conclude this all. I can now confirm it turned out to be a monitor failure as mharrison suggested. In the end the old screen stopped working all together after I rebooted a couple of days ago due to the latest kernel update. Then I had no other choice but to get a new screen and now there's no problems. Thank you for your help!

---

