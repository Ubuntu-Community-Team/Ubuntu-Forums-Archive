---
title: "apt-get (fresh install)"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by GeorgeB on 2006-02-09
Hello! I've just installed ubuntu and I've already run into some problems, and was wondering if anyone would be able to help. I've been unable to play any media, listen to music, or anything else. Now I've tried to get certain plugins via apt-get, but EVERY single thing I've tried to get through apt-get has failed. ie ...... Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs


Every package, even more common ones does the exact same thing :(

Is there a way around this or a fix? or do I need to configure apt-get to look in a certain repository of packages?

If anyone could help it would be greatly appreciated.

Regards, 

George

---

### Post by kingsidy on 2006-02-09
if you all you need is w32codecs follow the instructions below. you can also grab libdvdcss2 as well: 

> $ sudo gedit /etc/apt/sources.list

Add this lines

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

then in the terminal do:

$ sudo apt-get update

then

$ sudo apt-get install w32codecs

---

### Post by GeorgeB on 2006-02-09
Thankyou for the swift reply! Well it isn't all I need, but would I do a similar thing for the other plugins/codecs I need? ie for mp3s, mpgs, etc

I'll try it out now

---

### Post by kingsidy on 2006-02-09
you also need to enable your repositories in order to get access to all the packages. You can also install automatix which simplifies things quite a bit.

---

### Post by GeorgeB on 2006-02-09
Cheers! How would I enable them?

As for automatix, I'll have a look now

edit : I take it i just uncomment the links

---

### Post by kingsidy on 2006-02-09
yea at least unable the universe and multiunerverse repositories. i think that some of the repositories are not working. like those that say mirrormax so do not enable those. I just use automatix it'll get you a nice source list.

---

### Post by GeorgeB on 2006-02-09
Ok thanks for all the help, i should be right from here :)

---

### Post by kingsidy on 2006-02-09
good to hear.

---

### Post by GeorgeB on 2006-02-09
OK one more thing hopefully ... You mention automatix, and looking at it I find it to be quite sexy! Shame I'm on hoary though ... Just thinking if [http://ubuntuguide.org/#upgradehoarytobreezy](http://ubuntuguide.org/#upgradehoarytobreezy) would be a good idea, or there's a more stable way of updating to breezy?

Sorry to hassle you all, this has become quite a frustrating distro, all though simple when I find out what I was doing wrong

---

