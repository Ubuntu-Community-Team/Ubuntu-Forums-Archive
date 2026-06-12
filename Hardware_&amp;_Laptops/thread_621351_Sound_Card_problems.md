---
title: "Sound Card problems"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by icedragon2002002 on 2007-11-23
im new to linux so explain things as if you were to a five year old. im having problems with my sound i can hear it if i plug in headphones but when i unplug it it doesnt play any thing on the built in speakers.im using a compaq evo-n180. help would be much apreciated. 

also if any one knows how to use the delorme usb gps on ubuntu that also would be awsome.

thanks

---

### Post by icedragon2002002 on 2007-11-24
can no one help me with this or is every one out on holiday?

---

### Post by eggdeng on 2007-11-24
Type ```
aplay -l
``` at the command line and identify your sound card from the list. That's lowercase L, not 1. I expect you will find it is an Intel HDA . If so, go to [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383").

---

### Post by icedragon2002002 on 2007-11-24
ok so it is an intel but what do i need to do for a compaq with an intell sound card

---

### Post by icedragon2002002 on 2007-11-24
> **icedragon2002002 said:**
> ok so it is an intel but what do i need to do for a compaq with an intell sound card

(note) its not an hda its an ich3 heres exactly what it says it is "Intel 82801CA-ICH3"

---

### Post by eggdeng on 2007-11-24
Doesn't look good. The card seems to have worked well on 7.04 after installing updates but not on 7.10. There is a bug report at
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/156013]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/156013") Sorry not to bring better news.

---

### Post by icedragon2002002 on 2007-11-24
no no thats good news just means that hopefully they will get enough bug reports to fix it. i do remember that it did work when i loaded the older version of ubuntu. unfortunatly the wifi card didnt work so i just went back to xp. thank you so much for your help!!!!:)

---

