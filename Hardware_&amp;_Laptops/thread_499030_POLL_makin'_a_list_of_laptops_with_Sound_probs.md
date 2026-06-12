---
title: "POLL: makin' a list of laptops with Sound probs"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by matheuu on 2007-07-12
Ok then, 
Guess I will go first!
I have a fairly new Toshiba Satellite A200  Model Number: PSAF0A-04X019 (bought in Australia)
Had Vista on it.  Now has Feisty 7.04
No Sound at all.

If anyone reads this... and has a laptop that has/had sound problems with Feisty .... then please add to the list so we have an idea on the numbers of unfortunate individuals out there with natural born mute Ubuntu machines!

Cheers all
Mat

---

### Post by renzokuken on 2007-07-12
I have a Evesham Quest A240 (Clevo/Kapok MJ665 clone or something) which has no sound at all by default  on any ubuntu version i tried.

i fixed it by updating to the latest **alsa-driver** (compiling it from source)

```
Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: CLEVO/KAPOK Computer Unknown device 0661
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 50
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by drummingpariah on 2007-07-12
It may be a much better idea to post the sound card model number instead of the computer manufacturer model number here.

For example (my case):

type lspci in the command line, then scroll down to whatever audio device you have.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

on an Asus a8jm

This is a solved issue, but requires a workaround (posted on the forums, I just don't care to search for it :lolflag:

---

### Post by lisati on 2007-07-12
Toshiba A100, model number PSAA2A-03501n, purchased in NZ, no sound on first install of Ubuntu 7.04. Fixed by using update manager to do update, reboot, and adjusting volume.

---

### Post by matheuu on 2007-07-12
yeah my thing has the same card.
might be worth listing the cards...

---

### Post by Tegdap on 2007-07-18
Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) on a Gateway m210 laptop, no sound with Ubuntu Feisty....

---

### Post by Cavalier1723 on 2007-07-18
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) / Sony VAIO FZ190 / No sound through head-phone jack, speakers keep playing

---

### Post by fd9_ on 2007-07-18
Lenovo T61 here, and no sound.

---

### Post by David A Knight on 2007-07-29
> **Cavalier1723 said:**
> Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) / Sony VAIO FZ190 / No sound through head-phone jack, speakers keep playing

create or add the following line to /etc/modprobe.d/sound

options snd-hda-intel model=vaio probe-mask=1

This should make more items appear in the volume control + get sound through the headphone jack, won't stop the internal speakers from still playing though.

---

### Post by hessiess on 2007-07-29
hp pavilion dv2000

hda intell conexant cx20551 (waikiki)

sound works, but extremly bad qualaty, cannot record.

---

