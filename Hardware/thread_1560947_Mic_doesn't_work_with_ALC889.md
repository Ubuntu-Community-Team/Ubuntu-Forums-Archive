---
title: "Mic doesn't work with ALC889"
date: 2010-08-25
forum: Hardware
---

### Post by Scifer on 2010-08-25
Hello. I have a H55M-E33 MSI motherboard witch sound device is Realtek ALC889 (8 channels). The problem is when I unmute the MIC in Kubuntu Lucid Lynx KMix it plays no microphone sound but a awful squeak. I have no idea what it might be. Can anyone help me?
```
/proc/asound$ cat cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbef4000 irq 22
 1 [camera         ]: USB-Audio - USB camera
                      USB camera at usb-0000:00:1a.0-1.4, full speed
``````
/proc/asound$ cat version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

---

### Post by lidex on 2010-08-25
It might be feedback. Are you monitoring the mic through your speakers?

---

### Post by Scifer on 2010-08-26
> **lidex said:**
> It might be feedback. Are you monitoring the mic through your speakers?
I use only headphone and the MIC sounds different from feedback noise. It sounds more like something completely offline. It doesn't capture any sound neither.

---

### Post by lidex on 2010-08-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by Scifer on 2010-08-27
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Enter your user password when prompted. Choose the upload option and provide a link for the output.
[http://www.alsa-project.org/db/?f=d98b8be43cd7427d7c775d2709f3f193e3321da6](http://www.alsa-project.org/db/?f=d98b8be43cd7427d7c775d2709f3f193e3321da6)

---

### Post by lidex on 2010-08-27
Is this an internal or external mic? Looks like you need to enable some settings in alsamixer.
First try adding a model quirk in alsa-base.conf. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=targa-8ch-dig 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by Scifer on 2010-08-28
> **lidex said:**
> Is this an internal or external mic? Looks like you need to enable some settings in alsamixer.
First try adding a model quirk in alsa-base.conf. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=targa-8ch-dig 
```Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
The only difference that I noticed was a lower mic noise and now headphone channel muting makes effect.
By the way. Why targa model?

---

### Post by lidex on 2010-08-28
Try upgrading your alsa install to v 1.0.23. Use the link in my sig.

---

### Post by Scifer on 2010-08-28
I decided to buy a new headset and guess what? It worked. What a shame.
I'm very grateful for you help Lidex.
Thanks a lot!

---

