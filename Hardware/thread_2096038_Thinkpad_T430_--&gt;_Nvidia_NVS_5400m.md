---
title: "Thinkpad T430 --&gt; Nvidia NVS 5400m"
date: 2012-12-18
forum: Hardware
---

### Post by Piro24 on 2012-12-18
Just wondering if anyone has had success using the NVS 5400m graphics card that's included in the Thinkpad T430 alonside Intel's integrated graphics.

I just spent the last half hour or so recovering from an Xorg disaster when I tried to install nvidia-current and hope for the best (stuck at 640x480 resolution :0 ). If anyone has a quick "howto"  or some suggestions/links it'd be much appreciated.

It'd be nice not to have to reboot into Windows just to play some games. 
Thanks!

---

### Post by typhoon_tip on 2012-12-18
If you don't want to use the Intel card, just set in the BIOS to use discrete card only, and then install nvidia-current. Remember to run sudo nvidia-xconfig after installing the driver or it won't reboot correctly (somehow is not creating the correct X configuration after install). If possible, use commands to install nvidia-current (sudo apt-get install nvidia-current).

If you want to use Intel and switching capabilities, then you have to use Bumblebee.

---

### Post by Piro24 on 2012-12-19
> **typhoon_tip said:**
> If you don't want to use the Intel card, just set in the BIOS to use discrete card only, and then install nvidia-current. Remember to run sudo nvidia-xconfig after installing the driver or it won't reboot correctly (somehow is not creating the correct X configuration after install). If possible, use commands to install nvidia-current (sudo apt-get install nvidia-current).

If you want to use Intel and switching capabilities, then you have to use Bumblebee.

I tried installing and using Bumblebee after my first go-round with nvidia-current and nvidia-xconfig, however, it didn't seem to have any effect whatsoever, so I just uninstalled everything and reverted to my original configuration.

I'm going to give Bumblebee another shot and report back.

---

### Post by Piro24 on 2012-12-20
So, after giving Bumblebee another go, everything seems to be going well!

Framerate in several games I have tried isn't quite as good as under Windows, but still quite good. 

For anyone wondering, this is how to force the discrete card.

> $ optirun [options] <application> [application-parameters] 

Further reading here:
[https://wiki.ubuntu.com/Bumblebee#Installation]("https://wiki.ubuntu.com/Bumblebee#Installation")

---

