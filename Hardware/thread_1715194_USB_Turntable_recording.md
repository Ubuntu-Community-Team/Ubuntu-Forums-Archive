---
title: "USB Turntable recording"
date: 2011-03-26
forum: Hardware
---

### Post by funk71 on 2011-03-26
Ciao,
I'm trying to record some LP through a USB phono preamp (HAMA PA-005) with Audacity sw. I'm using Ubuntu 10.10. And now the problem: with older releases of ubuntu I was able to record, setting properly the playback/record devices in the audacity control panel. Now I can't do it anymore. The soundcard is integrated in the mobo, and I have no other problems with audio performance. I also installed jack, connecting all the "captures" to all the "playback". No way to record a sound. Any help is highly appreciated, since it seems I can record only with windows...[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
Ciao

---

### Post by prshah on 2011-03-26
> **funk71 said:**
> playback/record devices in the audacity control panel. Now I 

Since 10.04, there is no direct alsa access (normally). All sound is routed through the pulseaudio server (service).

Check your input device: Right-Click the volume control applet, and choose "Sound preferences"; open the "Hardware" tab and ensure that you have atleast one input device (may be combined as a singe input/output device). Then, click the "Input" tab, and "choose" the relevant input device (Eg, your USB device). Start playing your USB device, unmute the input and adjust volume until the sound meter registers sound.

if you run into problem, please post back with screenshot of the Sound preferences window, Input tab.

---

### Post by funk71 on 2011-03-27
Thanks for the reply.
I modified the sound preferences settings:
- hardware : internal, analog stereo duplex;
- input: USB headset analog stereo, connector: analog microphone (unmuted, 100% input volume).
I tried all the available combinations as input/output in audacity but it still doesn't work.
Please find attached a picture of the settings (sorry, but it's in italian).
Ciao

---

### Post by funk71 on 2011-03-28
Any new idea?
I'm trying many settings without success...
Thanks

Ciao

---

