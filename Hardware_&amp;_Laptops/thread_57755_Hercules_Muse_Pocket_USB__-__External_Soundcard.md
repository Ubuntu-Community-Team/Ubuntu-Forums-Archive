---
title: "Hercules Muse Pocket USB  -  External Soundcard"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by Ubuntuphraxis on 2005-08-17
Hello, on windows I'm using a 'Hercules Muse Pocket USB' as a soundcard, it's external and I want to know if it is compatible with Ubuntu...I've looked for drivers for it but not very extensively...

I'm very interested in changing to Ubuntu and do not want soundcard compatibility to hinder this change. Any help?

Thanks.



**P.S**  *Sorry if this is the wrong category to post in about this...* :???:

---

### Post by florut on 2006-10-29
Hmm... Not plug-and-play with kernel 2.6.17 (edgy), obviously (no surprise!...)
I would like to know if there is a way to make it work ?

---

### Post by bettola on 2007-03-01
anyone have informations?

---

### Post by bettola on 2007-03-06
help! card is recognized but when  select it by default on audio preferences and immediately if I reopen the window it's the other card by default again!

---

### Post by florut on 2007-03-30
I just upgraded to feisty fawn beta. Right after upgrade, sound was coming from my muse pocket usb sound card !! 
Then, happy and reassured, i restarted computer. And then, nothing again. All on the other sound card. 

Wouldn't there be some config to do ??

---

### Post by florut on 2007-03-31
I disabled my internal sound card and the sound card worked ! But... with only two channels. No way to activate the 4 others for 5.1 sound. 

And alsa seems not working as seen in console :
> flo@kubuntu:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device


How could i make it work with alsa (...so 5.1) support ?

---

