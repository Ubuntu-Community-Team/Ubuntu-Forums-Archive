---
title: "ubuntu 9.10, mic with snd_hda_intel (ad198*) and skype"
date: 2009-11-17
forum: Hardware
---

### Post by F43RY on 2009-11-17
Hi everyone. Since I installed ubuntu 9.04 Ive been not able to get mic work correctly on my laptop. I'm a skype user and I'd like to use it with no problem. I think that a bug is present and I'm looking for the fix or just a workaround. My intenral mic and headphones mic don't work any time but just sometimes. In Ubuntu 9.04 I used to reload alsa with the following command:
```

sudo alsa force-reload

```
and skype worked pretty fine. Last week I upgraded to karmic (9.10) and the issue is still present and the above command works no more.  I've tried several solutions but none fix the issue. Can someone of you help me to get through this issue? Here below my configuration:

Ubuntu 9.10 Karmic Koala fresh installation
Laptop HP 6735S
snd chip AD1984A
skype 2.1
module snd_hda_intel with option "model=laptop" added in /etc/modprobe.d/alsa-base.conf to get sound card to work.


Thx for any suggestion and sorry for my bad english

---

