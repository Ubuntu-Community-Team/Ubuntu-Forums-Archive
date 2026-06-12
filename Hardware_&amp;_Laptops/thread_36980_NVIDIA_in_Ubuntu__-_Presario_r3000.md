---
title: "NVIDIA in Ubuntu ? - Presario r3000"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by ::DoGG:: on 2005-05-25
I couldn`t find anywhere info about the drivers that comes with Ubuntu. if someone knows, please let me know is it a nv basic driver  or the nvidia.o driver that can handle hardware 3d acceleration and nonstandard resolutions (important for me since i have widescreen lcd on my laptop). I`m asking cause i read on thi forum that couple guys get 1280x800 without messing with any additionall driver installation jus out of a box - if that`s true.. damn Ubuntu is good :D ( installing NV on Debina amd64 is a pain, taht`s why i want to migrate to ubuntu 64 bit release)

---

### Post by cdhotfire on 2005-05-25
```

$ sudo apt-get install nvidia-glx
$ sudo /etc/init.d/gdm stop
$ sudo dpkg-reconfigure xserver-xorg

```

then choose nvidia, not nv, and continue through setup and u should up to a resolution selector, choose the highest resolution you want.  After this your pretty much set, for all your questions.:)

---

### Post by vladanian on 2005-05-25
I run Ubuntu on 64 -- the distro comes with the nv driver, which works fine, but for 3D you can get the nvidia driver through apt.  The instructions are here: [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by vladanian on 2005-05-25
Looks like you beat me to the punch...

---

### Post by cdhotfire on 2005-05-25
WOW!!!!!!!!!!!!!!!!
AT THE EXACT TIME.

Hey, ill give u a point also.;-)

---

### Post by Seti on 2005-05-25
Thanks for the info!! \\:D/

---

### Post by cdhotfire on 2005-05-25
Anytime.:)

---

### Post by ::DoGG:: on 2005-05-26
Thanks guys.  Drinks are on me :D

---

### Post by cdhotfire on 2005-05-26
[QUOTE=::DoGG::]Thanks guys.  Drinks are on me :D[/QUOTE]

Nice.:)

---

