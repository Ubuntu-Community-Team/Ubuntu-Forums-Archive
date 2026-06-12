---
title: "No sound dual boot (newbie noob)"
date: 2010-02-14
forum: Hardware
---

### Post by cat2005 on 2010-02-14
**I just received my new dual boot:  I installed both Ubuntu 9.04 and Windows XP Pro.**

However, when using the motherboard's "audio out" port, I receive no sound.  I used the same speakers and headphones which worked perfectly well with my prior computer.

Also, this new pc does have a sound card.  I do get sound using the sound card in Windows once I install the drivers.  I do not get sound in Ubuntu but then again, maybe it doesn't have Linux drivers available.

_My suspicions_:

a) The motherboard has a dead sound component.
b) The sound card doesn't work in Linux because there are no drivers included

_Questions_:

1)  Do these symptoms confirm my motherboard's sound component is dead?
2)  If my sound card does have Linux drivers, then where would I find them?

_Here are my relevant specs_:

a)  Intel i3 @ 3.06ghz
b)  ASUS P7H55D-M EVO mATX Intel 55 Chipset Motherboard (*very new motherboard*)
c)  4gb System Ram
 d)  Creative Sound Blaster X-Fi Xtreme Audio PCI Express Sound Card
e)  2x Internal SATA hdd with Ubuntu 9.04 on onw and Windows XP Pro on the other (*both 32 bit*)

**I would appreciate your thoughts!  Thank you!**

---

### Post by cat2005 on 2010-02-16
The mobo sound was turned off so it would not conflict with the sound card, which was turned on.

---

### Post by viper250 on 2010-02-16
usually installing a sound card will disable the onboard audio! many people installed sound cards because they had their own amplifier or 3d surround sound capability
anyhow try removing the card and connecting to the onboard sound jack and testing your live cd see if it loads a sound driver that works.
you will get error messages if the audio is not detected.
the intel chipset might not be supported by linux

---

### Post by cat2005 on 2010-02-21
Yeah, it seems to work now.  Thanks!

---

