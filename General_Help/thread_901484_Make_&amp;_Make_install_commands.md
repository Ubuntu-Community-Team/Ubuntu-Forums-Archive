---
title: "Make &amp; Make install commands"
date: 2008-08-26
forum: General Help
---

### Post by zoboraman on 2008-08-26
Hello All,

After using ./configure command, i need to use make ; make install commands to use my E-MU 1616m sound card with 8.04. ./configure command has no problem but when it comes to make i get the following feedback;

root@ubuntu-desk:/usr/src/alsa/alsa-driver-1.0.17# make
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.17'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.17/acore'
copying file alsa-kernel/core/info.c
/usr/src/alsa/alsa-driver-1.0.17/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.17/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.17'
make: *** [include/sndversions.h] Error 2
root@ubuntu-desk:/usr/src/alsa/alsa-driver-1.0.17# 

Of course, there is no use to use make install as make is not working. Does anyone have any idea about what to do?

By the way, i am recompiling alsa drivers, utils, libraries and firmware with the options  "./configure --with-cards=emu10k1 --with-sequencer=yes"

Thank you in advance...

Gokhan

---

### Post by tigercorp on 2008-09-03
Hi, 
I had the same message when following the howto: 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I hadn't installed the 'required tools and kernel headers'. 
After running
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`

the make and make install worked fine.  

Hope it helps.

---

