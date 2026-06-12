---
title: "No Sound"
date: 2009-09-23
forum: Hardware
---

### Post by akjerryo on 2009-09-23
I have kubuntu 9.04. It took me awhile to get it running on my Asus F50SF-X1A laptop. First the wireless wasn't working... Got it running and everything else is fine now except sound.

aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and the lspci -v audio section:
> 00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
        Subsystem: ASUSTeK Computer Inc. Device 15d3
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f9ff4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


now I saw this fix with searching, adding 
> options snd-hda-intel position_fix=1 model=lenovo to the end of alsa-base.conf ... not sure if that is the right line for my laptop though! Any ideas? Added the line and rebooted, and still no sound.

Thanks!

---

### Post by akjerryo on 2009-09-24
After searching some more, I came across the Comprehensive [Sound Problems Guide]("http://ubuntuforums.org/showthread.php?t=205449"), and I tried everything listed there... Still haven't bee able to get sound working :confused:

---

### Post by akjerryo on 2009-09-25
ok so after 2 days of tireless reading, searching, and experimenting. I had made no progress... Until I read some where about laptop sound problems, not working, speakers not working but headphones working or the other way around. So I decided to plug headphones in, and sound works! Granted the sound on headphones is much better than from the speakers, it would still be nice to get sound working on the speakers.

Guess its back to research >.>

Update, guess it kind of works? When I click the test button on System Settings -> Multimedia, it works... but no where else... so annoying >.<

---

### Post by akjerryo on 2009-09-26
Ok since there hasn't been any replies other than my own...

Does anyone think sound might work better, along with some of the other issues I have.. If I switch from 64bit to 32bit?

I have been crawling through post after post, and there hasn't been any breakthrough. Other than when I click test in the hardware manager I can hear the test, but there isn't sound anywhere else...

I am just running out of ideas >.<

---

### Post by aloyr on 2010-01-11
i am on the same situation here...

kubuntu karmic, hp dv7-3065dx lappy, no sound.

---

### Post by ashgoodman on 2010-05-15
Ditto,

As nice as the eye candy is in kde4 stability of kde has taken a serious turn for the worse.

I am considering moving to opensuse for a kde distro instead

---

