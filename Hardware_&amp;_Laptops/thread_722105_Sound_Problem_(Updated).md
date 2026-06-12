---
title: "Sound Problem (Updated)"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by linux1time on 2008-03-12
Well...at this point and having typed (only god knows) dozens of command lines on the console etc i still have no sound on my acer 5315...nothing seems to work...my card is named realtek id 268....

I dont  have mutch of hope but if someone can help i appreciate

---

### Post by superprash2003 on 2008-03-12
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by nothingspecial on 2008-03-12
I have the same sound card. I fixed it following the instructions here.
[http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound](http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound)

I`d followed these instructions previously but they didn`t work. I, like you had typed countless billions of things into the terminal and probably messed up my system so much they didn`t work. It was not until I did a fresh install that they worked but they did. Your sound will work.

Couiple of other things, before following that post I typed -

sudo apt-get install linux-backports-modules-generic

Also the part of that post about updating alsa is refering to alsa 1.0.15.  The latest alsa is 1.0.16 so if you download the latest alsa, copying and pasting the code will not work.  If you want to copy and paste make sure you change anything that reads 1.0.15 to 1.0.16.

Also when I`d completed the how to and rebooted I still had to turn up the volume in alsamixer.

options snd-hda-intel model=toshiba worked for me.

Good luck:)

---

