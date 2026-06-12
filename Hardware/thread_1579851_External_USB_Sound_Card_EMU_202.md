---
title: "External USB Sound Card EMU 202"
date: 2010-09-22
forum: Hardware
---

### Post by florian_roger on 2010-09-22
Hello,

I would to use my external usb sound card EMU 202 with my Ubuntu but don't understand how to do. I saw that people were working on a driver for this stuff on Linux, but I can't find an how-to about using it.

Thanks for your help.

Florian

---

### Post by lkjoel on 2010-09-24
> **florian_roger said:**
> Hello,

I would to use my external usb sound card EMU 202 with my Ubuntu but don't understand how to do. I saw that people were working on a driver for this stuff on Linux, but I can't find an how-to about using it.

Thanks for your help.

Florian
Why don't you take an internal sound card?

---

### Post by florian_roger on 2010-10-24
Hello,

I'm helping someone who buyed that card working with M$, but he is now on Linux and would like to use his own external card..

---

### Post by cchhrriiss121212 on 2010-10-24
According to my searchings [this card]("https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1") has partial support:
> The support for the EMU USB cards has started, and basic support is now  in the latest alsa hg. It only supports 48000 rate, but all the in/outs  should work. 

First check that the OS can access it, from a terminal try:
aplay -l
arecord -l
lsusb

Then open up alsamixer to check the sample rate is 48000 and set volume levels. According to other users, capture volume can only be controlled by the hardware.

---

