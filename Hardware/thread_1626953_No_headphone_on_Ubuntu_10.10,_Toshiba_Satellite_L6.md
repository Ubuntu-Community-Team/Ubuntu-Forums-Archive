---
title: "No headphone on Ubuntu 10.10, Toshiba Satellite L650"
date: 2010-11-20
forum: Hardware
---

### Post by harris.sw on 2010-11-20
I found other users having problems with getting sound and internal speakers to work on laptops.  I have a Toshiba Satellite L650 and following other posts updated /etc/modprobe.d/also-base.conf and tried different options (added each one, rebooted, if it didn't work removed it and tried the next)"

options snd-hda intel model=toshiba
options snd-hda intel model=toshiba postion_fix=0
options snd-hda intel model=toshiba postion_fix=1 enable=yes
options snd-hda intel model=thinkpad

Interesting, alsa_mixer shows the intel hd sound but the 'system sound preferences' only shows an analog audio output.

Any ideas??

---

### Post by zorkerz on 2010-11-23
**[solved]**I think my friend is having the same problem on a toshiba satellite. When she plugs anything into the headphone jack the internal speakers still play and no sound comes out of the headphones.

Is this your problem as well and non of those lines worked for you?

I just fixed it by adding the following line to the end of /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=thinkpad
This is the same solution offered on a number of other posts.

---

### Post by harris.sw on 2010-11-24
Ok I found my mistake.  If you look at my original post I didn't have the dash between the hda and intel.  I can't believe I missed that but yes, now sound works!  So I have wifi working, sound working, next its video!!

---

### Post by hotmantra on 2010-12-29
Hi guys
               actually yesterday was my first experience with ubuntu 10.10. and it take 3 days to install ubuntu. unfortunately i had a problem with my audio jack. laptop speakers have no problem, it is perfect and clear but my audio jack has no response. then i tried almost 8 hours to fix this issue. i tried different steps posted by lots of friends in this forum. Atlast i got solution for this issue. I am using Thoshiba Satelite Pro L630 laptop. please use the following steps especially for toshiba users.



enter code :

gksudo gedit /etc/modprobe.d/alsa-base.conf

Add,save and close. You should restart

                 options snd-hda-intel model=thinkpad

This is the same solution offered on a number of other posts.
Last edited by zorkerz; November 23rd, 2010 at 10:04 PM.

---

### Post by hotmantra on 2010-12-29
sorry guys ,

enter code:

 gksudo gedit /etc/modprobe.d/alsa-base.conf

then add

options snd-hda-intel model=thinkpad

save,close and restart the system
 thanks for all:guitar:

---

### Post by Bor1s on 2011-01-02
I have a Toshiba Satellite C650-178 running Ubuntu 10.10 and I had the same problem. I am just posting to say that this solution worked for me as well :)

WiFi: check
Sound: check
Mic: not

---

