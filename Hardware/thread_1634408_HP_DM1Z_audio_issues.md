---
title: "HP DM1Z audio issues"
date: 2010-11-30
forum: Hardware
---

### Post by Shaneiffer on 2010-11-30
Hello all, I am really in some need of help with the audio on my HP DM1Z-2000.  The netbook is the base configuration that is listed on the website with the exception of the processor, which I upgraded to the AMD dual core K625.  Shortly after I got the netbook, I changed over to Ubuntu netbook edition 10.04LTS (Lucid).
The issues that I am about to describe to you I did not initially have regularly, but they have increased in frequency to the point that they happen consistently every time I try to use the audio features of the netbook.
The issues are these:
1) the audio jack/speakers do not change over with out manual setting.  To elaborate: when I want to switch over from the speakers to headphones, the jack will not automatically pick up, instead it will play music through both the headphones AND the speakers.  To change this I must go through the System->Sounds options and manually set the output.  
Don't know if it matters or not, but there are two pieces of hardware listed in the Sound Preferences dialog box, under the Hardware tab: first is "Internal Audio, Output/1 Input, Analog Stereo Dubplex; second is "RS880 Audio Device [Radeon HD 4200}, 1 Output, Digital Stereo (HDMI) Output".  I currently have it set to the Internal Audio option with the Analog Stereo Duplex setting.
2) the microphone jack will not pick up at all, either by use of plugged in jack mic, or non-jack mic.

I am a relative newb, so somewhat unfamiliar with how everything in Linux works (I was bored with Windows and wanted something new to learn, figured Linux was that opportunity), but can definitely copy/paste codes in the terminal/follow directions.  Thanks in advance for any help offered!

Shane

---

### Post by rummy77 on 2010-11-30
On my last HP laptop, I had problems with the audio after every update.  Every time, I would re-install ALSA, which usually fixed the problem.  You might try following the steps [here]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/") and see if that solves any issues.

---

### Post by Shaneiffer on 2010-11-30
Actually, in the end, this problem ended up being much mroe simple to fix than all that.  I only had to OPEN Alsamixer in the Terminal and set the levels to where I wanted them and change the mic over to the line in option.  LOL...after all that frustration, it was so easy.  Thanks to all who helped (here or elsewhere)  :)

Shane

---

