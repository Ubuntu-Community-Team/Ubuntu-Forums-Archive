---
title: "Dual Monitor with two AMD Cards"
date: 2014-05-25
forum: Hardware
---

### Post by cranerja on 2014-05-25
Hello I'm running Ubuntu 14.04 with AMD Radeon HD 7870 and a AMD Radeon HD 7770 using the RadeonSI drivers. On start up, I get static on one monitor and black on the other. The only other thread I can find doing something similar dates back to 2005 and it states modifying the xorg.conf. xorg.conf is now empty on fresh installs and I am unsure of how to create one. I tried reconfiguring X from a tty but it didn't help any. What are my options?

---

### Post by gordintoronto on 2014-05-25
What are the brands and models of your video cards? Most modern video cards have (at least) two outputs, so you don't need two cards. Does your computer also have on-board video?

What version of Ubuntu are you using? Did you use "additional drivers" to install RadeonSI?

I would remove the 7770 and see what happens.

---

### Post by cranerja on 2014-05-26
One is an ASUS and the other Gigabyte. I have been using only the 7870 right now but I can't play a full screen game with both monitors on without tearing. I stated that I'm using 14.04 and yes the drivers are on that menu.

---

### Post by soldiertheinsanitywarrior on 2014-05-26
Afaik, you cannot crossfire 7870 and 7770. Or even use them at the same time.

Tearing is an issue with AMD drivers, all 3 drivers. FGLRX, Windows, and Mesa. I would advise against buying another radeon in the future if you cannot handle tearing.

---

### Post by cranerja on 2014-05-26
Its not a driver issue. I have zero tearing when its one monitor. This has been done before using the xorg.conf but I don't know how to occupy the file. Thats all I'm trying to do. 
[http://ubuntuforums.org/showthread.php?t=53966](http://ubuntuforums.org/showthread.php?t=53966)
This seems still possible to me but I'm unsure of how to do it.

---

### Post by soldiertheinsanitywarrior on 2014-05-26
I've always had terrible tearing on my computer, regardless of driver, except for a single version of the windows driver. Might be something to do with screen size and available bandwidth.

---

### Post by cranerja on 2014-05-26
Okay well I'm not having tearing unless I'm having multiple over hd monitors on it. I'm just trying to setup two video cards.

---

