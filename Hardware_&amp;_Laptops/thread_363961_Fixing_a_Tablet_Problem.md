---
title: "Fixing a Tablet Problem"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by the ev on 2007-02-17
So I love Ubuntu so much I put it on my ThinkPad X41 Tablet; so far it's working great.

I used the instructions found on this wonderful [wiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_on_a_ThinkPad_X41_Tablet"), but I've been having with the Suspend fix.

Basically, it works - but only if the system hasn't been suspended for too long.  I don't know the exact time, but waking the system up from a longer period of suspension gives me two brief error messages (something about an overcharge to a port, maybe USB 3 and 4 - it's really hard to read since it's only on the screen for less than a second), and Ubuntu drops the wacom fuctionality.

Given the information on the aforementioned wiki article, would anyone know how I might go about fixing this?  I tried running the script manually (/etc/acpi/resume.d/20-setserial.sh), but I got the following error:

```
Cannot autoconfigure port: Device or resource busy
```

...which I was a little confused about, because the wacom was not working.

As far as I know, though, this is the only problem I have with the system after an extended period of suspension.

Is it possible to restart the device manually, or in a script?  I don't have much experience with talking with hardware through Linux...

Any ideas and/or suggestions would be much appreciated! Thanks!

---

### Post by sackles on 2007-02-20
Amazing how closely this situation mirrors mine - I've been trying to get my thinkpad working for a couple of months now.  

Keeping my tablet in standby for more than 20 or so seconds seems to keep the pen from working on resume, while shorter durations work just fine.  

Also,  I am able to get the pen working again, but only after restarting the xserver and re-running setserial again from one of the terminals.

I've also tried changing where in the resume sequence the setserial command goes - nothing seems to help

Anyone have any ideas/thoughts/brilliant suggestions?

---

### Post by the ev on 2007-02-20
I talked with my friend just recently and he said the problem might be related to how a system suspends.  If I understood him correctly, in the first period of time x the system stores state information in RAM, then after enough time has gone by, transfers that state information to Virtual RAM on the HD so as to not draw on the battery to keep info in RAM.  We can surmise then that maybe Ubuntu is not storing the wacom state information to VRAM, so that when the system wakes up after an extended period of suspension, it is not drawing back the wacom because there's nothing to draw back.  Of course, I'm confused how this may or may not be related to those weird error messages I get...

I've really no idea how that might help to fix the problem, but I thought I should throw that out there.

---

