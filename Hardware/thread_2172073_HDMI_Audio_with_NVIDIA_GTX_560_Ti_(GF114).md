---
title: "HDMI Audio with NVIDIA GTX 560 Ti (GF114)"
date: 2013-09-03
forum: Hardware
---

### Post by glide2 on 2013-09-03
Nvidia HDMI audio is a widely asked topic, but I've not been able to find the answer for my case.

Card displayed by `lspci`

```

$ lspci | grep NIVIDIA
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)

```

Device displayed by `aplay`

```

$ aplay -l
...
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

All outputs unmuted by `alsamixer`

[IMG]http://i.stack.imgur.com/3OPJf.png[/IMG]

But the card does not appear in the Sound controller from System settings.

[IMG]http://i.stack.imgur.com/Kost5.png[/IMG]

I'm currently using "nvidia-325" driver, but I tried "nouveau" and several other versions

My HDMI output is detected to be `/proc/asound/card2/eld#1.0`

```

$ cat /proc/asound/card2/eld#1.0
monitor_present     1
eld_valid           1
monitor_name        DENON-AVAMP
 
connection_type     HDMI
...

```

`speaker-test` does not find the device

```

$ speaker-test -c 2 -r 48000 -D hw:2,3

speaker-test 1.0.25

Playback device is hw:2,7
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -19,No such device

```

Can someone help me with my problem ? Or at least tell me why doesn't my device appear on sound settings ?

---

### Post by glide2 on 2013-09-05
Nobody here ?
Question too complex ?

---

### Post by TiberiusT on 2013-11-22
Hi Glide2...hope you're still watching :)

Did yu get this working? I am thinking of buying a GTX 560 Ti for a multiseat setup but I must have 2 separate audio outputs on the graphics card, which, from your aplay -l yu seem to have.  

Can u confirm?

TIA
T

---

