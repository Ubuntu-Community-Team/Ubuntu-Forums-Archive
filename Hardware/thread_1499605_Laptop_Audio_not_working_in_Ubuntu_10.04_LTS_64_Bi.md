---
title: "Laptop Audio not working in Ubuntu 10.04 LTS 64 Bit Edition"
date: 2010-06-02
forum: Hardware
---

### Post by unreal_avarice on 2010-06-02
I have Ubuntu 10.04 LTS - 64 Bit Edition running on a** Sony Vaio  VPCEB12fx.**
From my understanding it has a **Realtek High Definition Audio Card** in it.

This will help profile my system a bit better, read from other forums...

For the** uname -a **command:
```
Linux gregory 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

```

For the** aplay -l **command:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

For the** cat /proc/asound/version** command:
```
Advanced Linux Sound Architecture Driver Version 1.0.21.

```

For the **head -n 1 /proc/asound/card*/codec#*** command:
```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

```

This was a clean install of Ubuntu 10.04 LTS 64 Bit Edition

Thanks in advance,
Greg

---

### Post by lidex on 2010-06-02
These sony's seem to respond well to an alsa upgrade. Follow the alsa-upgrade link in my sig.

---

### Post by unreal_avarice on 2010-06-03
This solved the problem.
I thank you for helping me with this greatly.

---

### Post by lidex on 2010-06-04
Awesome. Please mark the thread as solved using 'Thread Tools' up top.

---

### Post by lsanchezpacheco on 2010-07-14
WOW men thank you very much, SOLVED PROBLEM :D

---

