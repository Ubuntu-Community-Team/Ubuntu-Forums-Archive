---
title: "Screen black and after don't refresh"
date: 2016-01-06
forum: Hardware
---

### Post by angel45 on 2016-01-06
Hi,

I have install Lubuntu 15.10 about 2 weeks ago and I have a problem, when I'm using for a lot of times the screen goes down (colour black) and after show screen again but don't refresh correctly, like the images

[ATTACH=CONFIG]266574[/ATTACH][ATTACH=CONFIG]266575[/ATTACH]

I think is a problem of the graphics driver my card is 

00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)


I have remove it and install 15.4 and I haven't this problem.

Anybody can help me?

---

### Post by angel45 on 2016-01-11
Nobody?

---

### Post by mörgæs on 2016-01-12
Could be a matter of switching to UXA acceleration.
If you follow the link in my signature and search for 'UXA' in the text you will find instructions.

---

### Post by angel45 on 2016-01-15
Oyea!!!! That's the problem

I resolved width this link

[https://lists.ubuntu.com/archives/lubuntu-users/2014-April/007019.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-April/007019.html)

-----
Edit (or create) /etc/X11/xorg.conf as follows: (ugh, can't format,
should be a tab before each line except the first and the last).

Section "Device"
	Identifier "Intel Graphics"
	Driver "intel"
	Option "AccelMethod" "uxa"
EndSection
-----

---

