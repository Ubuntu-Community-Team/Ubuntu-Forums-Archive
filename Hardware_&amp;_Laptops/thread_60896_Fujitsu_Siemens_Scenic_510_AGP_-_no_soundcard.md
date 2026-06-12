---
title: "Fujitsu Siemens Scenic 510 AGP - no soundcard"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by Assembly on 2005-08-29
Hello! 
First im sorry to my english.

I have notebook Fujitsu Simens Scenic 510 AGP , 
Ubuntu don't see my soundcards (NeoMagic Magicmedia 256 AV) 
Im add to /etc/modules snd-nm256 
when system starting i have info. when modules loading 

nm256 - no AC 97 found 
force the parametr to load by passing in the modules force_ac=1

my   **lsmod |grep snd** is:
snd_nm256       
snd_ac97_codec 
snd_pcm_oss  
snd_mixer_oss 
snd_pcm
snd_timer
snd_page_alloc
snd
soundcore

and when ALSA start up i have comand 

 Invalid card number     amixer <options> command   

im instaling alsa driver 1.09 form this page [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Neomagic&card=MagicMedia+256AV.&chip=NM2200&module=nm256](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Neomagic&card=MagicMedia+256AV.&chip=NM2200&module=nm256) but im used this comand 

./configure --with-cards=nm256 --with-sequencer=yes;make;make install

and stop in 

...
Checking for kernel version ... The file /usr/src/linux/include/linux/version.h does not exist
Please install the pacage with full kernel sources for your distribution or use --with-kernel=dir option to specify another directory with kernel sources (default is /usr/src/linux). 

im find page [http://www.linuxfreunde.de/marl/mobile510/mobile510.html](http://www.linuxfreunde.de/marl/mobile510/mobile510.html) 

what I can install this driver "ad1848" & "adlib_card" (WSS) work fine, full-duplex to oss and alsa  CS4231 Sounddriver ?? 

thx so much for helping me ..

im newbie ...

---

