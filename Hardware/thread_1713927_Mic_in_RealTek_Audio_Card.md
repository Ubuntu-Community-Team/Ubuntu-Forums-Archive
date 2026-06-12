---
title: "Mic in RealTek Audio Card"
date: 2011-03-24
forum: Hardware
---

### Post by Deersindal on 2011-03-24
I've been having a problem lately while trying to use my microphone with my RealTek271x audio card. I recently bought a new laptop, so I have just tried to use my microphone (which I know works with another computer). I have the gnome alsa mixer, which I am trying to use to tweak the settings for mic boost, volume, etc. After fiddling with the settings for a while, I try to record in audacity, but the only thing I hear is loud static.

My laptop has a built-in mic, but I would like to use my plug-in mic becauswe it is obviously a higher quality mic. The sliders in alsa-mixer are:

Master (Mute tickbox)
Headphon (Mute tickbox)
Speaker (Mute tickbox)
PCM
Front Mi
Mic Boos
Beep (Mute tickbox)
Capture (Rec. tickbox)

Any suggestions about getting my microphone to work? I'll check in windows later if it works to see if the sound card and mic just don't like one another.

---

### Post by lidex on 2011-04-03
Should be your front mic.
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

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

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

