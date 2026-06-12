---
title: "ALC888 Help: Surround sound."
date: 2010-08-02
forum: Hardware
---

### Post by puredeviation on 2010-08-02
Hi, I am having a problem with getting my surround to work with the sound card. What happens is the Front and Surround speakers work, but the Center and Subwoofer channels don't work with some applications. 

Here's an example. When I am playing a 5.1 movie on my computer and I have the Center channel plugged in and the Subwoofer works.

When I play music, All speakers work, but the Subwoofer does not. 

Can someone help me with this problem? Much appreciated.

---

### Post by utilitytrack on 2010-08-02
Hello, too little info. Did you adjust the levels in alsamixer? What players you used?
What settings? What ALSA version? Which driver? Probable [FONT=Courier New]snd-hda-intel[/FONT]? 

If so, put here
```
# cat /proc/asound/card0/codec* | grep -i codec
``````
# cat /etc/modprobe.d/alsa-base.conf | grep intel
``````
# hwinfo --sound
```Also look here: [http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound)

---

