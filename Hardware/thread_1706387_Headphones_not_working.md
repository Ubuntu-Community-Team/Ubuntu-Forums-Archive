---
title: "Headphones not working"
date: 2011-03-13
forum: Hardware
---

### Post by jstnhickey2 on 2011-03-13
I have tried a few tutorials I found on google and tried to search for a driver for this card but I have not had luck.  Speakers work, but I need the headphones jack to work.  It works fine in windows, as I tested it since I am duel booted.  Alsa is installed.  According to alsa mixer I have:
Card: HDA ATI SB
Chip: Conexant CX20561 (Hermosa)

I am a beginner so step by step instructions would probably be needed for me to do any kind of work in the terminal.  
Thanks in advance.

---

### Post by jstnhickey2 on 2011-03-21
anyone?

---

### Post by jstnhickey2 on 2011-04-03
top, would love to use some headphones.  any ideas?

---

### Post by jstnhickey2 on 2011-04-11
top again

---

### Post by Yellow Pasque on 2011-04-11
Driver is pre-installed with Ubuntu (though there are also some 3rd-party drivers from conexant called linuxant).
Before you mess with the driver, first check headphone jack volume and mute status in alsamixer
```
alsamixer
```
Also run alsa-info script and post your info: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

