---
title: "No sound in 14.04 with HDA Intel PCH"
date: 2015-01-19
forum: Hardware
---

### Post by thompsw on 2015-01-19
Alsamixer reports that the card is HDA Intel PCH, chip is Intel Pantherpoint HDMI.  

I didn't have sound on 12.04, haven't had for some time (forever ?) and finally decided to check it out.  I decided to upgrade to 14.04, thinking that might solve the problem and I really should upgrade anyway.  I did that yesterday.  That turned out to be relatively painful as grub was updated on the wrong disc and VMware didn't want to recompile, but I got beyond all that.

Nothing is muted, alsamixer is reporting sound is set at reasonable levels, speakers are plugged into the correct analog motherboard port; I've done some googling and tried reinstalling alsamixer etc. I also tried creating a bootable 14.04 disc, booted from that with the same result -- no sound when I use the "test" buttons on sound settings.

Is it possible that the sound "card", i.e. the chipset, just doesn't work ?  Nothing is obviously wrong (at least to me !).

Thanks in advance for any suggestions ...

Dave.

---

### Post by thompsw on 2015-01-21
Lots of views but no suggestions -- anyone ?  

Thanks.

---

### Post by Yellow Pasque on 2015-01-21
The hardware is fairly recent, so I would try latest module/driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

If it's still not working with the latest driver (after reboot), give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by thompsw on 2015-01-24
Hi -- I tried the latest module/driver per your suggestion but still no luck.  The alsa info has been uploaded to 

 [http://www.alsa-project.org/db/?f=7d5b34557e14c580a74733b95bfee4928ad94bd3](http://www.alsa-project.org/db/?f=7d5b34557e14c580a74733b95bfee4928ad94bd3)

Thanks in advance for your help !

Dave.

---

### Post by thompsw on 2015-01-27
Hello all -- I'm still stuck without sound.  If anyone knows how to interpret the alsa information uploaded, I would appreciate any hints.

Thanks !

---

### Post by thompsw on 2015-02-06
Hello all -- still stuck no audio with 14.04  Does anyone know how to interpret the also information uploaded ?

Thanks !

---

### Post by Yellow Pasque on 2015-02-07
I don't see anything out of the ordinary. Have you ever tried headphones?

---

### Post by thompsw on 2015-02-09
Yes, just tried headphones.  No luck.

Dave.

---

