---
title: "Internal and external mics work in vol control - neither work in skype"
date: 2009-04-30
forum: Hardware
---

### Post by musther on 2009-04-30
I have a Lenovo Ideapad S10, recently installed 9.04 on it.  

Both the internal mic, and external mic (socket) show up in the gnome-volume-control.  When I unmute them (the default state) and move the sliders up, I can hear sound from them, the internal and external mic boost sliders work too.  So in short, both mics work well.

But, I can't get any sound input in skype.  I've set it to use the correct device (the only one which works - the others don't even allow me to try to make a test call).  But, no matter what I do, I can't hear my recorded message (skype test call).  I can hear hissing, suggesting that skype is sending something.  Essentially, it appears that skype is connecting to the device correctly, but not using either of the mics properly.  I've tried unmuting and turning up the devices in the volume control, before making a test call, but as I suspected, this didn't make any difference.  

In the volume control in jaunty, there's nowhere to select the current input device, as there used to be - don't know if that's got anything to do with it.

Incidentally - with 8.10, I had it working, but only using the external mic, with that, older version of ALSA, the internal mic didn't work at all.

Any help is very greatly appreciated.

Cheers

---

### Post by exorcism on 2009-05-08
I have the exact same problem... can't get mic to work with skype. i will really need to use skype with this ideapad s10 so please someone help!

i'm using the desktop version of jaunty and not the netbook remix if it makes a difference.

---

### Post by exorcism on 2009-05-08
just made my internal mic work with skype

i did this alsa upgrade mentioned here:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

i tested with the skype audio setup thing.. make a test call and finally i can hear my own voice. 

in the process i muted the microphone and mic boost and yanked the internal mic levels to max and just a bit on the internal mic boost. 

hope this works for you too.

ps: devices in skype are all set to hdaintel (first option under default device)

---

### Post by musther on 2009-05-08
CONFIRMED!

Using the newer version of alsa (by doing the upgrade linked to in the above post) you get full use of the HDA soundcard in the S10 - that means that both the internal and external mic work properly, including in skype.

I've read things which suggest not using that alsa update script as it's unsupported etc - but if you want your S10 sound to work properly, that's how to do it.

Cheers Exorcism

---

### Post by jrc4ever on 2009-05-09
THX!!! worked on my Lenovo S10e

---

