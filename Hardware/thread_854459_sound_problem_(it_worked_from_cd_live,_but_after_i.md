---
title: "sound problem (it worked from cd live, but after install its not)"
date: 2008-07-09
forum: Hardware
---

### Post by abc_amjad on 2008-07-09
Hello

I have a problem with sound

sounds work good when running ubuntu cd live
but after install it, no sound :confused:

what's the problem and how to fix it ??

i tried System->Preferences->Sounds options but no result :)

* version used: ubuntu 8.04
* sound card (from lspci):
  Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R)   AC'97 Audio Controller (rev 02)

I have little experience with Linux in general

help me please :)

---

### Post by Vivaldi Gloria on 2008-07-09
Have you tried double clicking the sound icon on the top panel and changing the sliders there?

---

### Post by abc_amjad on 2008-07-10
yes, i tried and no result :(

---

### Post by abc_amjad on 2008-07-12
any help ??

---

### Post by Culsar on 2008-07-22
I have the exact same problem.  Running Ubuntu 8.04 on a Dell Dimension 4600, with Intel 82801EB/ER (ICH5/ICH5R) chipset.  Please post results if you find a solution, and I'll do the same.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

