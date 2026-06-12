---
title: "Compaq r3000 ati ixp"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by Word on 2006-07-24
I have a compaq r3000 great machine fast everything works but ESD. When i start my computer sometimes is freezes becaue of esd I alt+ctrl f2 log in and sudo top and kill esd.

Then i got smart under system/preferences/sound i turned off esd but not i cannot use totem and beep together. As I understand its because of the ATI IXP sound card i've read everywhere there does not seem to be a solution that I can find. Am i stuck?

Thank you for your help.

---

### Post by Word on 2006-07-25
more /dev/sndstat output


Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux kweli-laptop 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
ATI IXP rev 0 with AD1981B at 0xe8003000, irq 5

Audio devices:
0: ATI IXP AC97 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Analog Devices AD1981B

---

### Post by qamelian on 2006-07-25
> **Word said:**
> I have a compaq r3000 great machine fast everything works but ESD. When i start my computer sometimes is freezes becaue of esd I alt+ctrl f2 log in and sudo top and kill esd.

Then i got smart under system/preferences/sound i turned off esd but not i cannot use totem and beep together. As I understand its because of the ATI IXP sound card i've read everywhere there does not seem to be a solution that I can find. Am i stuck?

Thank you for your help.

Wish I could figure out why this happens. I'm using a Compaq Presario R3000T and have the same problem. Strangely, this problem only exists in Dapper, not in Breezy. What I've done is to create a script that kills esd on login and drop it into my startup in the session manager. It's just a "killall esd", but it allows my laptop to hit desktop without my intervention. After esd is killed it respawns itself automatically.

---

### Post by Word on 2006-07-25
the worst part is it seems to be like 5 people with the issue. Ive just delt like maybe someone will fix it in "edggy eft"

---

### Post by qamelian on 2006-07-25
> **Word said:**
> the worst part is it seems to be like 5 people with the issue. Ive just delt like maybe someone will fix it in "edggy eft"
It's the only really annoying thing I've found in Dapper. I considered going back to Breezy, but the positives for me in Dapper vastly outweigh what, for me, is a relatively minor issue.

---

