---
title: "Audio snd-hda-intel AND ati hdmi - no output after hdmi"
date: 2009-06-25
forum: Hardware
---

### Post by oliver.greg@gmail.com on 2009-06-25
I have a dell Studio 16, which has an Intel integrated audio, and an ATI HDMI output for video/audio.  The only thing remaining for me to get working perfectly is the HDMI output (I only get video)..  This forces me to infrequently boot into that other OS to get audio and video output from hdmi..

Only drawback is that once I do this and I shutdown windows while still connected to hdmi, the audio output is stuck in hdmi mode for linux and I cannot get audio to play out my normal speakers.  

I try everything I know as far as alsa goes, switching the default outputs, disabling pulseaudio, etc..  Nothing works until I reboot back into windows and play audio out of my internal speakers.  Then I reboot right back into linux and viola!

My alsa config is at:

[http://www.alsa-project.org/db/?f=3937053806b4991ff65ed2596aa3da5a38c03d61](http://www.alsa-project.org/db/?f=3937053806b4991ff65ed2596aa3da5a38c03d61)

It seems something at the hardware level is happening, but I have no idea how to troubleshoot.  If anyone has run across this and found a fix, please let me know..  Better yet, if you know how to get hdmi audio out with the fglrx driver, please let me know..

Using radeon or radeonhd drivers are out of the question since I rely GL 3D apps that either eat too much CPU, or tear if they are too large.

Thanks

-Greg

---

