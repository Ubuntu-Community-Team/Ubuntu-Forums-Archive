---
title: "SOund on Acer Travelmate 4002 wlmi doesn´t work!!"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by manoletux on 2005-02-08
Hi! 
I´m having problems with sound in Ubuntu Hoary, now with array4. With Warty there´s no problem, but when i try to install Hoary,  sound doesn´t works.

I´ve got an Acer 4002 wlmi, with an AC´97 Intel soundcard, but i can´t hear nothing, with other distros there´s no problem, and i don´t know what to do....

i want to hear my mp3!!! :)


Thanx!!

Manuel Mas

PD: If you need something, just tell me.

---

### Post by snop on 2005-02-08
Hi,

I own an Acer travelmate 4001Wlmi (I think the only difference between 4001 and 4002 is the processor: 1,5Ghz - 1,6Ghz).

Some time ago I lost the sound when installing an update. I fixed that adding this line to /etc/hotplug/blacklist:
snd_intel8x0m

I guess you may solve your problem just issuing this command:
sudo "echo snd_intel8x0m >> /etc/hotplug/blacklist"

Then restart your system. 

Also check your esd configuration in gnome. In case you don't know esd is the sound server that gnome uses (our soundcard can't do hardware mixing so it may be perfomed by software). You should check Desktop -> Preferences -> Sound and see if the checkbox named "Start sound server at startup" (or something like this) is enabled. Also make sure your applications use esd instead of alsa. Check this thread for more info:
 [http://ubuntuforums.org/showthread.php?t=8235&highlight=Device+resource+%2Fdev%2Fdsp%3A+busy](http://ubuntuforums.org/showthread.php?t=8235&highlight=Device+resource+%2Fdev%2Fdsp%3A+busy)

I hope you solve your problem as I did. Tell us if this work for you.

Bye

PD: Perhaps you could check if the first solution works (once you blacklisted snd_intel8x0m) without rebooting your system issuing this commands:
sudo killall esd
sudo rmmod snd_intel8x0m
sudo /etc/init.d/alsa restart
sudo esd

---

### Post by manoletux on 2005-02-08
Hi!!

The sound now works, after deleting the module and rebooting, but i have problems with the audio files, an media players, i&#314;l be trying these days, i&#314;l tell you!!

thanx!!

Manuel Mas

---

### Post by manoletux on 2005-02-09
Hi!!

Like i tell you yesterday... now sound works, but it's so distorted, it sounds very bad, the gnome-ubuntu sounds of the desktop sounds at the samen way, distorted, and now i don know what to do...


Manuel

---

### Post by snop on 2005-02-09
Hi,

My computer sounds find. However the built-in sound card is not a high quality one. If you are using an external amplifier and the volume is too loud it may sound distorted. 

Also check if there are bass/treble controls (I don't have such controls on my mixer so I guess you won't have them as well) but xmms, bmp and this kind of apps has equalizers (try disabling equalizers).

Bye

---

