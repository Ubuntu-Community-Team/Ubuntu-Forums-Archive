---
title: "Wacom Bamboo Touch &amp; Pen CTH-460/K driver needed"
date: 2010-08-04
forum: Hardware
---

### Post by tomynho on 2010-08-04
Hello everyone. I finally uninstalled Windows, because I'm not going to use it anymore, but I have a problem - my tablet doesn't work out-of-box. I tried using this:

```

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6-1.tar.bz2

tar -xf linuxwacom-0.8.6-1.tar.bz2
cd linuxwacom-0.8.6-1
./configure --enable-wacom
cd src/2.6.30/
make
sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
sudo rmmod wacom
sudo modprobe wacom
```

but these packages doesn't exist anymore so this code can't be used. Isn't there any compiled .deb driver for this?
Or any WORKING and pretty easy guide? :D I didn't find any solution for this & I need this as fast as possible, please.
Oh, I'm using Ubuntu 10.04 Lucid Lynx 32-bit.

Thanks! :)

---

### Post by Favux on 2010-08-04
Hi tomynho,

Please see the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

