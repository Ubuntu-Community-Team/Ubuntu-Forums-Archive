---
title: "Realtec AC '97 Driver Install Issues"
date: 2006-09-10
forum: Hardware &amp; Laptops
---

### Post by Jomo182 on 2006-09-10
I have an Emachines M5405 POS.I figured out what my sound card was and downloaded the Driver for it but the linux version driver is for Redhat Fedora so when I try to install it all the directories are different. I was wondering if there is an alien command or some other way to install the driver that someone out there is aware of. Thanks,

Jomo

---

### Post by Jomo182 on 2006-09-10
O yeah my Ubuntu thinks my sound card is a SIS SI7012.

---

### Post by dannyboy79 on 2006-09-22
did you ever get the sound working for your card. I have the same card and I have sound but only out of the left side. it did all work at one time but after playing xmms thru remote desktop only sound comes out of left speaker now. Really weird. When i was using flight 7 sound worked fine but when i reinstalled ubuntu using the fianlly released version I ended up with this problem. I have a thread started but no one will answer me!

---

### Post by radiobuzzer on 2006-12-12
> **dannyboy79 said:**
> did you ever get the sound working for your card. I have the same card and I have sound but only out of the left side. it did all work at one time but after playing xmms thru remote desktop only sound comes out of left speaker now. Really weird. When i was using flight 7 sound worked fine but when i reinstalled ubuntu using the fianlly released version I ended up with this problem. I have a thread started but no one will answer me!

I have something relevant. Using RealTec HD on an Acer laptop. When Ubuntu starts, I have sound only from the right speaker. Then if I go and play with the mixer balance, the sound gets correct. BUT, for some reason, I can't record. When I try to do so in Windows, the mixer or the recording program behaves as if there were two soundcards, one RealTec HD Input and one RealTec HD output problem. Linux doesn't see the Input thing at all, and can only play.

---

### Post by lamy on 2007-01-29
The sound works out of the box on the M5405.  I posted the solution in another forum, here is a copy of it:

Here is what worked for me:

1. Double click on the speaker volume Icon.
2. Goto: File --> Change device, and make sure that "0: SI7012 (Alsa Mixer) is selected.
3. Click on the "Switches" tab.
4. Uncheck "External Amplifier"

If it still doesn't work, max out all of the volume levels.

Hope it helps,

lamy

---

