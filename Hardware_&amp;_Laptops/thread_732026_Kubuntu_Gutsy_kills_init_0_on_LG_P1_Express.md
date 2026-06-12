---
title: "Kubuntu Gutsy kills init 0 on LG P1 Express"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by CaptainHowdy on 2008-03-22
Hello people,

 I have an LG P1 Express laptop and i have Gutsy installed on it. 
I am recently having the following problem: When i press shutdown
or restart, the computer will initiate the appropriate actions but then freezes
(screen turns black). When i press CLTR+ALT+DEL it displays a message
something like "process init 0 killed" or something like that. As far as i can understand
somehow the process that initiates the shutdown of the computer is killed and 
the computer does nothing.

Where should i look or what should i check first?

Thanx!

---

### Post by CaptainHowdy on 2008-03-23
*bump*

---

### Post by CaptainHowdy on 2008-03-23
I have found the answer to this post:

[http://ubuntuforums.org/showthread.php?p=3849639&page=2](http://ubuntuforums.org/showthread.php?p=3849639&page=2)

I hope it works! :guitar:

---

### Post by CaptainHowdy on 2008-03-24
Unfortunately does not work! :confused:

Anybody? Ideas? At least where to start from??

---

### Post by FrankT-Qc on 2008-04-26
Hi 

I don't know if I can help, but right now, I'm running Hardy on a LG Laptop P1 Express Dual, on three partitions (swap, /, /home) and It's dual booting with Vista and running trouble free as long as I don't try to add a second monitor... 

I have been running Gusty, but it wasn't that comfortable, especially when it came to display drivers. If i ever changed a few things about it, (like trying to use ATI proprietary driver) my laptop would stop booting...

It's worth trying Hardy. By the way, installing the KDE4 version might be tricky; if i didn't use the safe graphics mode to install, i got HUUUGE fonts (like i could merely fit five characters in the screen)... LG being what it is, you might want to stick to KDE3...

Have fun !
Frank

---

### Post by CaptainHowdy on 2008-05-08
I have found the answer:

The problem lies in the ATI drivers. Specifically:

In /etc/ati/authatieventsd.sh change this line:
   XDM_AUTH_MASK=/var/lib/xdm/authdir/authfiles/A$1*

to:
   XDM_AUTH_MASK=/var/run/xauth/A$1*

I have found it in some bug in the launchpad and it worked! :guitar:

Cheers!

---

