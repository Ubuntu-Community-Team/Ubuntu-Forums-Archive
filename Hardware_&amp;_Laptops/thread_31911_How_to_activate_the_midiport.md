---
title: "How to activate the midiport?"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by maliStfn on 2005-05-05
Hello to everybody,
I try to activate the midi port on my ubuntu hoary computer. It has a terratec aureon fun sound card. On a suse audio live distr I managed it to work, there was the posibility to do it with the yast.
the bold line I would like to change:

stfn@jebiga:~ $ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux jebiga 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738-MC6 (model 55) at 0xb800, irq 10

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

[B]Midi devices: NOT ENABLED IN CONFIG
[/B]
Timers:
7: system timer

Mixers:
0: CMedia PCI

Is somebody here wanting to help me? thanx
greetings, ..stefan

---

### Post by ludi on 2005-05-05
[QUOTE=maliStfn]Hello to everybody,
I try to activate the midi port on my ubuntu hoary computer. It has a terratec aureon fun sound card. On a suse audio live distr I managed it to work, there was the posibility to do it with the yast.
the bold line I would like to change:

stfn@jebiga:~ $ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux jebiga 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738-MC6 (model 55) at 0xb800, irq 10

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

[B]Midi devices: NOT ENABLED IN CONFIG
[/B]
Timers:
7: system timer

Mixers:
0: CMedia PCI

Is somebody here wanting to help me? thanx
greetings, ..stefan[/QUOTE]
 I don't know if this chip have it (and if so, propably is very very bad).
Try load the snd-seq-oss module during the boot process.
Use the sudo nando  /etc/modules to do it.
Anyway, you can load a soft synth to play the midi sounds.
If you want to use this for a professional purpose, you should invest in a decent and much more capable sound card.

---

### Post by maliStfn on 2005-05-06
[QUOTE=ludi]I don't know if this chip have it (and if so, propably is very very bad).
Try load the snd-seq-oss module during the boot process.
Use the sudo nando  /etc/modules to do it.
Anyway, you can load a soft synth to play the midi sounds.
If you want to use this for a professional purpose, you should invest in a decent and much more capable sound card.[/QUOTE]
 Good morning ludi,
thanks for taking time. Yes, the chip has it and it is good enough for me. I just have a keyboard hanging on it and as I wrote it was possible to activate this port on suse with yast and I worked with it a long time running w98 on my box. It would be a pitty to switch back to w98 because of a not working midiport :) everything else works more or less perfectly on my box now, even my old korg1212 (2nd soundcard).
Maybe my english is not propper enough to explain it, but there must be a place in ubuntu to add options for this card like ```
options snd-cmipci id="first" enable_midi="1"
``` I tryed in /etc/modutils/alsa-base, but it didn't work :| .

The only thing that I recognized while adding the snd-seq-oss module was that jack started with no errormassages loading it without the snd-virmidi module. For now I'll leave the snd-seq-oss module because it doesn't harm the functionality of the rest and maybe it is one step to get more near to the problems solution. But what I really need is a readable and writeable mpu_401 client appearing in jack :roll:

---

