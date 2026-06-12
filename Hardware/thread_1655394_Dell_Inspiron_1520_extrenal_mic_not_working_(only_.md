---
title: "Dell Inspiron 1520 extrenal mic not working (only internal)"
date: 2010-12-29
forum: Hardware
---

### Post by sherbieny on 2010-12-29
The external mic isn't working only the internal is working and it wouldn't shut off


info:

uname -a:

Linux sherbieny-Inspiron-1520 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version:

Advanced Linux Sound Architecture Driver Version 1.0.23.


head -n 1 /proc/asound/card*/codec#*:

==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9205

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

I got alsomixer but at the mic tab there are lineIn or Mic

which is for the external mic (a normal plugin not usb mic)?

---

### Post by lidex on 2010-12-30
Let me know how this goes. 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m44 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by sherbieny on 2010-12-31
I did what you said,

Alsa Mixer has three sound card choises (-Default,0 HDA-Intel, enter device name)

should I choose HDA or leave it to Default

also the "sound" panel has those configuration(please find attachments)

---

### Post by lidex on 2010-12-31
Should be the same.

---

### Post by sherbieny on 2010-12-31
well, nothing changed so any ideas :)

---

### Post by lidex on 2010-12-31
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


Also see this:
[http://ubuntuforums.org/showpost.php?p=3845885&postcount=4](http://ubuntuforums.org/showpost.php?p=3845885&postcount=4)

---

### Post by sherbieny on 2010-12-31
well, I don't know If I didn't get it or something

I got the alsa-mixer and the pavucontrol but nothing happened and I can't which option is concerned with the internal mic and which is for the external mic (from the mic plugin)
I only have (micIN and lineIN) 
I need to close the internal and open the external  pleaseeeeee

---

### Post by lidex on 2010-12-31
Can you post a screenshot of alsamixer? Press F4 to show capture devices first.

---

### Post by LeonLinux on 2011-01-13
hi, i have same problem with same model exactly %100

---

