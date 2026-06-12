---
title: "Internal microphone not recognized: Gateway LT21 netbook"
date: 2010-07-06
forum: Hardware
---

### Post by llehsadam on 2010-07-06
I got the Gateway lt2110u netbook and installed Ubuntu 10.04 LTS. Everything actually worked out-of-the-box except for the internal microphone. I cannot make Skype calls or even simply record my voice. In Sound Preferences under the input tab, the audio level remains zero for the mic. I know the microphone is not broken because it works fine under Windows 7. When I attach an external mic, the external mic does work under Ubuntu. 

Any suggestions? Fixes? Please help! :cry:

---

### Post by lidex on 2010-07-07
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by rvndrk3233 on 2010-09-29
I have found there is a drop down menu you missed.
The apps are fine on default install.Check the PulseAudio configureation menu pages.Apparently there are a few dropdown menus.

Make sure you have DUPLEX audio enabled or mic jack wont work. internal mic, not so sure.took me a few minutes and a usb/1 8th inch headset to figure this out.

cheesy video2lin device works as intended.

---

### Post by llehsadam on 2010-10-14
Thanks guys!

I was traveling for the past few months and I decided to ignore the issue as I attached a little external microphone to my netbook to make Skype calls on.

I looked into the issue again and found other people with the same issue. Some of them could solve the problem the way described above, and some of them I now solved the problem by removing pulseaudio. I decided to remove pulseaudio... furthermore I decided to experiment with other distros that did not have pulseaudio as a sound server and everything worked better than expected.

I tried using the pulseaudio manager, but there were not that many options to choose from in the menus for the netbook... I never had problems with sound before Ubuntu brought in pulseaudio as default so...

I did what was posted [here]("http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html").

I don't think the issue in itself is solved though and when I  tried my luck with Ubuntu 10.10, the issue was still there. I am now actually using CrunchBang which doesn't implement pulseaudio, but I may try something else since I have time to experiment.

---

