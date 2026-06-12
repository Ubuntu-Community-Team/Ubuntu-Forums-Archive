---
title: "Lexicon Omega Installation"
date: 2008-08-06
forum: Hardware
---

### Post by jmd87 on 2008-08-06
Hi,

I've got a lexicon omega that I used with Windows and I want to get it to work with Ubuntu 8.04.

I've read that it "Just works" but I can't get it to work at all.Please can you help?

Many thanks
Joe

---

### Post by dillinger417 on 2008-10-01
Ive had some small success recording w/ a Lexicon Omega using Jack and Ardour although currently I can't get it to register properly.  System log shows it being plugged in, but it's not in cat /proc/asound/cards and I can't pick it for devices in Jack setup. But what I did was set the input and output as the Omega in Jack settings, connect Jack, then start Ardour, then you have to make sure that you select the proper input for the track in Ardour. More info in this post [http://ubuntuforums.org/showthread.php?t=725077&highlight=Lexicon](http://ubuntuforums.org/showthread.php?t=725077&highlight=Lexicon) I would recommend installing the Ubuntu Studio packages... [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)...  If you posted more information, someone could probably help you better.

---

