---
title: "is there any one that knows ACER and ALSA... please...."
date: 2010-01-21
forum: Hardware
---

### Post by Danwhelan on 2010-01-21
Running Karmic 9.10

1 - Acer Aspire

2 - The sound was working prior to me playing around... however the mic was not working.... not volume down... not working. 

I followed the following steps 

Download <a href="[ftp://ftp.alsa-project.org/pub/drive...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2")">Alsa drivers v10.0.20

Extracted

Compiled the driver with 
 
./configure
make
sudo make install

Configured alsa-base.conf using sudo gedit - filename 
 Added the following line to the end of /etc/modprobe.d/alsa-base.conf
 
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer

To complete the disaster I rebooted

All this seemed to go off with out a problem.. as in there were no errors that I noticed... however I am from the school of never assume... and I assume that as things are not working that there must have been some sort of error. 

I'm a little worried about un-installing things as the first time I set the system up I have an issue removing some blackberry software and ended up removing the desktop and a whole load of other stuff... 

I've now realised that the version I got wasn't the latest and downloaded the most recent version installed and same. 

Now... now sound.... except in Firefox! Firefox sound is there. 

Which makes it even more annoying. 

GNOME sound shows Dummy Output 0.00db - yet sound in FF 

The sound is actually now working.. however only in firefox. 

Various... 

Alsamixer functions well as a program... but like the labour party actually does nothing... there is no control of the sound at all it's either on full volume or off

Alsa conf - again runs through and picks the sound card... sets it up, says OK... then... no sound still dummy output 

Alsa force-reload produces 

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release. (approx 35 times) 

ALSA mixer - key F4... mic is set to capture in red.. so something is working.... but it's not the Mic 

Mic source only gives me the option of front mic.... on the pre 9.10 versions this was a problem for ACER... since no one has answered a acer mic Q for about 8 months I have to assume that this is still the case. 

Arms up in defeat 

Please there has to be one person out there that knows ALSA 

Best and thanks to anyone that might reply

---

### Post by Danwhelan on 2010-01-21
Short version 

ACER 

UBUNTU 

ALSA 

SOUND NOT WORKING 

HELP!!!!!

(Don't vote green, lab, dim or UKIP) 

:-)

---

### Post by Danwhelan on 2010-01-22
V short version

ALSA... ACER... HELP

---

