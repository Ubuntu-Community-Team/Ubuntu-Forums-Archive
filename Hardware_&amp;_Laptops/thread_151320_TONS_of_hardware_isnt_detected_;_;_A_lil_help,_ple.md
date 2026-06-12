---
title: "TONS of hardware isnt detected ;_; A lil help, please?"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by N1GH7M4R3-Linux on 2006-03-27
Well just finished installing Ubuntu...did the initial package updates and had a look around....first of, i can't access hdb, which is my secondary FAT32 hard drive (I need that!!) and my Asus GeForce 6600 isn't being detected properly. Any help would be nice :)

---

### Post by aysiu on 2006-03-27
[QUOTE=N1GH7M4R3-Linux]Well just finished installing Ubuntu...did the initial package updates and had a look around....first of, i can't access hdb, which is my secondary FAT32 hard drive (I need that!!)[/quote] A combination of these two links should help:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) > and my Asus GeForce 6600 isn't being detected properly. Any help would be nice :) Try pressing Control-Alt-F1, logging in, and then typing ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can and then ```
exit
``` Control-Alt-F7
Control-Alt-Backspace

---

### Post by N1GH7M4R3-Linux on 2006-03-27
Sorry, followed your instructions, video card still isnt being detected... :( but the good news is, I got my windows drive :D Any clue as to why it won't work? (The video card I mean)

---

### Post by aysiu on 2006-03-27
It's entirely possible your card is just unsupported.

If not, maybe [this link](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) might help.

---

### Post by N1GH7M4R3-Linux on 2006-03-27
Thanks, I fixed it, even though DM doesnt see it, i get the nVidia splash screen before login. :D Thanks.

---

