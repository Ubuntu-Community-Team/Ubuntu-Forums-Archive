---
title: "How do I should install Pixelview PlayTV Pro 2?"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by ernetas on 2006-06-22
How do I should install Pixelview PlayTV Pro 2?
I am following this: [http://www.linux.com/howtos/BTTV](http://www.linux.com/howtos/BTTV) , but there is no sound. I must to use PAL-D and my TV tuner supports PAL-BG/DK, but with tvtime I still can't get any sound. I am using 38 tuner. Modules realy are loaded.

---

### Post by Efialtis on 2006-06-26
I'm having the same problem with my Pixelview PlayTV Pro.
Its configured as card=37 tuner=5 and i can tune and see the channels fine but there is no sound. The cable from my tuner audio out is connected to my sound card line-in and in Windows it works flawlesly. I also tried the volume controls and mute option of my cards line-in in the sound panel and even installed and used aumix where everything seems fine. Any ideas will be appreciated.

---

### Post by ernetas on 2006-06-26
[QUOTE=Efialtis]I'm having the same problem with my Pixelview PlayTV Pro.
Its configured as card=37 tuner=5 and i can tune and see the channels fine but there is no sound. The cable from my tuner audio out is connected to my sound card line-in and in Windows it works flawlesly. I also tried the volume controls and mute option of my cards line-in in the sound panel and even installed and used aumix where everything seems fine. Any ideas will be appreciated.[/QUOTE]
Has your sound card hardware mixer?

---

### Post by aNTwNHs on 2006-11-19
I have the same problem on ubuntu 6.10 Edgy Eft.
I'm trying to setup my pci tv card (pixelview play tv pro / bt878 ). I finally managed to get video working perfectly (with tvtime) but i get no sound. Also radio seems to respond, at least it seems to scan station correctly, but again (obviously) no sound. The audio out of my card connects with a cable with the line in of my sound card.
I' think the problem is described better here: [https://launchpad.net/distros/ubuntu....15/+bug/29789](https://launchpad.net/distros/ubuntu....15/+bug/29789)
but none of the proposed workarounds seems to work in my case.
Has anybody managed to get this card working?
Any suggestions are welcome.

---

### Post by nzadLithium on 2008-01-03
dunno if any of you are still looking for an answer but this should make it go

sudo modprobe btaudio

---

### Post by sefs on 2008-01-05
Are you on gutsy?

If so do you have directions also for getting the card itself installed?  Do I have to download this bttv from elsewhere and install it or does it come by default in Ubuntu?

> **nzadLithium said:**
> dunno if any of you are still looking for an answer but this should make it go

sudo modprobe btaudio

---

