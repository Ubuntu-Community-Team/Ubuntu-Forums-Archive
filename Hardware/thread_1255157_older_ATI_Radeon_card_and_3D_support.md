---
title: "older ATI Radeon card and 3D support"
date: 2009-09-01
forum: Hardware
---

### Post by Megatron3000 on 2009-09-01
Hello,  i am a very new Ubuntu user, and have a graphic card problem (apart from that, everything seems to be running smoothly). My card is an ATI Radeon Mobility HD 2600, and with the default driver (Xorg, i suppose), i get no 3D support, which makes some things not as smooth as i want them to (rounded corners look quite bad, no shadows, sometimes i get trails when dragging a window...).  I tried the proprietary driver, but after installing that my system won't start up anymore (apparently it is not made for this card). I haven't found any solid suggestion on the net (apart from maybe the Xorg Ati driver), and since i'm not such a fluent terminal writer yet, i don't want to risk rescuing my system in text mode just yet.  Does anyone have a suggestion? Thanks!  I run Jaunty 9.04 on a Toshiba Sattelite H200 1H2, with an Intel DuoCore 1,66GHz processor and 2046 MB RAM

---

### Post by Megatron3000 on 2009-09-01
oh, and it doesn't have to be too fancy, i'm not into wild gaming. just enabling slightly less spartan looks would be sweet

---

### Post by Megatron3000 on 2009-09-03
anyone?

---

### Post by automaton26 on 2009-09-03
There's someone [here]("http://ubuntuforums.org/showthread.php?t=1256855") with your computer specification, trying to get proprietary drivers working.

They got them working by using the "Hardware Drivers" option and rebooting, so it should be quite straightforward.

---

### Post by Megatron3000 on 2009-09-03
thanks! i got it working in my normal kernel, though i had to arrange the 'aticonfig --initial' and the xorg xserver in recovery mode before my display would work. it also messed up the realtime kernel, which won't even start in recovery mode now. still, sweet to have some better graphics.

---

