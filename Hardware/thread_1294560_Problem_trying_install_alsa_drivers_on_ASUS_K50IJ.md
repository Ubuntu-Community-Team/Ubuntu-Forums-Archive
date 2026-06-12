---
title: "Problem trying install alsa drivers on ASUS K50IJ"
date: 2009-10-18
forum: Hardware
---

### Post by WestCity on 2009-10-18
Few days ago I bought ASUS K50IJ and installed Ubuntu 9.04 Jaunty. There was no sound after that. I found on this forum how to solve the problem, but i got error. This is code, that I used in terminal:

> wget [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz)
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
./configure --with-cards=hda-intel
make
sudo make install

Why I got error? How else I could fix this no sound issue?

Maybe i have not hda-intel sound card? After I type "aplay -l" it says "aplay: device_list:217: no soundcards found...". Is this normal? My sound card should be built in motherboard.

Sry for bad english. :)

---

### Post by WestCity on 2009-10-18
Ok, here is the code, then I type "./configure --with-cards=hda-intel > ErrorLog.txt":

> ./configure: eval: line 5400: syntax error near unexpected token `)'
./configure: eval: line 5400: `my_compiler_version=4.3.3-5ubuntu4)'
config.status: WARNING:  'Makefile.conf.in' seems to ignore the --datarootdir setting

Any suggestions?

---

### Post by WestCity on 2009-10-24
I solved this problem. I reinstalled Ubuntu 9.04 and finally saw my sound card with command "aplay -l".

1. Updated everything with System -> Administration -> Update Manager.

2. Installed Alsa 1.0.20 (driver, lib, utils).

3. Added 2 extra lines in the end of alsa-base.conf:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
 
 4. Installed hda-verb and added 1 extra line in rc.local just before the line "exit 0":

hda-verb /dev/snd/hwC0D0 0x1c SET_EAPD_BTLENABLE PCM


And sound was working after restart... :) 

Hope, it will help to someone who has similar problems with sound and Alsa drivers on ASUS K50IJ.

---

