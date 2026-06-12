---
title: "Natty C-Media CMI8338 no sound and 7 channels problem"
date: 2011-10-03
forum: Hardware
---

### Post by xube on 2011-10-03
Again... after problem with Creative and external soundcard i decided spend another few bucks for better soundcard that should be compatible! According to alsa there is supported module snd-cmipci. Soundcard is detected but only 4 channels and NO sound. Volume control is mute after every reboot. When i change volume or unmute soundcard disappear from devices in sound settings.

So i tried almost everything and nothing helped. Perhaps i can install native OSS driver but there will be lot of problems with compatible and i don't know about any tutorial or straight-forward documentation how to do it without breaking Ubuntu with option to control volume or number of channels.

Any advice, link or help?
Thanks

---

### Post by xube on 2011-10-03
Fine, Solved! C-Media works great after installing 11.10, and putting to PCI socket..."hard way". I am not sure but i have some clues that there's some compatibility issue with my mainboard. Perhaps BIOS... But again, i am not sure it's just my opinion.

Right now i can't choose my integrated Realtek HD soundcard but in bios is set to auto. I think, BIOS has some problems with IRQ addressing or he decided that i don't need soundcard as i have one. It's Asrock N68PV-GS motherboard (latest 2.0 BIOS).

*There is still problem with 7.1,5.1 channels if you want recording too. So you have to choose only Duplex before recording. But It's not big deal and it's logical.*

---

