---
title: "LG T1 sound issues"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by chaosgeisterchen on 2006-09-25
Hi there,

I am a more or less proud owner of a LG T1 Dual Express notebook (the cheaper edition). These is the basic technical data:

Intel Centrino Core Duo CPU, 2 MB cache, 1860 MHz max.
Intel GMA 950 integrated graphics
1024 MB DDR2-667 RAM
Intel Pro/Wireless 3945ABG
60 GB P-ATA 1,8" HDD, 4200 rpm
some Agere Ethernet card (not working out of the box)
Bluetooth, Video-Out, 3x USB 2.0, etc...
5200 MAh battery
1440x900 max. Resolution
14,1" WXGA+ display

The problem is the following:

Sound is working fine with speakers but if I plug in headphones, I have sound both on headphones and still on speakers.. so there is double output - normally, speakers mute upon plugging in audio out. I have tried to reconfigure alsa, tried to change several settings in GNOME.. but I did not find a solution yet.

I can only say: Help! If there is anyone out there having the capability to help me, I would be very pleased.

Thanks in advance.

~cg

---

### Post by xyz on 2006-09-25
Hi-
Have you tried Application > Sound/Video > Volume Control and ticking/unticking red X?
But it's weird...normally it cuts itself off without "human intervention"...so to speak.
Hope it works!

---

### Post by chaosgeisterchen on 2006-09-25
Sorry, but it does not work :(

alsamixer shows that headphones are chained to speaker settings - this is quite weird..

---

### Post by diantn on 2006-12-28
Please check this out for LG T1 / TX sound issue:
[http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html](http://www.math.chalmers.se/~ossa/linux/lg_tx_express.html)

Link from: [http://nsaunders.wordpress.com/2006/08/10/ubuntu-606-on-the-lg-t1-express-dual/#comment-1557](http://nsaunders.wordpress.com/2006/08/10/ubuntu-606-on-the-lg-t1-express-dual/#comment-1557)

> 
The sound works out of the box as well, but there is a problem that plugging in headphones does not deactivate the internal speaker. This turned out to be as simple as adding a module option.

    * Exit the desktop, and stop the sound:

      >/etc/init.d/alsasound stop


    * Install modconf:

      >sudo apt-get install modconf


    * sudo run modconf, and find kernel/sound/pci/hda. Install snd-hda-intel, and in the option prompt add model=lg.

    * Restart alsasound.


After I did this on my TX the headphone port started working as expected, but microphone stopped working. This turned out to be a mixer setting. If you start alsamixer you'll find there are now three switches called Input Source, Input Source 1, and Input Source 3 respectively. Setting these to Mic, Line, and Internal Mic respectively, and setting the volume of the first one up under the capture tab, seems to work, at least for make skype calls. Your mileage may vary.


---

### Post by chaosgeisterchen on 2006-12-29
Thanks, I will give it a try.

---

