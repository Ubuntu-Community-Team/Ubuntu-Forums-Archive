---
title: "Toshiba T135 Conexant Microphone Issues"
date: 2010-08-16
forum: Hardware
---

### Post by Dynelight on 2010-08-16
Hello. I installed Ubuntu 10.04 and it works beautifully on my Toshiba T135. 
However, my microphone doesn't seem to work.
Any help trying to get this to work will clearly be appretiated, as it's what's keeping me from using Ubuntu as my main O/S.

---

### Post by Dynelight on 2010-08-19
No one got it to work here?

---

### Post by lidex on 2010-08-19
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by Dynelight on 2010-08-19
Done. Reported. Did all that wiki says.

---

### Post by lidex on 2010-08-19
*Dynelight*
Can you post the link to the bug report please?

---

### Post by Dynelight on 2010-08-20
[https://bugs.launchpad.net/bugs/620843](https://bugs.launchpad.net/bugs/620843)

---

### Post by lidex on 2010-08-20
Three things you can try.
1) BIOS update
2) ALSA upgrade (the link in my sig)
3) Inserting a model option in alsa-base.conf:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-vostro 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by Dynelight on 2010-08-22
I tried all of that... nothing...

---

### Post by lidex on 2010-08-23
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

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

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

