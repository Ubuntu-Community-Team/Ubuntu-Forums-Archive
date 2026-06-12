---
title: "Please help me with my Modeline"
date: 2010-03-06
forum: Hardware
---

### Post by finster on 2010-03-06
Hi all,

I'm having problems getting my PC to connect to my Sharp LC-32AD5E 32" TV. The display isn't auto-recognised, I've also tried moninfo on Windows with no luck whatsoever.

The specs of the TV from the manual for using the VGA input are supposedly: -

[LIST]
[*]VGA - 640×480, 31.5 kHz Horiz Freq, 60 Hz Vert Freq
[*]SVGA - 800×600, 37.9 kHz Horiz Freq, 60 Hz Vert Freq
[*]XGA - 1024×768, 48.4 kHz Horiz Freq, 60 Hz Vert Freq
[*]WXGA - 1280×768, 47.7 kHz Horiz Freq, 60 Hz Vert Freq
[*]WXGA - 1280×768, 48.1 kHz Horiz Freq, 60 Hz Vert Freq
[*]WXGA - 1360×768, 47.7 kHz Horiz Freq, 60 Hz Vert Freq
[/LIST]

I've managed to X running at 1360x768 using both of the following modelines that I found for similar TV's (obviously using one at a time), but I am getting quite a lot of flickering...

```
  Modeline "1360x768_60.00"  85.50  1360 1424 1536 1792  768 771 776 794  -hsync -vsync
  Modeline "1360x768_60.00"  85.431  1360 1424 1536 1792  768 771 777 795  -hsync -vsync
```

(I don't really understand these numbers to be honest.) 

The system is going to be used solely as a media centre. Would using one of the lower resolutions be a safer bet (although I'll probably have the same issue in trying to get a valid modeline).

Anybody got any ideas?

Thanks.

---

