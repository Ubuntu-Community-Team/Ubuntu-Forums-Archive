---
title: "Edgy and Radeon X1950 Pro can't get fglrx to work"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by rblatz on 2007-02-19
So after hearing about how great Ubuntu is from everyone on the internet I decided to give it a try.  So far it's been pretty good, but still not the flawless experience I was hoping for.

 Frankly I'm impressed that everything was working on the first boot, I was able to start X, sound worked, my printer worked... all the things that didn't work last time I attempted Linux (several years ago).  Right now I'm using the vesa drivers for my video card (Sapphire Radeon X1950 Pro), I would like to get the fglrx drivers installed so I don't have jerky window movements, and can actually watch movies on my computer.  Tommy S stated in [http://ubuntuforums.org/showthread.php?t=315439&page=2](http://ubuntuforums.org/showthread.php?t=315439&page=2) that he was able to get his X1950 working using method 2 at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide).  I have tried this twice now and on reboot I get stuck at the Ubuntu screen and a weird blue line pops up.  I've restored the backup of my xorg.conf file and am back in X.  Does anyone else have any idea whats wrong? Has anyone else gotten the X1950 to work with the fglrx drivers?

---

### Post by Shepherd on 2007-02-21
I just went thru the ringer getting the fglrx drivers installed on my system. After way too many hours I finally got it working. My solution was real easy, but it might not help you. This [[COLOR="Blue"]page[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-83973.html") helped me. The key for me was to run "sudo dpkg-reconfigure xserver-xorg" so I could configure the xserver myself. None of the other webpages I searched even mentioned that. Part of my problem might of been running this command "sudo aticonfig --initial". It didn't set up my xorg.conf file correctly, bad monitor info. Make sure you have you monitor specs if you decide to setup the xserver manually (I used the advanced option).

Don't forget to add to the new xorg.conf file...

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

I left out...

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

...that the one set of instructions mentioned to put in. I haven't run into any problems with those lines left out of the conf file. So far fgl_glxgears looks great and on this old 9700pro card I get over 500fps. Now I just have to test it on a game. That's my next project, getting W.I.N.E. to work flawlessly :confused: 

Good luck

---

