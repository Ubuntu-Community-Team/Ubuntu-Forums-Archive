---
title: "Pixelview PlayTV Pro - No Sound"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by aNTwNHs on 2006-11-18
I'm trying to setup my pci tv card (pixelview play tv pro / bt878 ) on ubuntu 6.10 Edgy Eft. I finally managed to get video working perfectly (with tvtime) but i get no sound. Also radio seems to respond, at least it seems to scan station correctly, but again (obviously) no sound. The audio out of my card connects with a cable with the line in of my sound card.
I' think my problem is described here: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/29789](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/29789)
but none of the proposed workarounds seems to work in my case.
Has anybody managed to get this card working?
Any suggestions are welcome.

Thanx,
Antonis

---

### Post by aNTwNHs on 2006-11-19
Something funny, when I record with gnomeradio, although I don't hear anything the sound is recorded correctly. Any ideas pls?

---

### Post by aNTwNHs on 2006-11-19
[http://bugzilla.kernel.org/show_bug.cgi?id=7109](http://bugzilla.kernel.org/show_bug.cgi?id=7109)

any workaround?

---

### Post by aNTwNHs on 2006-11-20
I connected my speakers directly to the tv card and i get sound. Any suggestions on how to get sound from the master channel?

---

### Post by aNTwNHs on 2006-11-20
It finally was quite simple. The /dev/radio0 was muted! How i found out. I opened gnomeradio preferences and selected vol in mix source. After unmuting vol, I changed back to line, so as to control my volume (vol seems not to scale). I'dont remember finding this in alsamixer, or in any configuration file of bttv. Anyway the tv sound also works fine now.

---

### Post by davim on 2007-01-12
> **aNTwNHs said:**
> I'm trying to setup my pci tv card (pixelview play tv pro / bt878 ) on ubuntu 6.10 Edgy Eft. I finally managed to get video working perfectly (with tvtime) but i get no sound. Also radio seems to respond, at least it seems to scan station correctly, but again (obviously) no sound. The audio out of my card connects with a cable with the line in of my sound card.
I' think my problem is described here: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/29789](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/29789)
but none of the proposed workarounds seems to work in my case.
Has anybody managed to get this card working?
Any suggestions are welcome.

Thanx,
Antonis

How did you got it to work? I can't get it to tune any channel...

---

### Post by aNTwNHs on 2007-01-14
> **davim said:**
> How did you got it to work? I can't get it to tune any channel...
This [how to]("http://www.linux.com/howtos/BTTV/") worked for me. After that I had some problems with the sound, but it was solved...
> It finally was quite simple. The /dev/radio0 was muted! How i found out. I opened gnomeradio preferences and selected vol in mix source. After unmuting vol, I changed back to line, so as to control my volume (vol seems not to scale). I'dont remember finding this in alsamixer, or in any configuration file of bttv. Anyway the tv sound also works fine now.
Are you sure you have configured tvtime(or whatever) correctly (eg. TV system PAL/SECAm/... according to where you live)?
edit: also check [this]("http://linux.bytesex.org/v4l2/bttv.html").

---

