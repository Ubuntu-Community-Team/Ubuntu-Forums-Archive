---
title: "no sound card found in 9.10 64 bit"
date: 2010-03-14
forum: Hardware
---

### Post by cgb223 on 2010-03-14
hey my sound card is not found when going to my sound settings making it awful hard to listen to music. every time the kernel is upgraded, it seems i loose and regain this functionality, alternating on each one. any idea why? I'd like to be able to hear things on my compy. 

just to clarify, there is not a single sound card showing in the sound prefrences thing. and my headphone jack doesnt work either. 

i am running a smexy sager 9280. 

if you need any more info please let me know, i want to listen to my music, and get back to lmms.

---

### Post by knightop on 2010-03-14
I have a similar problem.  

I'm on a HP dv2845se, which has known sound card instability in Windows.  I tried dual-booting with Ubuntu 9.10 (kernel 2.6.31) and the sound card was recognized! Great!

Unfortunately the wireless was not.  I had to upgrade the kernel to 2.6.32 to get the b43xx fwcutter support for my broadcom card to work.  Now I have no sound :(     

Before the upgrade "lspci" was listing my sound card correctly under the MCP67 HDA driver.  Now, the sound card doesn't show up at all.  This happened in Windows as well, the device manager wouldn't recognize the PCI high def audio device at all.  

I'm new to Linux and am eager to learn...any suggestions on things to try would be welcome.

Thanks

---

