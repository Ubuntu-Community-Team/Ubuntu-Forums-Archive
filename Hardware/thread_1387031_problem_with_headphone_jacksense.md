---
title: "problem with headphone jacksense"
date: 2010-01-21
forum: Hardware
---

### Post by suprem1ty on 2010-01-21
hey guys, im really new to ubuntu and linux and have been having this prick of a problem whereby the internal speakers of my laptop wont mute when i plug in a pair of headphones.

ive been searching all over the net and have found a few sites that recommend setting
options snd_hda_intel model= with various models etc in the file alsa-base.conf in etc/modprobe.d, ive been messing around with it for ages, changing the model with some recommended ones and rebooting to no effect. ive tried all sorts of things and just cant get it to work right, id be grateful for any help, im running v10.04 of ubuntu with all the updates, but i had the same problem in 9.04.
my laptop is a fujitsu siemens amilo pro v3545 with realtek ALC883 audio, all the hardware etc is fine as it was working aight in windows vista etc so i donno what more i can do; thanks for any help you can give me

---

### Post by suprem1ty on 2010-01-22
anyone got any ideas or suggestions?

---

### Post by suprem1ty on 2010-01-23
i tried fedora and it had the exact same problem, this is really putting me off using linux, before i throw in the towel and just use windows for everything can anyone suggest anything for me to try :\ no headphones is a big put off for me

---

### Post by suprem1ty on 2010-01-24
haha im stoked i found a fix, for those of you with a similar problem or a fujitsu v3545 / realtek alc883 try this: add options snd_hda_intel model=6stack-dig to etc/modprobe.d/alsa-base.conf then use gnome alsamixer changing front volume / mute to effect headphones and surround volume to effect internal speakers

---

