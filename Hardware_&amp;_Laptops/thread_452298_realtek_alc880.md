---
title: "realtek alc880"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by Daniele86 on 2007-05-23
Hello Everything,

I have a Fujitsu Siemens Amilo M1451G laptop with an Intel Realtek ALC880 soundcard. I have installed Ubuntu Feisty 7.04 with 2.6.20 kernel but suond doesn't work.I have an X on volume control and if I click on i have this errore message:
No G-Stream plugin or dispositive of volume regolation.
Can I have your help?

---

### Post by renzokuken on 2007-05-23
try searching SYnaptic for "gstreamer" and install the package that comes up.

reboot and see if it works then.

also, you could try going to System -> Admin -> Sound and make sure it is using the ALSA plugin instead.

if neither of those work, compiling the latest alsa-driver from source will probably sort it out

---

### Post by dbulante on 2007-05-24
I have the same sound card and have no sound also.  It seems like the drivers are properly loaded, but it doesn't recognize it.

---

### Post by renzokuken on 2007-05-24
in that case i'd recommend updating to the latest alsa-driver.

get it from [www.alsa-project.org](www.alsa-project.org)

extract the tar file, enter the new folder and do

```
sudo apt-get install build-essential
./configure
make
sudo make install

```

reboot and see what happens.

i think the latest stable version is 0.1.0.13 but i'm using 0.1.0.14rc4 with no problems at all

---

### Post by dbulante on 2007-05-24
I installed the current release candidate and rebooted.  Still didn't work.  No sound still.  So frustrating.

---

### Post by Daniele86 on 2007-05-24
I downloaded the sound card driver from realtek.com and installed it. After rebooting another problem appears: there is an error in gnome demon and the system works slowly,so slowly that I can't do actions(  like windows :D )...what do i do? format and reinstalling ubuntu?
It's possibile that ubuntu doesn't support my sound card?
Thanks

---

