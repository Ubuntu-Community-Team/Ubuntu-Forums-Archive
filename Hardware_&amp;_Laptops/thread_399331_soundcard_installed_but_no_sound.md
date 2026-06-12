---
title: "soundcard installed but no sound"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by darkos on 2007-04-02
My motherboard is this one: gigabyte ga-k8nf-9 and im usin the onboard soundcard
I installed kubuntu, everything is fine but when i decided to plug in my headphones i couldnt hear any sound, i looked at Kmix and everything seems ok.
im using alsa rivers and in kinfocenter i can see this:
---------------------------------------------------------------------------------------
Sound Driver: 3.8.1a-980706 (ALSA v1.0.12rc1 emulation code)
Kernel: Linux darkos-server 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
NVidia CK804 with ALC850 at 0xf0100000, irq 225

Audio devices:
0: NVidia CK804 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC850 rev 0
---------------------------------------------------------------------------------------
Is there any other information i should post for anyone to help me?
thanks in advance :)

---

### Post by stworek on 2007-04-02
maybe is it  muted in alsamixer, are you in audio group?

---

### Post by darkos on 2007-04-02
Primary group: darkos
Secondary groups: adm, dialout, cdrom, floppy, audio, dip, video, plugdev, lpadmin, scanner, admin

---

### Post by darkos on 2007-04-02
i ran alsamixer, pushed all bars to the top, but still no sound...

---

### Post by Eversmann on 2007-04-02
Maybe it's a problem with the motherboard bios and the kernel interrupt asignation. Try to boot the kernel with noapic for instance and see what happens ;-)

---

### Post by darkos on 2007-04-02
d'oh that sounded like chinese to me >_<
Maybe you could try and be a little bit more explicit?
all the instructions step by step :)
sorry for being such a noob :P

---

