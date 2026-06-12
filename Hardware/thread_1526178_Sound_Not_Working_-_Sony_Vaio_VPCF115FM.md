---
title: "Sound Not Working - Sony Vaio VPCF115FM"
date: 2010-07-07
forum: Hardware
---

### Post by codebyter on 2010-07-07
Hello all!

This is my first post on the Ubuntu forums as I have recently switched over from Windows to Linux. I absolutely LOVE Ubuntu! I have a problem though... I have managed to get sound working but I cannot use my built in microphone. I need some help and am stuck with how to configure it. Anyone know where to start?

Again, I'm still very new to Ubuntu but am familiar with terminal etc.

Thanks for your time!
-CodeByter

---

### Post by lidex on 2010-07-08
OK, misleading thread title...:rolleyes:

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

### Post by codebyter on 2010-07-08
Ok, first off thanks for responding! I fixed the original title I think.

I downloaded the gnome-alsamixer and checked the microphone to make sure it was all the way up and it wasnt muted. The microphone seems likes its detected but is not working. I downloaded Audacity to try recording just in case I was crazy.. Audacity didnt pick anything up either.

Sidenote: In sound preferences, the input tab. There are no connectors showing at all. I have been reading up on other fixes. Some people have been using: 

options snd-hda-intel model=xyz

However, I'm not sure if that's anywhere near what I need to be doing.

Thanks for all the help!

---

### Post by lidex on 2010-07-08
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by codebyter on 2010-07-08
Here is the information that you asked for. I appreciate everything you are helping me with! Thanks so much!

```

codebyter@codebyter-laptop:~$ uname -a
Linux codebyter-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
codebyter@codebyter-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC275 Analog [ALC275 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC275 Digital [ALC275 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
codebyter@codebyter-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-22-generic 2.6.32-22.13                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-2.6.32-23-generic 2.6.32-23.16                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.23.24                                    Backported drivers for alsa-driver snapshot.
codebyter@codebyter-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC275

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GT220 HDMI

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GT220 HDMI

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GT220 HDMI

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GT220 HDMI
codebyter@codebyter-laptop:~$ 


```

---

### Post by lidex on 2010-07-08
Sounds like a pretty sweet machine. The mic issue is addressed here:
[http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone]("http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone")

---

### Post by codebyter on 2010-07-08
That post is great, however I don't know how to apply it to the kernel AND it disables my line in. Does this mean I can use a USB mic still?

When I plugin my USB microphone now, it freezes the entire machine and it seems like PulseAudio stops working. I know the original post was about the built-in microphone, however it seems after reviewing my options and my current dual monitor setup, I will actually need to get my mic working via USB. 

Thanks again!

And ya, this laptop is a BEAST! I love it!

---

### Post by codebyter on 2010-07-10
bump. really need some help with this. Thanks alot :)

---

### Post by codebyter on 2010-07-19
bump.

---

### Post by lidex on 2010-07-19
Scroll down to USB section here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

---

