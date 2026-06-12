---
title: "HDA Generic Sound Card Issues"
date: 2010-07-25
forum: Hardware
---

### Post by Goveynetcom on 2010-07-25
I have been trying over and over trying to get my sound card to work.
I have tried most of the settings here:
[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto"]```
https://help.ubuntu.com/community/HdaIntelSoundHowto
```[/URL]
And no luck.
The codec command reveals this:
```

Codec: Intel G45 DEVCTG

```I really need help with this, it's frustrating when my sound stops working, or it doesn't detect I plugged in headphones, it just outputs though both.... My HDMI sound output works fine though.

This is my only issue with Ubuntu. I'll do whatever it takes to get this working!

*weeps and hopes for help :(*

---

### Post by lidex on 2010-07-25
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

### Post by Goveynetcom on 2010-08-03
Sorry that it has been a week, I left the day I posted it.
uname -a:
```

Linux chris-laptop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

```

aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

dpkg -l | grep "alsa"
```

ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library

```

head -n 1 /proc/asound/card*/codec#*
```

==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5067

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG

```

The model of my laptop is HP G60.

---

### Post by lidex on 2010-08-03
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Goveynetcom on 2010-08-10
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.
Still not working. Haven't had my sound glitch out lately. But it's still no detecting that I have headphones plugged in. It just outputs through both.

---

### Post by lidex on 2010-08-11
Try updating your alsa install. Use the link in my sig.

---

