---
title: "Wireless adapter disappeared - please help"
date: 2008-07-31
forum: Hardware
---

### Post by finomeno on 2008-07-31
Hello!

I'm using an HP Pavilion dv6095ea laptop (AMD Turion 64 x2) with a Broadcom 4312 wireless adapter. Running Ubuntu Hardy 8.04.1 (32 bit) with the b43 driver. I have a dual boot system with Win XP Home.

My wifi (and everything else) was working with no problems and no need to use ndiswrapper like in previous versions of Ubuntu, but since I suspended the laptop this morning my wireless card has disappeared from the system. It is not shown anywhere in network settings, nm-applet or lspci. The system just doesn't seem to see the card. :-k

Suspecting a hardware problem I shut down the computer and rebooted into Windows which not only recognised the wireless card but also connected to my router as usual, no questions asked. :???:

All of this leaves me puzzled because I cannot imagine what could cause Hardy to suddenly stop seeing a device with which it was working perfectly before. :confused:

Please help me find an answer to this if you can (-:
Any suggestions appreciated.
Thanks!

PS
I toggled the wireless on/off switch on the laptop several times, including during going into suspend/waking up/turning off/on to no avail.

---

### Post by phidia on 2008-07-31
Sometimes there are issues with wireless cards from doing suspend/resume-I wish that weren't so but it is.

The one thing you didn't say is if you tried to reboot and see if you can connect and NM sees your card. If it works after a reboot but fails from suspend/resume then we know the problem is with acpi stuff.

If you still don't have a connection when you boot into ubuntu then open a terminal window and enter > iwconfig & > lshw -C network post the output.

---

### Post by finomeno on 2008-08-01
Thanks for your reply.
My case is more tricky. I did reboot several times, but to no avail. The system is acting as if the card was not in the laptop at all. No wireless hardware whatsoever. Although it was there and was setup and working normally just 30 minutes before it disappeared. Plus, Windows sees the hardware. I even took the card out, cleaned it, put it back in and reset my BIOS. No result...

---

### Post by finomeno on 2008-08-01
**Problem solved.** :)

The card disappeared in Windows as well. Apparently it was a hardware problem due to an undocumented conflict between motherboard, battery and the Broadcom wireless card in many HP laptops.

If anybody else is experiencing the same type of problem - look at [this forum]("http://forums12.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1217621466431+28353475&threadId=1107945") - there are several solutions for this.

Thanks for the help and hope this helps in case your wireless disappears.

---

