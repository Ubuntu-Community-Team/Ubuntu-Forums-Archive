---
title: "Thinkpad T21 Kubuntu - no mixer and no sound"
date: 2008-07-22
forum: Hardware
---

### Post by Der_Idiot on 2008-07-22
I have a thinkpad T21 and there's no mixer available and no sound at all. I already installed alsa-mixer-gui and when I load it, I get the same error I get form alsamixer:

```
alsamixer: function snd_ctl_open failed for default: no such file or directory
```

When I reload alsa, I get:

```
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```

When I look for multimedia devices, I get:

```
lspci | grep Multimedia
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
```


Any ideas? I really need sound out of this, as my main PC got owned by lightning.

Thanks!

---

### Post by Der_Idiot on 2008-07-22
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Best thread ever. I love this forum.

I swear, I did two days of googling and in 5 minutes time I come up with that :lolflag:

---

