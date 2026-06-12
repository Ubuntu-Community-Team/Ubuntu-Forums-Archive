---
title: "Gutsy on Dell Precision M6300"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by mysticman on 2007-10-24
Hi Folks:

Can someone help me with this problem.  I've installed Gutsy on a Dell Precision M6300 laptop with an nVidia Quadro FX1600M.  When Gutsy boots it does not recognise my screen and xserver-xorg will not start.  What do I need to do?

Thanks

---

### Post by psypher on 2007-10-25
Thats weird. I just got my M6300, still busy setting it up right now, and the screen is working great. Installed restricted drivers and compiz is switched on. What I don't have is sound. lspci seems to pickup the hd audio device. but the volume control complains that it could need gstreamer plugins. so will try that in a minute.

I must say so far this has been a great start. Wireless picked up instantly and I'm connected to a WPA network. the bluetooth seems to be detected, although I can't test it. Don't have a bluetooth device.

The dell site has no linux drivers, although i hear that they are starting to sell the m6300 with redhat 5 next month so hopefully there will be some source drivers. 

few things to try.
make sure your install cd is perfect. do a hash check on the iso file b4 burning, and do a verify after the burn. then try install again.

try flash the bios. i see there is 1 bios update. not sure if there is only one.

my laptop came from ireland. so it might be where u got yours?

does the live cd boot up ok?

u might also, very slim chance, have a faulty drive or memory. but its rare on a new laptop.

still having problems, try posting your xorg log

---

### Post by psypher on 2007-10-26
k i got my sound working quite well. followed this: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

and used method g. Activate backport repository, apt-get update and then 
sudo aptitude install linux-backports-modules-generic

follow the rest of the instructions and yr sound and control button on the front will work perfectly. 

Only thing left now is hibernate. i could suspend, but hibernate does not work properly. gonna hack at it but if i get stuck i recommend the suspend2 software suspend kernel patch. used it on my old laptop and worked very well.

still don't know why u don't have screen. saw your post about xubuntu, which makes me doubt that it is a faulty cd problem.

good luck!

---

### Post by cpravia on 2007-11-12
Thank you for this post, I had the same problem with a Dell Precision M6300 and the solution G worked perfectly !!:popcorn:

---

### Post by zugg on 2007-12-13
I too had the problem of gutsy gibbon (64bit at least) hanging on the boot-up of the live cd on my dell m6300 (with a quadro fx 1600m vid card) . it was hanging at "loading boot scripts /etc/rc.local".  what i did was download and burn an iso of the "alternate" cd.  command line install. (look for the little check box on the ubuntu download site)

once installed it booted and said it didn't recognize the vid card, it offered to configure, cancel or continue (or something similar...it's from memory).  i just hit continue.  i then was able to log in and the first thing it did was suggest the nvidia-glx-new unrestricted driver which i installed and then rebooted.  all seems glorious (though no sound, i will try suggestions above).

---

### Post by zeddock on 2008-01-23
> **psypher said:**
> k i got my sound working quite well. followed this: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

and used method g. Activate backport repository, apt-get update and then 
sudo aptitude install linux-backports-modules-generic

follow the rest of the instructions and yr sound and control button on the front will work perfectly. 

Only thing left now is hibernate. i could suspend, but hibernate does not work properly. gonna hack at it but if i get stuck i recommend the suspend2 software suspend kernel patch. used it on my old laptop and worked very well.

still don't know why u don't have screen. saw your post about xubuntu, which makes me doubt that it is a faulty cd problem.

good luck!

Are you using the 64 version of 7.10 or the 32?
I have not yet tried to fix the audio but don't want to get too far from the basic install until I know where I am headed!

Thanx for your posts.
zeddock

---

### Post by jbella on 2008-01-24
Would you guys mind posting the hardware that you opted for on your M6300? I.e. wifi, bluetooth?  It looks like my work is letting me choose my next laptop and I really want to go with this model, but only if Ubuntu is pretty solid on it.  It sounds like it is, but I'd like to be sure I'm not wandering off into unknown territory :) 

Thanks!

---

### Post by zeddock on 2008-01-24
M6300 with 2 gigs of ram. 2.2 processor. regular graphics. WUXGA 17" display. the intel Wireless "N" card.  160 fall-sensor HD running 7200rmp.

Came with Vista Business. Did a shrink of that OS from inside of its disk manager app.
Installed Gusty Desktop from CD, and chose largest contiguous space.

Everything works well! the only issue was sound. Now that is working too.

I have VMware Workstation running XP Pro in the background without issue. Soon I will dump the Vista OS which is tying up HD space as I have come to HATE vista.

Good luck to you!

zeddock

---

### Post by jbella on 2008-01-25
Do you ever use this notebook with a docking station?  My plan is to be running with two external monitors while in the office. Any info on that?

---

### Post by EcliptuX on 2008-01-26
I have this computer too and all working very well with Gutsy (modem RTC and Firewire not tested for the moment)

---

### Post by sakisg on 2008-02-05
It does not works for me :( 
I thing it is my /etc/modprobe.d/alsa-base
how can I get the original ?

---

