---
title: "Help with Realtek ALC680"
date: 2010-04-03
forum: Hardware
---

### Post by mk360 on 2010-04-03
Hi...

I regularly read this forum to find solutions to my problems, but this is my first message, becouse one of the problems are my spanish ;)... but well, now I can't find solutions, only other people with the same problem, so I'll try to explain...

I installed ubuntu lucid (yes, is beta, but I'm testing from the alfa versions and all works correctly, so I'm using it) in a hp pc (I don't remember the model but I can find for this if is needed) all the installation proces worked fine and apparently the system hardware works without any problem (on windows I had to install too many drivers, so I think ubuntu is working fine) but the sound card was detected and sounds really low, the sound card model is Realtec ALC680.

as it is said I installed ubuntu lucid, but I've the same problem with stable versions, so I think that is not the problem... Also, I find on internet and aparently many people has the same problem.

I downloaded drivers from realtek's home page but it requires the compilation of alsa drivers and some modifications to important files (I think) and obviously it sounds complicated to me... however, I'm finding for other solutions (dev packages?) and if I need to install the driver some instructions, becouse all other things are working correctly.

These are the instructions of the readme file:

The source code copy from [www.alsa-project.org](www.alsa-project.org). ver:5.14
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203
====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC259
ALC269
ALC270
ALC272
ALC275
ALC660
ALC660VD
ALC661
ALC662
ALC663
ALC665
ALC670
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A
ALC892
Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 
Automatic install: (Recommend RedHat distribution)
execute
./install
Note: Ubuntu OS, please use manual install.
Run commands need to add sudo at first words. 
Manual install:
Step 1. unzip source code
tar xfvj alsa-driver-1.0.xx.tar.bz2
Step 2. Turn on sound support from kernel config 
(soundcore module, default turn on)
Step 3. Complied source code
a. cd alsa-driver-1.0.xx
b. ./configure (--with-cards=hda-intel)<= for HDA options
c. make
d. make install
e. alsaconf
Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
(Please refer to the attached modules.conf)

snd-xxxx is the card ID.
-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
--- Intel ICH6 ICH7 ---------
snd-hda-intel
-- AC97 controller --ALC655 ALC650 ALC250 ALC255
--- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
snd-intel8x0
--- Via8233 Via686a ------------------------------- 
snd-via82xx
--- ATI Chipset -------------------------------
snd-atiixp
Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-xxxx 
# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
Step 5. reboot your machine
Step 6. Use the alsamixer the disable mute (All audio line default is mute)
Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
excute alsamixer
Note: 1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
2. Kernel Version must be 2.6 or later.
3. All mixer channels are muted by default. You must use a native
or OSS mixer program to unmute appropriate channels.
4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
5. The driver added to support the SPDIF functoin. 
6. a. You can download the alsa-lib-1.0.x and alsa-utils-1.0.x form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
b. Suggest use "alsamixer" to control mixer function.
c. Used "alsaconf" can autodetect which drive you need to install (step 4). 
7. SUSE Distribution must install the ncurses package. 
 
Regards,
mk.

---

