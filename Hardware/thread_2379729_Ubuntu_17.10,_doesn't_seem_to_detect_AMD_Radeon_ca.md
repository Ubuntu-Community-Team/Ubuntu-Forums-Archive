---
title: "Ubuntu 17.10, doesn't seem to detect AMD Radeon card"
date: 2017-12-08
forum: Hardware
---

### Post by mistcloud-misty on 2017-12-08
Hello all. I just got 17.10 installed on my new Lenovo y520. It is the one that uses the AMD radeon, rx560 card. Unfortunately my laptop doesn't seem to even be aware of it - I have checked the additional hardware and there are no drivers. Terminal output is:

```
arcane@arcane-Lenovo-Y520-15IKBA:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)

```

I mean it is functioning fine with just the Intel graphics, but I would like to get use of the AMD.

Unfortunately I am not sure if the lack of graphics detection is due to my error during installation, in which I received that "force UEFI" thing which I chickened out on and installed it under Legacy BIOS. Unfortunately windows was, indeed, under UEFI and now I can only boot into Ubuntu if I select the Legacy option under BIOS. Not a big deal, I just switch to UEFI when I want Windows... but maybe it could be the reason I don't see the graphics card?

Any advice would be appreciated. I would want to avoid reinstalling under UEFI if possible.

Unless I used the wrong command, I'm not sure what to do about finding it.

---

