---
title: "Eee PC 1021PN No Sound"
date: 2010-07-19
forum: Hardware
---

### Post by baseline on 2010-07-19
Hi,

I've just installed UNR Lucyd on my brand new Asus 1021PN (ION2 platform).
Everything is in working order except for sound. Both input and output produce no result whatsoever...
Can anyone help me with this? I know it's a fairly recent hardware spec...

Cheers,

---

### Post by baseline on 2010-07-20
Small update... By enabling "proposed updates" on the aptitude sources I now have sound output but still no mic support.
Any ideas guys and gals? I would really hate having to go back to Windows7...

Cheers,

---

### Post by lidex on 2010-07-20
I would really hate for you to have to go back to windows7 also ;)
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

### Post by baseline on 2010-07-21
Hi lidex,

Thanks for the feedback.
Bellow is the output you requested:

```
neta@Elvis:~$ uname -a
Linux Elvis 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
```

```
neta@Elvis:~$ aplay -l
**** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: Intel [HDA Intel], dispositivo 0: ALC269 Analog [ALC269 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

```
neta@Elvis:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                      1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA
```

```
neta@Elvis:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID b

```


Cheers,

---

### Post by lidex on 2010-07-21
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=lifebook 
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

### Post by baseline on 2010-07-22
Hi,

After reboot I get two possible Mic selections:
[LIST]
[*]Mic
[*]Internal Mic
[/LIST]

I tried every combination I could think of: mute one, unmute the other, with Mic boost, whithout, etc. All I'm able to get is a lot of white noite whenever I use "sound capture".

Cheers,

---

### Post by Erdosain on 2010-07-22
i am having a similar (wouldn't say EXACTLY the same, since I have not tried out my mic yet) on an Eee PC 1015. I have tried every combination that seemed successful for lower model number, to no results. Actually, I just recently got the speakers to go silent when the headphone jack is plugged in by putting "model=asus-mode4" on alsa-base.conf. But the headphones still do not play any music.
I'd be grateful for any ideas.
Thanks!

---

### Post by lidex on 2010-07-22
> **baseline said:**
> Hi,

After reboot I get two possible Mic selections:
[LIST]
[*]Mic
[*]Internal Mic
[/LIST]

I tried every combination I could think of: mute one, unmute the other, with Mic boost, whithout, etc. All I'm able to get is a lot of white noite whenever I use "sound capture".

Cheers,

OK. Remove that option line. Next follow the alsa-upgrade link in my sig to get v. 1.0.23

---

### Post by baseline on 2010-07-23
Hi lidex,

UPgrading Alsa and inserting the line ```
options snd-hda-intel model=auto
``` on alsa-base.conf did the trick.
Thanks a bunch ;)

Cheers,

---

