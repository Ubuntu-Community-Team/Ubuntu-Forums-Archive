---
title: "no sound on asus w7j"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by amaan on 2007-02-25
i just recently installed ubuntu 6.10 - although have not been able to get my sound working. i've tried numerous solutions:

1. download and install linux drivers from realtek.tw website
2. use guide [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) using latest updates of the driver, lib, utils, and oss files
3. took a look at about a dozen threads that circled around the same problem, including this one which was most useful (although i still couldn't get the sound working): [http://www.ubuntuforums.org/showthread.php?t=283155&page=3&highlight=realtek+hd+audio](http://www.ubuntuforums.org/showthread.php?t=283155&page=3&highlight=realtek+hd+audio)
4. a lot of going back and forth; i.e installing, re-installing, un-installing, and again and again

so basically, i have an asus laptop w7 series, model j (w7j), and im running the realtek high definition audio hardware - at least whats what windows xp driver said when i had xp installed

i'm totally noob to linux, but absolutely love it and definitely do not want to go back to xp

if anyone can give me a hand it would be highly appreciated, thank you in advance

regards,
amaan

---

### Post by amaan on 2007-02-25
yea so im replying to myself so that nobody has to waste time, i got it working

solution i used:

i followed the HdaIntelSoundHowTo, i installed the latest SVN version of alsa-driver, library, utils, and oss.

after that , i edited /etc/modprobe.d/options, by using:

sudo gedit /etc/modprobe.d/options

then added this line:

options snd_hda_intel model=3stack

then i saved, and rebooted, and voila i had sound :)

---

