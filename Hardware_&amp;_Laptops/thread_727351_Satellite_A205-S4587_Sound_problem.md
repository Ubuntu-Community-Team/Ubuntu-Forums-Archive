---
title: "Satellite A205-S4587 Sound problem"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by malkateb on 2008-03-17
Hello,

My laptop is Toshiba  Satellite A205-S4587

I've been trying for *weeks* to fix my sound. But, failed.

Anyone can give me a step-by-step help to get my sound working? I tried the relevant posts on this forum but they couldn't fix my problem.

To start with,

The output of the command:

aplay -l

gives me this message:

aplay: device_list:205: no soundcards found...

Thanks in advance.

---

### Post by superprash2003 on 2008-03-18
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by malkateb on 2008-03-18
All right.

A progress has been achieved. 

I executed the following commands:

cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now

and got the sound card to be detected by the system and alsamixer back to work. 

Currently the output of the command: 

aplay -l

is as follows:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


BUT... I still do NOT have sound in my system. 

Any further idea that may help?

---

### Post by youtux on 2008-03-18
if you have ich8, i had the same problem and i have solved so:

add hardy repository, and type an apt-get update, but not the upgrade, then apt-get install alsa-source and remove the hardy repo. then dpkg-reconfigure alsa-source and select only hda intel. then the procedure with module-assistnat. if you want i can send a packet deb of alsa that i have made and should work for you, just send a pm

---

### Post by malkateb on 2008-03-18
Thanks much, Youtux.

I have ich7. 

Should your solution work in this case? If so, please send me more details about the solution. Excuse me, I'm very new to Ubuntu world.

---

