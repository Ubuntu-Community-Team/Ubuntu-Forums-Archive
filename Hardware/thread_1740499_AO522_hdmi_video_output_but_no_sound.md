---
title: "AO522 hdmi video output but no sound"
date: 2011-04-27
forum: Hardware
---

### Post by tigrezno on 2011-04-27
Hi, by using xrandr I can get hdmi video output, but still no sound.
Installed pulseaudio and pavucontrol, selected hdmi audio output, sound works as I can see it in the graphic bar of pavucontrol, but can't hear it on TV.

This is an acer aspire one 522

any idea?

people said that by using pulseaudio sound is workin on hdmi, but not mine.

---

### Post by lidex on 2011-04-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by shiftersbox on 2011-04-29
I installed Ubuntu 11.04 on my AO 522. I plugged in the hdmi cable from the netbook to my Samsung TV and selected hdmi audio output. Sound goes out to TV, no configuration needed.

---

### Post by tigrezno on 2011-04-30
ok, i'll try it :)

thanks

---

