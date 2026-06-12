---
title: "weird alsa problem"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by dave_euser on 2007-02-03
This is strange.... I've found that if I have the order of my alsa hw config set as:
    saa7134 index=0
    emu10k1 index=1

mplayer, gnome sound, etc all choke to some degree. However, if I modify my alsa-base configuration to switch the order:
    saa7134 index=1
    emu10k1 index=0

Everything works perfect, except unreal tournament 2004 has a "slowdown" in the audio - it doesn't stop generating sound, but the output changes to about 1/2 to 1/3 the speed of what it should be, for about 30s until it recovers....

I've got a SB Audigy 2 and a no-name flyvideo something video capture board (where the saa7134 shows up).... any ideas?

---

