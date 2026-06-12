---
title: "No sound on Dell 1420n with kubuntu 8.04"
date: 2008-07-30
forum: Hardware
---

### Post by tobleron on 2008-07-30
I recently installed kubuntu 8.04 on my Dell 1420n and have had no sound since (none whatsoever). There are several threads related to similar problems, but I haven't really found anything for me. Even the [Dell Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade") was no help (the folder /lib/modules/2.6.24-17-generic/updates
simply doesn't exist; neither does ....-19-generic/updates - see below).

The kernel I'm using is 2.6.24-19-generic, aplay -l gives the following output: 
Karte 0: Intel [HDA Intel], Gerät 0: STAC92xx Analog [STAC92xx Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: STAC92xx Digital [STAC92xx Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

(Karte = card, Gerät = device)

Thanks a lot for any help!

---

### Post by esanchez on 2008-07-30
this one is easy...
just download the latest alsa-driver[1]

then, open a terminal and execute the following commands:

bunzip alsa-driver-1.0.17.tar.bz2
tar -xvf alsa-driver-1.0.17.tar
cd alsa-driver-1.0.17

./configure
make
make install

as a matter in fact I just did this some minutes ago with my Precision M4300.

hope this helps,
Best regards,
 -eduardo s.m.


[1]ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2

---

### Post by tobleron on 2008-07-30
Thanks for the tip. It won't install the driver, however. When I type ./configure, this produces the following:

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

:(

---

