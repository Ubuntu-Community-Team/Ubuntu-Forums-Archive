---
title: "HP G62-144dx - Audio and Video problems"
date: 2010-07-10
forum: Hardware
---

### Post by tcamolesi on 2010-07-10
I recently bought a HP G62-144DX notebook and I can't seem to get neither audio or video drivers working properly. 
I'm running Kubuntu 10.04 and I'm not able to turn Desktop effects on (using opengl for compositing) and there are no proprietary drivers available (this notebook uses an Intel HD Graphics adapter). After googling for help, it seems that the issues with this graphics adapter was supposedly solved in the latest release of ubuntu, so I don't really know what to do.

About the audio problem, I'm not able to get any sound output at all. After running:
```
cat /proc/asound/card0/codec#* | grep Codec
```I get:
```
Codec: Realtek ID 270
Codec: Intel G45 DEVIBX
```But I don't really know how to proceed from here, this thread: [http://ubuntuforums.org/showthread.php?t=1465133](http://ubuntuforums.org/showthread.php?t=1465133) suggests that I might have to update alsa, is that the only possible way to get the audio to work ?

UPDATE: I managed to get the sound working by updating alsa to .23, using this script: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) But I still haven't solved the video issue

---

### Post by tcamolesi on 2010-07-10
It seems that the driver I'm currently using doesn't have opengl support, that's why I can't enable desktop effects.
Trying to run glxdemo yields:
```
Xlib:  extension "GLX" missing on display ":0.0".
```
Does anybody know how I'm aupposed to solve this issue ?

---

### Post by lidex on 2010-07-10
Can you provide these outputs:
```
lspci -nn | grep VGA
sudo lshw -C display
cat /var/log/Xorg.0.log
```

---

