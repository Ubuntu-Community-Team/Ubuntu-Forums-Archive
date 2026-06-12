---
title: "firewire car recommendation"
date: 2008-07-03
forum: Hardware
---

### Post by chillyair on 2008-07-03
Can any one recommend a good pci firewire card that you know will work on hardy. I just bought a new card but so far i've absolutely no luck getting it to work. From a little web research it seems that getting any firewire card to work on linux is almost unheard of. I really want to be able to capture video from my camcorder and will be really dissapointed if I can't. So please, anyone who knows anything about how to install a card or which ones to use let me know. Otherwise i'll have to go back to windows.

---

### Post by phidia on 2008-07-03
I have 1394 working on my computer now (this one has onboard fw) but I have had it working through two different PCI cards in the past.
Many companies don't bother to advertise linux support and they don't want to offer phone or email help I suppose. But I haven't found it difficult to get my cards recognized at all.

what does lspci -v  and dmesg output for you?

You can check [here]("http://www.linuxquestions.org/hcl/index.php/cat/201") and [here]("http://kmuto.jp/debian/hcl/") to look for and check your device(s).

---

### Post by chillyair on 2008-07-03
> **phidia said:**
> I have 1394 working on my computer now (this one has onboard fw) but I have had it working through two different PCI cards in the past.
Many companies don't bother to advertise linux support and they don't want to offer phone or email help I suppose. But I haven't found it difficult to get my cards recognized at all.

what does lspci -v  and dmesg output for you?

You can check [here]("http://www.linuxquestions.org/hcl/index.php/cat/201") and [here]("http://kmuto.jp/debian/hcl/") to look for and check your device(s).

lspci -v lists the device:

01:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
	Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at dc00 [size=128]
	Capabilities: <access denied>

wasn't quite sure how to read through dmesg but I can list the results if you really want. 

I'm a little bit new to linux so I may not know all the procedures on how to get cards reckognised.

What i want to be able to do basically is import dv video from my canon ZR 800 using kino. However when I go to the IEEE 1394 tab in preferences, the device is not listed.

Can you help me out at all. I'm completely stumped on what to do.

---

### Post by phidia on 2008-07-04
From this [page]("https://help.ubuntu.com/community/Video") which is itself useful reading-check out the section on [1394]("https://help.ubuntu.com/community/Video#Firewire%20(IEEE1394)")
Hope that helps.

---

### Post by chillyair on 2008-07-05
Wow I feel stupid. It turns out it was just a faulty firewire cable all along. Here I was cursing linux. Lesson learned for me.

---

