---
title: "Cmpq r3000 pointer freezing after clicks"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by beetlejelly on 2006-07-01
I have 6.06 installed on a Compaq R3000 AMDx64 Laptop and everything seems great except that when I click on an item with my mouse the system freezes until the mouse is moved. this includes clicking on icons on the desktop, applications and also Internet links. 
thanks

---

### Post by Fully216 on 2006-08-15
I had a similar issue until I installed the latest synaptic driver (even though I have an Alps touchpad).  More information on the issue can be found here:

[http://www.ubuntuforums.org/showthread.php?t=60494](http://www.ubuntuforums.org/showthread.php?t=60494)
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[http://www.linuxquestions.org/questions/showthread.php?p=2375738](http://www.linuxquestions.org/questions/showthread.php?p=2375738)

With some of the options shown in the xorg.conf, you will be able to control that aweful behavior you are talking about.  The last link above has a sample xorg.conf file that might be useful.  I would post mine but I often use a kingston usb mouse as well, causing a more complicated configuration.

The driver that I used can be found here:

[http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)

I hope this helps! ;)

---

### Post by ksquared on 2006-08-18
...dude, U ROCK! I was having that problem too with my V2000Z. I imagine we have similuar touchpad mouse hardware... while it has not locked up, I have one heck of a time grabbing a window to move or resize it. I had Fedora core 5 on it before, and it did not have the same problem (lots of other ones, but not the same window select issue).

I will try your recommendations and see where that takes me.

---

