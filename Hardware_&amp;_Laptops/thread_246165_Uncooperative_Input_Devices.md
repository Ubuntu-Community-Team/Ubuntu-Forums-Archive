---
title: "Uncooperative Input Devices"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by manitoba98 on 2006-08-28
I installed, in late June/early July, Dapper Drake 6.06. It worked fine, even Xgl/Compiz! Now, whenever I boot into Ubuntu (or even off the CD), it absolutely ignores my input devices. I have a PS/2 keyboard and USB optical mouse. During the "Mounting root filesystem" startup stage, the keyboard begins being ignored (although the Numlock light stays on), and the mouse goes dark. Here is my hardware configuration (nothing is/was overclocked):

AMD Sempron 2600+
1GB DDR RAM (was 512MB at the time of install, but has been failing since before the upgrade)
60GB hda ( dedicated to Windows :( )
120GB hdb ( various storage partition, also home to Ubuntu. boot device )
Nvidia GeForce FX 5200 (128MB, AGP)
DVD Writer

WHY DOES UBUNTU DO THIS TO ME? Can anyone help? Please? :(

---

### Post by Omnios on 2006-08-28
Try using 
```
sudo dpkg-reconfigure xserver-xorg
```

 This is a turtle type graphics config program for xserver wich will allow you to manually set or auto detect your monitor keyboard and mouse. From what you said a update probably broke your set up.
The set up file can also be accessed with
```
sudo gedit /etc/X11/xorg.conf
```

---

