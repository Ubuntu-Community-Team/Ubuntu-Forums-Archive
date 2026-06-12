---
title: "HPG2t Help: Speakers don't work"
date: 2010-08-05
forum: Hardware
---

### Post by ezm on 2010-08-05
I am trying to get Ubuntu 10.04 to work on my new HPG62t.  Most things work well, but the sound is not right.  The headphones work, but not the speakers.  I have tried pretty  much every setting int he gnome alsa manager.  Here is the output of 'aplay -l': 

[INDENT]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/INDENT]

Does anyone have any idea what might be going on here?  Any help would be greatly appreciated.

---

### Post by lidex on 2010-08-06
Can you post the output of these terminal commands for me please:
```
uname -a
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by ezm on 2010-08-06
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

My laptop is an HP G62t-250.  Here you go (and thanks for the help!): 

```

ethan@extremophile-ubuntu:~$ uname -a
Linux extremophile-ubuntu 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
ethan@extremophile-ubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-driver-linuxant                  1.0.18.0                                        ALSA driver enhanced for Conexant HDA modem 
ii  alsa-oss                              1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ethan@extremophile-ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 270

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
ethan@extremophile-ubuntu:~$ 

```

---

### Post by ezm on 2010-08-06
I think I've managed to solve this problem.  At least for the moment, my speakers are working.  What I did was install the drivers from the realtek site.  Specifically, the Unix driver on their page for High Def Audio Codecs.  Here's the link: 

[INDENT][http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownType](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownType)  ID=3&GetDown=false[/INDENT]

I downloaded the tar ball, unpacked it, and followed the instructions in the file Readme.txt.  I had previously installed the packages necessary for compiling I think ("build-essential").  I rebooted once and it still didn't work but then I noticed my gnome-alsamixer was missing, so I reinstalled that, and then on reboot the speakers began to work.  Hopefully, it stays that way.

---

### Post by lidex on 2010-08-06
I imagine it would, at least until a kernel upgrade.

---

