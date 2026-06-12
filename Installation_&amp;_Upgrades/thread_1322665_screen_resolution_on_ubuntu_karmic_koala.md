---
title: "screen resolution on ubuntu karmic koala"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by mistikkia on 2009-11-11
hello everyone,

I'm trying to change my screen resolution on ubuntu karmic koala ... and things are going horribly wrong ..
I have a fujitsu siemens esprimo mobile laptop (version V5535) with intel core 2 duo ...
i'm only getting some 800x600 but I would like to use the full potential of my screen (which i think is 1280x800 according to this : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/444476](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/444476)) .. for previous ubuntu releases i just tweaked the xorg.conf file and it kinda worked ... now I cannot do that anymore ... (copying a random file with random parameters makes the laptop go only in command line mode)...  i did try to do things "a la carte" ... but I do not know where to find the parameters of my screen (looked through websites and manufacturer website but it does not mention anywhere HorizSync or VertRefresh or anything useful).

since karmic koala doesn't even have an xorg.conf file i tried to look for alternatives ... no success .. found something about intel video drivers.. but as far as i understand they should already be installed in 2.6.31-14-generic

##if this is of any help : lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)


thanks,
mistikkia

---

