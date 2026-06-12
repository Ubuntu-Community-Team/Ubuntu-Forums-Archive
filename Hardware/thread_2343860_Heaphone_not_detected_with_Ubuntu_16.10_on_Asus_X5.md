---
title: "Heaphone not detected with Ubuntu 16.10 on Asus X555UB"
date: 2016-11-20
forum: Hardware
---

### Post by italomaia on 2016-11-20
Hello. I've just installed ubuntu-gnome 16.10 on my asus x555ub. It has a nvidia 940M on it. When I plug my headphone on it, it does not recognize it nor 
changes audio output to it. I tried a few tricks listed in the internet like the one suggested by Michael here [http://askubuntu.com/questions/132440/headphone-jack-not-working](http://askubuntu.com/questions/132440/headphone-jack-not-working), 
removing and creating **.config/pulse/** and activating the headphone through alsamixer with no success. **pavucontrol** also lists my headphone as unplugged (when plugged).
Any suggestions on how to fix this?

---

### Post by Yellow Pasque on 2016-11-20
Please give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by italomaia on 2016-11-20
There you go [http://www.alsa-project.org/db/?f=fa7931bc9e8f858ea9e1c9802f4abc81a8455f22](http://www.alsa-project.org/db/?f=fa7931bc9e8f858ea9e1c9802f4abc81a8455f22)

---

### Post by Yellow Pasque on 2016-11-20
Not much help, I'm afraid, but other owners of this laptop have reported the issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1598571](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1598571)

---

### Post by italomaia on 2016-11-21
Thanks. Temüjin, it is good to know I'm not alone.

---

