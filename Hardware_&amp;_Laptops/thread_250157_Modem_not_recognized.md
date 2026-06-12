---
title: "Modem not recognized"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by scottym on 2006-09-03
I have a thinkpad g40 with an Agere  AC'97 modem. Ubuntu will not recognize the modem. I have configured a dialup but when i do the pon command i get 'unrecognized option /dev/modem'. I am about to give up on Ubuntu if i can't get an internet connection. 

Also assuming i am able to connect how do i run the firefox that i have in windows xp partition. I know there is a firefox in ubuntu but i have ahighly customized one i have been using for a while. Also the same with Thunderbird. I have been unsuccessful as well trying to mount the harddrive following the instructions on the this forum. I also want to use my firewall and a few other programs running in windows. Is it possible to do this?

---

### Post by mariner09 on 2006-09-03
To get your modem working, you need to install a package called sl-modem.  I haven't had to use a modem for some time under linux, but that's what you'll need to get started for the modem you have.  I use a T41 with the same modem.

As for launching your applications on your windows partition, I'm not sure that's entirely possible.  Your XP partition is probably formatted as NTFS which may be quite difficult to mount without recompiling NTFS support into your kernel.  Search this forum on mounting NTFS partitions and you will find that answer.

Best bet is to copy you thunderbird and firefox personal folders over to your linux partition and using it in that manner.  Making a small fat32 partition would be a good way to facilitate this as well as a simple USB key.

Good luck...

---

