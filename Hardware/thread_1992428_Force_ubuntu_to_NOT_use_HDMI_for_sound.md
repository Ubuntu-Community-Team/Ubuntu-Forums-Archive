---
title: "Force ubuntu to NOT use HDMI for sound"
date: 2012-05-31
forum: Hardware
---

### Post by Tijn1978 on 2012-05-31
_Hi guys,_

I recently found out that to use my hdmi cable instead of vga, all i had to do is unplug the vga and reboot. Brilliant!
However, now sound is send to my monitor and the sound, well it ain't that good. I want to use my onboard sound.
I used alsamixer in a terminal to see if I could change it but it only sees my NVIDIA card (graphics+sound)

Could someone point/advice me to the right location or simply tell me what to install? Preferebly a GUI to set it up.
I'll post a short howto in order to help others out.

I already tried another part of the forum. Reinstalled libalsa32.. something in order to undo the damage done by unplugging my vga cable.

_cat /proc/asound/cards :_
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf9f78000 irq 23
_From alsamixer:_
Card: HDA NVidia
Chip: Realtek ALC1200

Hope someone can point me in the right direction..


Thanks in advance,
Tijn1978

Recently I came to find out that sound is send to both speakers and monitor. There is no issue here :)

---

