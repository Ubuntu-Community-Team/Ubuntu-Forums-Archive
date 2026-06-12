---
title: "Enabling the build-in microphone on a Lenovo T61P"
date: 2010-07-05
forum: Hardware
---

### Post by edgue on 2010-07-05
Hello there,

my Thinkpad has a build-in microphone; and in my good old Windows days I could that when making software based phone calls (not perfect; but
good enough to hear other people on the speaker and talk to them).

Now, with Linux, I couldnt find any profile for the internal sound
card that would allow me to then select it as input. There is an
"analog duplex", but when i select that ... i still cant use the internal
mic.

(I attached a screenshot of the sound preferences).

Any idea?

---

### Post by lidex on 2010-07-05
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

