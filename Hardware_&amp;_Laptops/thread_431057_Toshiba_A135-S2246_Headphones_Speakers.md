---
title: "Toshiba A135-S2246 Headphones Speakers"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by stchman on 2007-05-02
Hello all, I have a Toshiba Satellite laptop model A135-S2246 running Ubuntu 6.10.  Everything works well except that when I plug in the headphones the built in speakers still continue to function.  This is a problem when I go on an airplane and watch a movie or listen to music.  I turn the sound up and everyone around me hears the movie.  The volume wheel on the front turns up the sound for both speakers and headphones.

I thought that the headphones being plugged in deactivates the built in speakers.  Apparently this is not the case.  Does anyone else have this problem and is there a solution?

Thanks.

---

### Post by stchman on 2007-05-02
Anyone?

---

### Post by n3azz on 2007-05-03
I have the same problem on my Toshiba Satelite pro a120.....

please, somebody help us here...!!!!

---

### Post by stchman on 2007-05-07
Does anyone happen to know what type of hardware this laptop contains?  I have determined the following:

Processor: Celeron M 430 1.73GHz
Video:  ATI Radeon Xpress 200m (shared video memory)
Chipset:  ATI SB400
Sound: ? (according to Toshibas' website the built in sound card is a Realtek model, some folks say SB450)
Ethernet:  Realtek 8139
Wifi:  Atheros ???? (madwifi works)
Modem: ???? (don't use a modem so I don't care)
Touchpad:  Synaptics (fully works in Ubuntu)

---

### Post by erissiva on 2008-04-04
This now seems to be working relatively in the 8.04 beta. However, now it seems like its functioning is on/off. 

Every once and a while, when I unplug the headphones - the speakers don't come back on. :confused:
I don't understand why. That issue hasn't been fixed with any of the solutions I've found in the forums and it hasn't been fixed in the new beta.

anyone shed some light on this?

---

### Post by VMan on 2008-04-04
I'm not sure why your speakers don't come back on when you unplug the headphones.  I had the problem with the speakers staying on when the headphones were plugged in.  I tried several modifications to the /etc/modprobe.d/alsa.base file until this suddenly started working.  I could have sworn it didn't before.

Add this line to /etc/modprobe.d/alsa.base:
options snd-hda-intel model=lenovo

This worked with an A135-S4467 laptop.

---

