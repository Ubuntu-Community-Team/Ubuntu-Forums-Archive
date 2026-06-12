---
title: "USB Headset AudioFX 5+1 Pro doesn't work"
date: 2010-04-11
forum: Hardware
---

### Post by proxess on 2010-04-11
I've had this headset for a while now, has a bunch of nice features like virtual 5.1 and stuff like that. Problem is, in Ubuntu and Xubuntu (the variants I've tried it on), only the microphone works. Also how do I make use of the virtual 5.1 when I get it working??

Edit: The headset's microphone works.

---

### Post by lidex on 2010-04-11
Can you post the output of these terminal commands please:

```
aplay -l
head -n 1 /proc/asound/card*/codec#* 
```

---

### Post by proxess on 2010-04-12
I got the headset to work by changing the volume directly with alsamixer. Weird eh.


Here's the output of those commands:
```
proxess@PRXSS-Laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
proxess@PRXSS-Laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: ATI R6xx HDMI

==> /proc/asound/card1/codec#0 <==
Codec: Realtek ALC272

==> /proc/asound/card1/codec#1 <==
Codec: LSI ID 1040
proxess@PRXSS-Laptop:~$ 

```


Still no virtual 5.1. Also my login sound comes out of the laptop speakers. How do I change that behavior?

---

### Post by proxess on 2010-04-13
*bump*

---

### Post by lidex on 2010-04-13
You said it's virtual, do you need 5.1 output or just 2? What is your status now - do your speakers work? Do you have headphone output of any type?

---

### Post by proxess on 2010-04-14
> **lidex said:**
> You said it's virtual, do you need 5.1 output or just 2? What is your status now - do your speakers work? Do you have headphone output of any type?

My headset now works, I have analog output. Yes I kind of need my virtual 5.1 output for me gamez0r.

---

### Post by proxess on 2010-04-20
6 Days? *bump*

---

### Post by Cerealklr on 2010-08-26
eDimensional FX 5+1 Pro, same issue. Toying around gives me a 4.1 surround option, but its analog and therefore is definitely not working. *bumpbumpbump*

I'm not afraid to get dirty in source code if I need to, but I'd greatly appreciate a little more information if anyone has it.

---

### Post by Zargar on 2010-09-29
I have the same problem, I'd really love a solution!!!

---

### Post by cyb3rkn19ht on 2011-01-18
Here is my output from the above console commands. I also have annoying popping in the headset.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC262 Digital [ALC262 Digital]
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
card 2: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC262

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GPU 10 HDMI/DP

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GPU 10 HDMI/DP

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GPU 10 HDMI/DP

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GPU 10 HDMI/DP

```

---

