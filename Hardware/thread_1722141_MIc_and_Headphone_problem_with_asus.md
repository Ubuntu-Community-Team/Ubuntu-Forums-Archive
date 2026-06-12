---
title: "MIc and Headphone problem with asus"
date: 2011-04-05
forum: Hardware
---

### Post by mannyv14 on 2011-04-05
Hi, I recently installed ubuntu 10.10 using wubi on my laptop, Asus Notebook U50 series intel core i3 4gb ram 64 bit system, everything was working fine until I tried listening to music, I would put in my headphones but the built in speakers would continue to work while no sound was coming from my headphones, and my built in microphone refuses to work also. I have spent many hours trying to search for a solution but have not found one, any help would be appreciated

---

### Post by lidex on 2011-04-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mannyv14 on 2011-04-05
here is the link [http://www.alsa-project.org/db/?f=7cf10abe6ab9ed8e779887d8bf80cba136f8bad4](http://www.alsa-project.org/db/?f=7cf10abe6ab9ed8e779887d8bf80cba136f8bad4)

---

### Post by lidex on 2011-04-05
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by mannyv14 on 2011-04-05
that fixed the headphone problem thank you:D, but i still cant use my built in microphone

---

### Post by lidex on 2011-04-06
Run this command and post the output:
```
amixer
```

---

### Post by mannyv14 on 2011-04-07
here ya go:
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 33 [45%] [-41.00dB] [on]
  Front Right: Playback 33 [45%] [-41.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 251 [98%] [0.80dB]
  Front Right: Playback 251 [98%] [0.80dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [off]
  Front Right: Capture 80 [100%] [6.00dB] [off]
Simple mixer control 'Analog Mic Boost',0
  Capabilities: cenum
  Items: '0dB' '10dB' '20dB' '30dB' '40dB'
  Item0: '0dB'

---

### Post by lidex on 2011-04-07
Run alsamixer and unmute your capture switch. You may also need to turn up the 'analog mic boost'

---

### Post by mahenkpatel on 2011-04-07
Please if somebody could take a look at my issue here

[http://ubuntuforums.org/showthread.php?p=10648213#post10648213](http://ubuntuforums.org/showthread.php?p=10648213#post10648213)

There is no sound from my laptop:(

---

### Post by mannyv14 on 2011-04-07
i did all you told me but my mic still does not work

---

### Post by lidex on 2011-04-08
> **mannyv14 said:**
> i did all you told me but my mic still does not work

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

