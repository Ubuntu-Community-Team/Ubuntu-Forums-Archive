---
title: "Yet more 915 resolution problems"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by EV1CR8R on 2007-05-13
Greetings 
I have a gateway widescreen  laptop which has an i915 chip and  uses 1280X800 resolution in winxp.
Much like others I cannot change my resolution from 1024x768 in feisty. As Ned Flanders father said we've tried nothin and we are out of ideas. I have installed 915resolution changed mode 30 to 1280x800 32 bit and set that as default in 915resolution I have reconfigured xorg to use 1280X800 , but I still have no other option than 1024X768 in gdm and kde. I am using the i810 drivers not vesa. any help would be greatly appreciated, missed steps in setting up 915resolution or some such mistake.
Please help this is the only thing hold me back from complete windows independence.

---

### Post by endersshadow on 2007-05-13
Try this:

```
sudo apt-get remove 915resolution
sudo apt-get install xserver-xorg-video-intel
```

Restart X or just restart your computer, and you should be all set.

---

### Post by EV1CR8R on 2007-05-13
Awesome
Thank you so much. It works perfectly now. :)

---

### Post by wabunka on 2007-05-14
> **endersshadow said:**
> Try this:

```
sudo apt-get remove 915resolution
sudo apt-get install xserver-xorg-video-intel
```

Restart X or just restart your computer, and you should be all set.

i would like to say thank you too :KS :KS :KS 

this solve my problem with the Intel 954GM with the
dell, now i could use the 1680 x 1050 resolution, so
much space now... :lolflag: :lolflag: :lolflag:

---

