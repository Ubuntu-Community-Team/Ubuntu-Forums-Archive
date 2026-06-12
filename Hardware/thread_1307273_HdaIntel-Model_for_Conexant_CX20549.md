---
title: "HdaIntel-Model for Conexant CX20549"
date: 2009-10-31
forum: Hardware
---

### Post by chari on 2009-10-31
Hey guys,
my sound works, but only through headphones and my internal mic doesn't work.
I got my sound working using this guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
I already tried to find the correct model using this one:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
And I looked up my model here:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

I tried:
options snd-hda-intel model=hp
options snd-hda-intel model=laptop-hp
options snd-hda-intel model=intel8x0
options snd-hda-intel model=hp-dv6736

and some others I forgot. I also tried:
options ac97_quirk=hp_only

But nothing seemed to work. 

charly@lucy:~$ cat /proc/asound/card0/codec#* | grep Codec
**Codec: Conexant CX20549 (Venice)**

I want to phone my girlfriend in Germany, I'm currently living in Japan. I'd be really happy if someone could help me.
Thanks in advance,
chari

---

