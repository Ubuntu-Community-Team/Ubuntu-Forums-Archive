---
title: "TV not detected on Nvidia 8800 GTS! Help!"
date: 2009-01-28
forum: Hardware
---

### Post by aczar on 2009-01-28
Hello,

I have a TV with only a cable input, and therefore must plug my S-Video cable into an RF Modulator to be able to use the TV. The problem is, my Nvidia 8800 GTS doesn't detect the TV because of the Modulator. I tried for endless days to get it working in windows, and thought I would try with Ubuntu (8.10... fully updated, nvidia drivers all installed etc etc). 

no dice. 

I'm pretty new to Linux and have tried everything I know, and have scoured the forums for hours and found nothing useful. 

Please, if anyone knows how to force the S-video to be on... or has any ideas... I will be forever grateful.

---

### Post by aczar on 2009-02-02
If it's worth noting, I had the same problem with my laptop.. but got that working. 
Difference is that the laptop has an ATI card, and I used a combination of the last post in [[COLOR="RoyalBlue"]_this thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=31526") and the following couple of lines to get it working.

```
xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc

```

but again, cant get it working with my Nvidia card on my other machine.

---

