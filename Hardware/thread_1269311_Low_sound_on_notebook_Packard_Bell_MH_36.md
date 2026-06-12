---
title: "Low sound on notebook Packard Bell MH 36"
date: 2009-09-18
forum: Hardware
---

### Post by seolover on 2009-09-18
Hi. I've low sound on notebook Packard Bell MH 36. Sound chip is ALC272. On XP, Vista sound is ok.

lspci -v
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 03)
	Subsystem: Packard Bell B.V. Device 018b
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f4700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

aplay -l
> card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice &#8470;0: subdevice #0

---

### Post by seolover on 2009-09-18
Up

---

### Post by ultimatebuster on 2009-09-19
easy stuff, check this out

[http://thekks.net/570](http://thekks.net/570)

---

### Post by seolover on 2009-09-21
I've tried this. Also, i've update ALSA to 1.0.21 but nothing.

---

### Post by seolover on 2009-09-22
Guys. Help me please.

---

### Post by TheMadMan on 2009-09-23
> **seolover said:**
> Guys. Help me please.


hi,

I installed ubuntu 9.04 yesterday and noticed that my sound was much lower than win7.  I have a Dell XPSM1530.  I tried the link mentioned above ([http://thekks.net/570](http://thekks.net/570)) and it certainly did the trick for me.

Maybe worthwhile giving it a try again.

regards

---

### Post by seolover on 2009-09-24
I've tried this, also i've tried all that is said here:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by seolover on 2009-09-25
Up

---

### Post by seolover on 2009-09-30
Up

---

