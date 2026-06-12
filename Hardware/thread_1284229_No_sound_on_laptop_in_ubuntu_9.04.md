---
title: "No sound on laptop in ubuntu 9.04"
date: 2009-10-06
forum: Hardware
---

### Post by toownzie on 2009-10-06
Heya,

I'm having no sound at all on my laptop ( a medion akoya ).
I've tried many different tutorials/possible solutions, none worked..

Some more information: 
command aplay -l gives: 
 aplay -l
aplay: device_list:217: no soundcards found...

so that seems bad, but lspci lists a soundcard, this one: 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller

Another thing, the GNOME ALSA Mixer screen is totally empty, really like this: 
[http://img203.imageshack.us/img203/6407/screenshotgnomealsamixe.png]("http://img203.imageshack.us/img203/6407/screenshotgnomealsamixe.png")
 and when i try to click 'Edit -> soundcard propreties' even this empty screen disapears. Already tried reinstalling it, no help.

Any chance to fix the sound?

Grtz

---

### Post by BertjeBebo on 2009-10-06
Same problem, I suppose since the latest automatic update. I just noticed the problem when I tried to play a mp3. Last week, sound on my computer was perfect. I had a ALSA problem, but compiled a new version of the driver. 

cat /proc/asound/version

Linux Sound Architecture Driver Version 1.0.20.
Compiled on Sep 28 2009 for kernel 2.6.28-15-generic (SMP). 


I solved my problem by redoing the driver thing ([http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html))

---

### Post by toownzie on 2009-10-08
Thank you very much! 
I first tried the instructions on your link to update the driver, but i was stuck somewhere.. then i googled a little bit further and i found this: [http://webupd8.blogspot.com/2009/09/alsa-1021-upgrade-script-for-ubuntu.html]("http://webupd8.blogspot.com/2009/09/alsa-1021-upgrade-script-for-ubuntu.html"), pretty much the same website but with a script to perform the update. I just ran it, rebooted and sound is working now :)

---

