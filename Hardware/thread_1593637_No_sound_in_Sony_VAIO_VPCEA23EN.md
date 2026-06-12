---
title: "No sound in Sony VAIO VPCEA23EN"
date: 2010-10-11
forum: Hardware
---

### Post by schbonn on 2010-10-11
I'm somewhat a newbie to Linux. I recently bought a Sony VAIO notebook model VPCEA23EN. I installed Ubuntu 10.04 Lucid. Everything seems to go fine but there is no sound whatsoever from the speakers or from the headphones. The sound works very well in Windows 7 though.

The command, cat /proc/asound/card0/codec#* | grep Codec, outputs Realtek ALC269 and I edited the /etc/modprobe.d/alsa-base.conf file, but in vain.

Can anyone please help me?

---

### Post by ufkazim on 2010-10-26
> **schbonn said:**
> I'm somewhat a newbie to Linux. I recently bought a Sony VAIO notebook model VPCEA23EN. I installed Ubuntu 10.04 Lucid. Everything seems to go fine but there is no sound whatsoever from the speakers or from the headphones. The sound works very well in Windows 7 though.

The command, cat /proc/asound/card0/codec#* | grep Codec, outputs Realtek ALC269 and I edited the /etc/modprobe.d/alsa-base.conf file, but in vain.

Can anyone please help me?

refer this link for more [http://ubuntuforums.org/archive/index.php/t-1449001.html](http://ubuntuforums.org/archive/index.php/t-1449001.html)

and the solution is

1. sudo apt-get install build-essential
2. wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
3. tar -xjf alsa-driver-1.0.23.tar.bz2
4. cd alsa-driver-1.0.23/
5. ./configure
6. make
7. sudo make install
8. alsamixer (don't know if this step was necessary since my volume was already enabled)
9. reboot

Sound should now work...!

..........................................................................
...................................................................
..............................................................

also please mark it as SOLVED.

---

### Post by schbonn on 2010-10-26
Wow...that was cool. The sound now perfectly works. Thank you!

---

