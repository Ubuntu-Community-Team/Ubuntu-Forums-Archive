---
title: "Soundblaster X-Fi Installed, no sound"
date: 2009-11-23
forum: Hardware
---

### Post by th3j3ster on 2009-11-23
Hey all,

So I've checked through the forums and found many helpful steps, and I was able to get Ubuntu 9.10 to recognize my Creative Soundblaster X-Fi PCI-e card. I've checked through the gnome sound preferences, alsamixer, alsamixergui, and gnome-alsamixer, and I can't find anything muted or any of the volumes down. My lspci -v output makes it look like the card should be working (I'll paste that below), but for some reason there is still no sound whatsoever. I know that the card and the speakers are working, as I am dual booting Win 7 x64 and the card/speakers have no issue there. Please help, its not mission critical, but it is very annoying to have to switch back to Win7 to watch a video...or music..or youtube etc...I know I should buy a more linux-friendly card, but this is an older card and purchasing a new one isn't an option now. Thanks to everyone in advance! 



04:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=04, secondary=05, subordinate=05, sec-latency=64
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel modules: shpchp

05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
    Subsystem: Creative Labs Device 0018
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at feafc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by th3j3ster on 2009-11-24
Heh...now that its not the middle of the night maybe someone else could take a look :smile: Any ideas?

---

### Post by th3j3ster on 2009-11-24
I should also mention that the x-fi driver got set as HDA Intel after I installed linux-backports-modules-alsa-karmic-generic...I hope this helps

---

### Post by guillemsola on 2009-11-24
Blame Creative and buy another card!

I have tried everything with the XFi with CA0110 chip. Currently there is no linux driver for this. There was a something like a "driver" from kernel 2.6.31-rc1 to 2.6.31-rc5 but a patch broke it's poor support.

Now I have a SB XFi titanium PCIE with the emu20k2 chip and since alsa 1.0.20 works well.

---

### Post by th3j3ster on 2009-11-24
Well that's just my luck. It looks like I have two choices...either go over friends houses and flip couch cushions when they aren't looking to gather change, or wait and pray that support for the CA0110 is added....decisions decisions. 

Seriously without a doubt, this is the last Creative card I will ever, ever buy.

---

### Post by Trifidlebock on 2009-11-24
Damn... same problem.  We're stuck waiting then?

---

### Post by th3j3ster on 2009-11-24
Well I checked around now further using the exact chipset model to search...yeah it looks like we are stuck for the moment. Doesn't look like anyone else has had luck getting our chipset to work. Some of the other x-fi seem fine, just not ours :(

---

### Post by guillemsola on 2009-11-25
If you look at the creative page about this card there is no linux driver.

Other XFi with emu chipset has a previous driver that creative just released as GPL a few months ago.

Consider sending an email to creative asking for a driver, I did it too ;)

---

### Post by whoop on 2009-11-25
Hhhm, my X-fi xtreme gamer is working fine, out of the box... The current kernel in 9.10 is the first that should support it.

---

### Post by johnb820 on 2009-12-04
Do install or upgrade to the latest version of alsa 1.0.21 which includes support for the x-fi. As of now, I have playback working under Karmic, but I can't get recording to work. I also have not tried 5.1 yet.

---

