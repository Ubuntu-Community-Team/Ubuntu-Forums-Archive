---
title: "Logitech Webcam With Ubtunu?"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by Breaks on 2006-01-28
Well, i have a logitech webcam, and i use it a lot with skype, on a windows machine that is, but im just curious, is it hard, or even possible to get a logitech webcam working under ubuntu? and on skype?

---

### Post by it.henrik on 2006-01-29
It depends on which one you have :)

The way I got it working was by following this post from Arnieboy.

[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

### Post by Breaks on 2006-01-29
Ahh.. ill be sure to give that a try, hopefully it works.. thanks for the reply :).

---

### Post by nalmeth on 2006-01-29
NOTE:
I don't think that the linux version of skype supports webcam yet. Look into it, but when I tried, it couldn't even recieve an incoming feed.

GAIM messenger also does not yet support webcam's either, but the new aMSN does now support webcams after all. 

It is not in the repositories yet (you would download an older version without webcam support if you tried synaptic or apt-get)
To install it (if you don't know), go to [http://sourceforge.net/projects/amsn/](http://sourceforge.net/projects/amsn/)
(sourceforge seems down/slow at the moment, so I can't get you the exact link)

Look for version 0.95, and pick Ubuntu when it asks for your distribution.

Save the .deb somewhere (maybe desktop)

Open a terminal, and go to the directory you saved it 

cd ~/Desktop

type:
sudo dpkg -i amsn0.95.deb

replace with actual name of package of course..

---

### Post by Breaks on 2006-01-29
Why, does that version of amsn support webcaming? 

Thanks for your replies by the way :).

---

### Post by nalmeth on 2006-01-29
Not totally sure. Usually cloning a MS app is a gradual process. I guess they just finally 'unlocked the door'.

As to why this most recent and useful version is not in the repositories, I couldn't say. I don't know much about the development/integration process. 

I for one was really dissappointed with skype not supporting webcam's with their linux version. Linux sometimes gets the short end of the stick from 3rd party developer's. More 3rd party support would boost everything tremedously. At least we can see it picking up though!

Good luck with your cam!

---

### Post by Breaks on 2006-01-30
Ahh yeah when browsing the skype website it says the version for linux is 1.2 something but the one that supports video is 2.0 which is only for windows for now.. indeed that does kinda suck a bit..  im guessing the mic works without fail on that though? If so is it easy enough to get a mic working?

---

