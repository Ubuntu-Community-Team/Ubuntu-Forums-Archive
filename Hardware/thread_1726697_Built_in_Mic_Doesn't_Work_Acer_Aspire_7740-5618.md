---
title: "Built in Mic Doesn't Work Acer Aspire 7740-5618"
date: 2011-04-11
forum: Hardware
---

### Post by vbartolotta on 2011-04-11
I've been searching for a solution for my built in microphone problem. Can't record a thing using Sound Recorder. The mic works fine when I boot in Windows 7. I've tried various remedies suggested in the forum to no avail.

Thanks in advance for any suggestions you may have.

This information may be of help:

victor@victor-laptop:~$ uname -a

Linux victor-laptop 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

victor@victor-laptop:~$ arecord -l

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


victor@victor-laptop:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

victor@victor-laptop:~$ cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.21.

victor@victor-laptop:~$ head -n 1 /proc/asound/card*/codec#*

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 670

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

Victor B

---

