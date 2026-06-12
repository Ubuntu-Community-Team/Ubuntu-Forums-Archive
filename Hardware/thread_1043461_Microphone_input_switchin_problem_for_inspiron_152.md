---
title: "Microphone input switchin problem for inspiron 1525"
date: 2009-01-18
forum: Hardware
---

### Post by lorandsm on 2009-01-18
Hi,

I have a dell inspiron 1525n laptop without camera but it has a built in microphone. The sound chip is sigmatel. BIOS says it's a Sigmatel 9205, alsamixer says it's a STAC9228, lspci -v describes it as:

0:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Device 022f

and finally lspci -vn tells it's:

0:1b.0 0403: 8086:284b (rev 02)
        Subsystem: 1028:022f

The build-in microphone works by doing modprobe snd-hda-intel, but if I plug in an external microphone, the one that continues to work is the built in one. Changing the input switch to "front mic" or "line" mutes the built in microphone but from the external one still won't be captured anything. I've tried to give different values to the model parameter of snd-hda-intel and only if I use model=5stack then the built in microphone won't work but the external one (but only if the input source is set to mic and not if set to "front mic" or "line"). I would like to change between the two microphone inputs, is there some way. The kernel version I use is 2.6.28 on debian testing.

---

