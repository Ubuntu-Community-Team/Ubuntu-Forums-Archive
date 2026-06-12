---
title: "Wacom Bamboo Pen &amp; Touch Working on Ubuntu 10.10 !"
date: 2011-03-04
forum: Hardware
---

### Post by sephiroth_slash on 2011-03-04
Hi guys,

I tried so hard to install the driver for my tablet Wacom Bamboo pen & touch on Ubuntu 10.10 amd64, I spent hours & hours following the official driver installation on [here]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page") , I installed both **[xf86-input-wacom]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom") **and **[linuxwacom]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Linuxwacom") **and edited xorg.conf and 50-wacom.conf but that didn't work ( very weird ) !!

But I found a very simple trick to make Bamboo Pen & Touch work ! here's the stuff : 

- Run these commands : 

[FONT=Courier New]$ sudo add-apt-repository ppa:ripps818/wacom
$ sudo apt-get update
$ sudo apt-get install wacom-dkms [/FONT]

 - Reboot  



It works !! I dunno how !!

Now I'm enjoying some vector drawing with InkScape !! 

Hope it helps !!

---

### Post by eyedeal on 2011-03-07
Not working for me. You've probably done other things before that...

---

### Post by thunderbirdje on 2011-03-12
Same configuration here: Bamboo pen & touch new model CTH-460/K(A) = also recognize touch gestures + Ubuntu 10.10.

This worked for me

sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get install wacom-dkms

(Still testing the touch gestures...)

---

### Post by brabender on 2011-03-13
> **thunderbirdje said:**
> 
This worked for me

sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get install wacom-dkms

It works for me too! Wacom Pen & Touch CTH-460 + Ubuntu 9.10 32 bits. Only thing that does not work is touch gestures, I'll keep trying. Thanks for the advice.

---

### Post by DuckDodgers on 2011-08-25
This solution only marginally worked for me I can't use the touch feature and I can't rest my hand on the pad while using the stylus making drawing fairly awkward.  Also the buttons don't work.

---

