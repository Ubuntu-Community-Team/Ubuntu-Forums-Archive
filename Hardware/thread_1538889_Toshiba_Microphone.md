---
title: "Toshiba Microphone"
date: 2010-07-25
forum: Hardware
---

### Post by nrbdw55 on 2010-07-25
i cannot get ubuntu to pick up my mic. i do not want to go back to windows.help me pleeeeeeease:popcorn:

---

### Post by lidex on 2010-07-26
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

Then use pulseaudio volume control (pavucontrol) or 'Sound Preferences' to select and unmute your mic in 'Input Devices' tab.

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

### Post by georgeen on 2010-07-27
Hello, well I had the same problem until today, I installed a Pulse Audio Applet and in volume control option in input devices tab I selected show all input devices, so appear the device that doesn't work. If it doesn't appear is a matter of drivers.

 If appear:
- go to recording tab
- open sound recorder application from sound and audio applications menu and try to record something. The application appear now in the applet as an application that is using the recording system in that moment you can select from a button in the recording tab the source of audio
- select another one else than the default and continue recording some seconds more in sound recorder app.
- After your testing you can playback that you try record from the sound recorder application, if you in some point listen your voice that's the device you have to choose when skype is running in order to others listen you.
- Start Skype and go to testing call with the applet opened and choose the device that really works. That's it.

Bye I expect that this help you and others with the same problem.

JQ

---

### Post by nrbdw55 on 2010-07-28
hello georgeen. where do i get this applet from. thanks

---

### Post by lidex on 2010-07-28
> **nrbdw55 said:**
> hello georgeen. where do i get this applet from. thanks

If not installed already (Applications>Sound & Video>Sound Recorder)
```
sudo apt-get install gnome-media
```

---

### Post by nrbdw55 on 2010-07-28
hello again. tried the above but nothing worked. please do not forget i am a total noob but i love this os

---

