---
title: "No sound on MSI EX610 (after some fix)"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by NuSuey on 2008-03-13
Got no Sound after ..

> Method B: Manually build alsa-modules (1.0.15-rc1 only)
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2)
tar xvpjf alsa-driver-1.0.15rc1.tar.bz2
cd alsa-driver-1.0.15rc1
./configure --with-cards=hda-intel
make
sudo make install

would like to restore it back.. or whatever..

the sound worked before this, but the headphones, speaker ..didnt mute .. when one has been used..

thanks in advance for any suggestions..

---

### Post by superprash2003 on 2008-03-13
this may help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

