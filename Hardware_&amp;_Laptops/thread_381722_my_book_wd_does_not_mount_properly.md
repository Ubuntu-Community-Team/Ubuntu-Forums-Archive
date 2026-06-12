---
title: "my book wd does not mount properly"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by naseem on 2007-03-11
hi all!
I bought an external hd my book essential edition 500g. from westewrn digital, when I plug it and switch on it opens nautilus but the window looses control and freeze, moreover all icons in desk t. desappear, when I switch off device, it all goes back to normal, I tried to reed the device with gparted but does not work since whene I switch on it causes lot of troubles in gnome.
I tried it in edgy and feisty and had same result???
please help!!!!

---

### Post by divineleft on 2007-03-11
It may be something wrong with the drive. I have the same hd and it's worked like it should for the last year.

Have you tried mounting it manually? If not, do this:

```

cd ~/
mkdir mybook
sudo mount /dev/<device> mybook

```

where <device> is the mybook partition you want to mount. for me, and probably for you as well, it is sda1.

---

### Post by naseem on 2007-03-11
hi thanks for the fast replie!
I found out that the problem si on the usb hub, when I plug the hd to the case all fine, throught the hub it does not work

---

