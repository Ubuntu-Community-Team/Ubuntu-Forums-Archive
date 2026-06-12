---
title: "GeForce 7500 LE and driver 304.135"
date: 2017-07-06
forum: Hardware
---

### Post by aispobla on 2017-07-06
When I install the driver nvidia 304.135 from restricted drivers or terminal, it is installed, but the result is bad:

[ATTACH=CONFIG]275888[/ATTACH]

No icons, only the cursor is moved, and not open nothing. I have try with nomodeset and also ppa:graphics-drivers/ppa, bad not work. After of click and any icon, it freeze.

SO Ubuntu 16.04, 64bit, with unity.

Any idea?

---

### Post by oldfred on 2017-07-06
Often the open source driver just works with the older nVidia cards. The open source driver is usually a couple of versions behind on features so nVidia driver usually required with newer nVidia cards.

My 620Gt works well with nouveau. I did on one install add the nVidia driver, but did not notice any difference. You may then need nomodeset.

To purge:
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by aispobla on 2017-07-06
Thanks oldfred, with nouveau yes work, but the performance is poor, the windows are moved a bit slow, and unity search is very slow, that is the reason by I want install driver nvidia.

---

### Post by oldfred on 2017-07-06
May not be video driver?

How much RAM?
My old laptop with 1.5GB of RAM and Intel video was very slow with Unity, but then I install fallback which made it very usuable. 
Most suggest Lubuntu, Xubuntu or one of the other lightweight flavors.

---

### Post by aispobla on 2017-07-07
I have 4GB

---

