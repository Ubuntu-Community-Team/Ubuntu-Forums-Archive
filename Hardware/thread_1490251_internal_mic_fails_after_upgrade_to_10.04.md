---
title: "internal mic fails after upgrade to 10.04"
date: 2010-05-22
forum: Hardware
---

### Post by phorminx on 2010-05-22
After upgrading from ubuntu 8.10 to 10.04, the only thing that does not work (anymore) is the internal microphone of my laptop.

For capture alsamixer lets me choose between "mic" and "internal mic". Well, I want to use the internal mic, so I toggle capture such that it refers to "internal mic". But then the Sound Preferences application tells me something different. Here, the only input device I can choose from is "Internal Audio Analog Stereo". Is this again my internal mic? Well, when I choose "internal mic" within alsamixer, "Sound preferences" says that I've muted the input (presumably input from "Internal Audio Analog Stereo" which is the only input device known to Sound Preferences -- it would be helpful if these two applications used the same lingo). So I remove the mute tickmark in sound preferences, and alsamixer responds by toggling the capture from "internal mic" to "mic". It appears as if these two applications do not quite agree with each other on which input devices I have and how they can be accessed.

Needless to say that up to now the (internal) mic does not work.

I also tried to recycle my old asound.state (from before the upgrade to 10.04) using alsactl. But somehow this does not work either. Too bad! 

-- Any suggestions on how to fix this are appreciated.

---

### Post by lidex on 2010-05-23
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.

Then use pulseaudio volume control (pavucontrol), input devices tab, to select mic.

---

### Post by phorminx on 2010-05-23
Thanks for your help!
> **lidex said:**
> Try gnome-alsamixer.
**[Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
This says that the internal mic is selected. It doesn't offer a possibility to adjust levels.
> **lidex said:**
> Then use pulseaudio volume control (pavucontrol), input devices tab, to select mic.
No matter what I select in pavucontrol, when I try to record something with the sound recorder, this will change the settings in alsamixer to "mic" (instead of internal mic). But this will not record anything (except overamplified noise).
In the meanwhile, I realized that there are quite a few reports on bugs.launchpad.net reporting similar difficulties, see, e.g.,
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/571294](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/571294)

---

### Post by lidex on 2010-05-23
Try this to remove cruft:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

Next update alsa to 1.0.23 via the alsa-upgrade link in my sig

---

