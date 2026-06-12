---
title: "G555 sound issue"
date: 2010-07-08
forum: Hardware
---

### Post by Mitchell Hale on 2010-07-08
I bought a Lenovo G555 and installed Ubuntu on it. It works great, save for one problem, the sound card. I still get sound through the speakers, and the headphone ports work, however, when I plug in headphones the speakers do not turn off. Both the headphones and speakers continue to produce sound. The computer does not even recognize headphones are plugged in. Can anyone give me a solution or point me to a driver? (already tried Googling it so don't be one of those jerks who just says "Google!" and inserts a grinning emoticon)

Oh, if it helps the sound card is a conexant.

Thanks!

---

### Post by lidex on 2010-07-09
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

### Post by Mitchell Hale on 2010-07-13
```
mitchell@mitchell-laptop:~$ uname -a
Linux mitchell-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
mitchell@mitchell-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mitchell@mitchell-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                                         ALSA driver configuration files
ii  alsa-firmware                         1.0.20-0medibuntu4.1                                           Contains firmware for ALSA devices - Medibun
ii  alsa-firmware-loaders                 1.0.22-0ubuntu1                                                ALSA software loaders for specific hardware
ii  alsa-tools                            1.0.22-0ubuntu1                                                Console based ALSA utilities for specific ha
ii  alsa-utils                            1.0.22-0ubuntu5                                                ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                                  Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                                      GStreamer plugin for ALSA
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                               SoX alsa format I/O library
mitchell@mitchell-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Conexant ID 5069

```

Got this back from term.

Laptop's a Lenovo G555

---

### Post by lidex on 2010-07-13
Try this for me please.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes 
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

### Post by Mitchell Hale on 2010-07-14
Nothing. Still refuses to even acknowledge headphones are there. And only one soundcard shows up so I don't think I have the wrong one selected.

---

### Post by lidex on 2010-07-14
Try these drivers for conexant audio chips. Make sure to download the correct version.
[http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")

---

### Post by Mitchell Hale on 2010-07-20
> **lidex said:**
> Try these drivers for conexant audio chips. Make sure to download the correct version.
[http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")
Which one? I tried the one that seemed right (the .deb on that page) and nothing.

---

### Post by p2ranger on 2010-07-27
I also recently got a  Lenovo g555 and put 10.04 on it. I am trying to get a headset to work for voice chat and ran into the same problem. Audio still comes out of the pc speakers and the pc mic is still picking up causing feedback. I've tried all of the options suggested in this thread except for the new driver. Have you gotten it to work yet when you plug into the jack?

I opened up the alsa mixer and didn't have much sucess, wasn't quite sure what I'm looking at.

Thanks

Jason

---

