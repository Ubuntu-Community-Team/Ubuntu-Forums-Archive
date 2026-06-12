---
title: "Problem with Microphone"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by apollo13 on 2007-02-18
I bought myself an Asus G1 Laptop.
Everything is working fine except the microphone.
It is an internal microphone and the device is a Intel "82801G (ICH7 Family) High Definition Audio Controller".
When I try to record something (using system->sound->test) I only hear rumbling noises. No problem I thought and plugged in my external microphone, but it looks like the internal one is not deactivated. Any ideas how to solve this issue?

Tell which data you need...
Thx in advance
apollo13

---

### Post by solar george on 2007-02-18
Could you actually record from the external microphone. If not you probably need to adjust some settings in the volume control. What program are you using to record?

---

### Post by mikewhatever on 2007-02-18
Had exactly the same issue. If you can't fix it any other way 
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

---

### Post by apollo13 on 2007-02-18
Nope I couldn't, it seemed as if the external one wasn't activated cause of the active internal...
And Volume is 100% not muted etc....

EDIT:// @mikewhatever thx I'll look through it

EDIT:// The link didn't help cause it is just the microphone which doesn't work

---

### Post by sureinlux on 2007-02-18
Apparently there a bug in ALSA (pre 1.0.13 versions) which cause trouble with the headphone jack. The 1.0.13 version fixes this problem though and can be downloaded from [here]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2").

Compile and install it. Create a "sound" file in the [FONT="Courier New"]/etc/modprobe.d[/FONT] folder. Open this file and add :
```
options snd-hda-intel index=0 disable_msi=1
```

p.s. by default the volume is muted.

---

### Post by apollo13 on 2007-02-18
Sh.. I rebootet after compiling and installing and now my system does not boot anymore, tells me something like /usr/sbin/modprobe exited abnormally :(

---

### Post by apollo13 on 2007-02-18
I think I'll wait for Feisty, cause I don't use my microphone often....

---

### Post by mikewhatever on 2007-02-18
Sorry it didn't work for you. This Intel audio stuff is so irregular. I've seen others having their mics not working. Still others have no sound, or the speakers are not muted when the headphones are in. In my case, I think the driver did not detect the hardware, because after recompilation, I got more functions in volume controls and a separate function for internal and external mics. Hope it does work in Feisty.

---

