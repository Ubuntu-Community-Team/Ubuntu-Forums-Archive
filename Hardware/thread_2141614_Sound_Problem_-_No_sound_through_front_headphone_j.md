---
title: "Sound Problem - No sound through front headphone jack"
date: 2013-05-03
forum: Hardware
---

### Post by kanagawaben on 2013-05-03
Hi, new to Ubuntu/Linux as have recently installed Ubuntu 13.04 on my old Gateway GT5042J desktop. Everything seems to be working fine except that I get no sound through my headphones when connecting them to the front headphone jack. In sound settings I see that the output devices changes to headphones and sound stops coming out of the speakers, but no sound comes through the headphones. Not the end of the world but I would like to fix the problem if possible.

---

### Post by Yellow Pasque on 2013-05-03
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by kanagawaben on 2013-05-03
[http://www.alsa-project.org/db/?f=5eeb0ba0a578291569a9021a154d28471eb7e738](http://www.alsa-project.org/db/?f=5eeb0ba0a578291569a9021a154d28471eb7e738)

---

### Post by Yellow Pasque on 2013-05-03
I would try the latest driver, and if it still doesn't work, file a bug: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by kanagawaben on 2013-05-03
Will try the driver, thanks.

---

### Post by kanagawaben on 2013-05-03
The updated driver seems to have solved the problem. Thanks so much!

---

### Post by m1chev on 2013-05-05
Hello,

I have the same issue and updating the drivers did not work for me. Here is my ALSA information.

*[http://www.alsa-project.org/db/?f=8ebf6f3f07c0d284f07ab84b0c830a60045bc991](http://www.alsa-project.org/db/?f=8ebf6f3f07c0d284f07ab84b0c830a60045bc991)*

It would be great if someone can help me with.

Sincerely,

---

### Post by Yellow Pasque on 2013-05-05
@m1chev:
```
Kernel release:    3.8.0-19-generic
```
That means you didn't install the latest driver (or you removed it before getting the information). You'll probably need to keep updating the driver until you have the driver from kernel 3.10, since ALC268 codec support was recently fixed/added: [http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=9992ba72327fa0d8bdc9fb624e80f5cce338a711](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=9992ba72327fa0d8bdc9fb624e80f5cce338a711)

---

