---
title: "Soundcard not working"
date: 2013-11-11
forum: Hardware
---

### Post by oozaru on 2013-11-11
Hi, I have a computer with a soundcard that I can't find drivers for. It originally had windows xp on and I put Ubuntu 12.04 on it. The sound card is a Sound Blaster PCI 128 CT4700, does anyone know of any drivers that might work for this soundcard?

thanks

---

### Post by Yellow Pasque on 2013-11-11
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by oozaru on 2013-11-11
ok but what am I supposed to do with that?... sorry I'm a noob

---

### Post by Yellow Pasque on 2013-11-12
You're supposed to read it, enter (copy/paste) the two commands and give us a link to your audio information.

---

### Post by oozaru on 2013-11-12
oh... ok [http://www.alsa-project.org/db/?f=85739554a6ac1881042fdd772658823a117cfec7](http://www.alsa-project.org/db/?f=85739554a6ac1881042fdd772658823a117cfec7)

---

### Post by Yellow Pasque on 2013-11-12
It looks like ALSA kernel modules are not loading. I guess this is a result of something you did to "fix" the issue?
```
Driver version:     
Library version:    1.0.25
Utilities version:  1.0.25
```

Try reinstalling kernel image:
```
sudo apt-get install linux-image-`uname -r`
```

>  I can't find drivers
The drivers are built into the kernel. It's an Ensoniq ES1370 chip (Creative purchased Ensoniq because it was putting out good products and Creative hates competition).
The module is named snd-ens1370

---

### Post by oozaru on 2013-11-14
I ran the code but it didn't work, just said it was the newest version

---

### Post by oozaru on 2013-11-14
Ok nevermind. The computer was for my father in-law and he decided to just buy a new soundcard, which works. Thanks for the help though.

---

