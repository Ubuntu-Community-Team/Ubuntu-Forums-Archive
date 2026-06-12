---
title: "Sound"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by hercvyfm on 2005-04-28
I have an old KDS laptop and i had Warty on it and everything was fine but when i upgraded to Hoary my sound does not work it give me an error of dev/dsp not found what can i do to get it to work.

Thanks

---

### Post by jliedeka on 2005-04-29
[QUOTE=hercvyfm]I have an old KDS laptop and i had Warty on it and everything was fine but when i upgraded to Hoary my sound does not work it give me an error of dev/dsp not found what can i do to get it to work.

Thanks[/QUOTE]
 I have the same issue with my Sony S-270.  Sound worked great with Warty.  Since I upgraded to Hoary, nada.  The drivers appear to be all loaded.  Xmms doesn't work with ALSA or OSS.  My flash plugin is silent also.  Xine doesn't give sound either.

Does anyone have any ideas?  I've been spoiled by linux distros from the last few years.  I expect sound to just work.  I haven't had to figure out sound problems since ISAPNP under Red Hat 5.0.

     Jim

---

### Post by kevinlyfellow on 2005-04-29
Maybe this will help?
[http://www.ubuntulinux.org/wiki/SoundProblemsHoary](http://www.ubuntulinux.org/wiki/SoundProblemsHoary)

---

### Post by jliedeka on 2005-04-29
My system didn't like ESD for XMMS.  ALSA and OSS fail to give sound.

jliedeka@damballa:/usr/lib $ lsof | grep snd
xfce-mcs- 8293   jliedeka    5u      CHR      116,0               6659 /dev/snd/controlC0
xfce4-pan 8302   jliedeka    8u      CHR      116,0               6659 /dev/snd/controlC0
xmms      8827   jliedeka    8u      CHR      116,0               6659 /dev/snd/controlC0

jliedeka@damballa:/usr/lib $ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux damballa 2.6.10-5-686 #1 Tue Apr 5 12:27:02 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Intel 82801DB-ICH4 with AD1981B at 0xd0000c00, irq 9

Audio devices:
0: Intel 82801DB-ICH4 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Analog Devices AD1981B

That IRQ 9 thing kind of worries me but I don't know if that matters anymore.

---

### Post by jliedeka on 2005-04-29
I upgraded to the 2.6.11 kernel.  That magically fixed the sound but now my touchpad is really slow and tapping doesn't work. :(

---

