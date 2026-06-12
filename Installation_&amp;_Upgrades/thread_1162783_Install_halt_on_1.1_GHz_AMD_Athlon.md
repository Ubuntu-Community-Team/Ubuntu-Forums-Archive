---
title: "Install halt on 1.1 GHz AMD Athlon"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by russb on 2009-05-18
I had very good luck this weekend when I installed xubuntu on an ancient Dell Inspiron 3500 laptop. (After experimenting with D___ Small Linux, Puppy, and xubunto 8.04 and 9.04, I settled on 8.10).
 
Since I was on a roll, I attempted to install xubuntu 8.10 on a homebrew 1100 MHz AMD Athlon desktop PC with an AMI BIOS dated 2000. The motherboard contains no silk-screen or etched markings that would indicate manufacturer or model number. A utility program claims that it's an Elitegroup motherboard. This PC until recently ran Windows XP. 
 
The install and live startup process halted after a couple minutes, while displaying the xubunti splash screen. Both xubuntu 8.04 and 9.04 halted similarly.
 
Does this problem sound familiar? Should I be thinking in terms of BIOS update, or video card problems, or something else, please?
 
Thanks.
[http://russbellew.com](http://russbellew.com)

---

### Post by Brian88 on 2009-05-18
> **russb said:**
> I had very good luck this weekend when I installed xubuntu on an ancient Dell Inspiron 3500 laptop. (After experimenting with D___ Small Linux, Puppy, and xubunto 8.04 and 9.04, I settled on 8.10).
 
Since I was on a roll, I attempted to install xubuntu 8.10 on a homebrew 1100 MHz AMD Athlon desktop PC with an AMI BIOS dated 2000. The motherboard contains no silk-screen or etched markings that would indicate manufacturer or model number. A utility program claims that it's an Elitegroup motherboard. This PC until recently ran Windows XP. 
 
The install and live startup process halted after a couple minutes, while displaying the xubunti splash screen. Both xubuntu 8.04 and 9.04 halted similarly.
 
Does this problem sound familiar? Should I be thinking in terms of BIOS update, or video card problems, or something else, please?
 
Thanks.
[http://russbellew.com](http://russbellew.com)

You could install the minimal Ubuntu by downloading this image :
```
https://help.ubuntu.com/community/Installation/MinimalCD
```
and then you could burn it into CD. For your AMD, just choose the 32-bit version.

After you finished installing the minimal Ubuntu, install the X server and GUI (XFCE) using the apt-get.

---

### Post by russb on 2009-05-20
Thanks. I'll give this a try.
 
Does xubuntu / ubuntu have trouble with AMD Athlon CPUs?
 
Regards,
Russ
[http://russbellew.com](http://russbellew.com)

---

