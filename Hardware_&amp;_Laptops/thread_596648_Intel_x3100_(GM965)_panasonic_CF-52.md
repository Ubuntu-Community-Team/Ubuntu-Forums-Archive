---
title: "Intel x3100 (GM965) panasonic CF-52"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by portamorta on 2007-10-29
I need some help:
[U]
System[/U]
Panasonic CF-52 (widescreen laptop) with Intel x3100 (GM965). 1280x800(60hz) native
 
Installed 7.10, I get 3d acceleration but I cannot get it to populate the right hand side of the screen. Ubuntu displays the screen but using just little more than a half of the screen. 

I can drag Icons to the unpopulated area, but, everytime I boot the login window, taskbar and nautilus windows wont get to the populated area. The only way I can get it to populate the whole LCD is by changing to 1024X768@30hz(Generic Monitor).


Tried:

Intel driver, i810 driver, Changing the monitor in the Screen and Resolutions to every setting as posible,"sudo dpkg-reconfigure xserver-xorg", xvid tuning, EVERYTHING

I've read every post available and nobody has had this problem!!!!!!!!!!!


Please Help

---

### Post by mattclary on 2007-11-02
I am also having this problem. I have found several references to it on the web but not a fix yet. I am surprised there hasn't been more talk of this.  :(

---

### Post by portamorta on 2007-11-03
Yeah, im surprised to. Seems like a common problem. I have installed 7.04 (kubuntu and ubuntu) and the same problem occurs. Im about to uninstall everything and keep using what works.

---

### Post by mattclary on 2007-11-04
OK, finally found the fix!!


This resolved the issue for me 100%  FYI, I'm running a Gateway ML6720, (now!) at 1280x800


[http://ubuntuforums.org/showpost.php...21&postcount=3](http://ubuntuforums.org/showpost.php...21&postcount=3)

I had found a similar fix that was much more complex than this that did not work, but this one did the trick.

---

