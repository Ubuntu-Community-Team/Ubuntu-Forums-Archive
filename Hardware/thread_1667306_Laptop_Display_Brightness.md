---
title: "Laptop Display Brightness"
date: 2011-01-14
forum: Hardware
---

### Post by Thucydides411 on 2011-01-14
I'm running 64-bit Ubuntu 10.10 on an Asus G53JW with an Nvidia GeForce GTX 460M graphics card.

I noticed while running the laptop on battery power that the screen was not dimming at all, which is clearly less than optimal. Investigating further, I found that although my function keys seem to be bound correctly, i.e. the brightness indicator changes when I press to dim/brighten the screen, the screen's brightness does not change as desired. Instead, the screen seems to take on random brightness settings when I try to adjust the brightness. The observed brightness normally changes two or three times nearly instantly when I press to dim or brighten the screen, although the indicator changes as it should.

I've tried two workarounds, with no success. The first was to add the following line to the device section of /etc/X11/xorg.conf:
Option "RegistryDwords" "EnableBrightnessControl=1"

That was suggested [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1474511&page=3").

The second workaround was to uncheck "PowerMizer Monitor" in the NVIDIA X Server Settings.

Neither of these seemed to have an effect. I've retained the altered xorg.conf file, but now reactivated the "PowerMizer Monitor."

I've also updated my driver from the standard "nvidia-current" (260.19.04) to the 260.19.29 driver from the repository ppa:ubuntu-x-swat/x-updates.

It would be really helpful to get this sorted out, since it would allow me to use my laptop away from a power source for longer periods of time.

Thanks in advance.

---

### Post by pwabrahams on 2011-01-15
I have an Asus K60IJ laptop running Kubuntu 10.10, and I too have been trying unsuccessfully to adjust the screen brightness.  There's an adjustment for brightness in the Battery Monitor, but alas, it doesn't seem to do anything.

I noticed the excessive brightness a short time ago. I also saw some kind of calibration bar popping up in the lower center of the screen, but I can't control when it appears or change its setting.  The logo on it is of a screen, so it might be relevant.

The keyboard has a Fn key and according to the manual the combination Fn-F4 is supposed to reduce the brightness, but that doesn't do anything either.

---

### Post by Thucydides411 on 2011-01-17
Still not resolved... Bump.

---

### Post by artistajose on 2011-01-20
Same problem with the brightness control on the ASUS G53JW-SZ144V (Ubuntu 10.10 64, Nvidia Driver 260.19.06).
 Also I have only sound through headphones. (00:1 B.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)).

---

### Post by artistajose on 2011-01-20
Same problem with the brightness control on the ASUS G53JW-SZ144V (Ubuntu 10.10 64, Nvidia Driver 260.19.06).
 Also I have only sound through headphones. (00:1 B.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)).

---

### Post by artistajose on 2011-01-20
Same problem with the brightness control on the ASUS G53JW-SZ144V (Ubuntu 10.10 64, Nvidia Driver 260.19.06).
 Also I have only sound through headphones. (00:1 B.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)).

---

### Post by artistajose on 2011-01-20
Same problem with the brightness control on the ASUS G53JW-SZ144V (Ubuntu 10.10 64, Nvidia Driver 260.19.06).
Also I have only sound through headphones. (00:1 B.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)).

---

### Post by Thucydides411 on 2011-02-01
bump

---

### Post by clayt0njknight on 2011-02-11
I've got an Asus K60IJ as well.  

[http://art.ubuntuforums.org/showthread.php?t=1605498](http://art.ubuntuforums.org/showthread.php?t=1605498)


this worked like a charm for me.

---

