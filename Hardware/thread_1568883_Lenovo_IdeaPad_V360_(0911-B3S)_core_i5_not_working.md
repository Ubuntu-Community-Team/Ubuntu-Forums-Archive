---
title: "Lenovo IdeaPad V360 (0911-B3S) core i5 not working intel integrated video properly"
date: 2010-09-06
forum: Hardware
---

### Post by Fredy Gamez on 2010-09-06
Lenovo IdeaPad V360 (0911-B3S) not working video properly in ubuntu 10.04.
(Intel Core i5-520M (3M Cache, 2.40 GHz) with  intel integrated graphics. 3GB RAM, 500GB HDD)

                 I am relatively new in Ubuntu, and I  got this Lenovo core i5. I want to replace fully  Windows 7 but start Ubuntu in graphic mode has been a headache to install Ubuntu due to this  issue. Although I am running right now Ubuntu, the video resolution is  poor.
 . I tried Ubuntu 10.04 and  the beta version of 10.10, still the same problem. Temporally I could  start the video in 1)VESA in the Xorg driver, and 2)passing  in the  kernel parameter "nomodeset" each time I boot my computer. It allows me a  resolution of 1024x768, in basic mode (I mean, no extras in video  effects).
 I tried to install intel driver (xserver-xorg-video-intel) with all updated versions, but problem remains.
 I tested different alternatives from liveCDs, and the results at date  (Sept2010) are:
- Lubuntu 10.04 LiveCD: Starts LXDE only with the F6 parameter for safe graphics nomodeset
- Ubuntu 10.04 LiveCD: Starts with F6 selecting parameter nomodeset , and adding in the line  i915.modeset=0
- Ubuntu 10.10 LiveCD: Starts with F6 selecting parameter nomodeset , and adding in the line  i915.modeset=0
 Alternatively, I use an external monitor, and i can boot with a  kernel parameter "i915.modeset=1", and the external monitor takes full  resolution, but the laptop screen remains blank (no images at all).

        

Please help!!!

---

### Post by Fredy Gamez on 2010-09-09
Any suggestion, I have no any progress with the bug with the intel video. Still I can have full featured video, only the vesa option.

---

### Post by piperon on 2010-09-21
> **Fredy Gamez said:**
> Any suggestion, I have no any progress with the bug with the intel video. Still I can have full featured video, only the vesa option.

Same problem here, it´s a Lenovo V360 core i5 520m with integrated Intel GMA HD graphics and HM55 chipset, i tried several distros with same results...

---

### Post by luisremis on 2011-03-13
same problem. v360 core i3 intel graphics.

i install ubuntu with a minitor (VGA), but can't make it work in the main diplay

any ideas?

---

### Post by piperon on 2011-04-14
Finally LCD it´s working with Ubuntu Nanny 32b beta 1, GPU acceleration seems to be working to. :D

---

