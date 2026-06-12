---
title: "Multiple Problems with Dell Inspiron B130 and Feisty"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by frogitts on 2007-05-08
I'm not sure if this is the right thread to be posting in, but I've got a number of n00bish problems that I just can't find answers to. I think most of them are hardware related. Here's what I've got:

Dell Inspiron B130
1 GB Ram
Intel Celeron 1.5 Ghz
 Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

Here are my main problems:
1) Video problems
     Open Arena causes a logout. This makes zero sense to me and doesn't come up in any OpenArena forums
    Scorched 3d freezes as soon as 3d scenes are displayed. I don't know how to kill a task when I can't use the menus to access the system monitor, so I just have to turn my laptop off and on again
     .AVI files won't play even with codecs installed. Totem and VLC Media player open, but as soon as the movie loads, they automatically close
     
2) Root user problems
     Every time I try to use the graphical login screen to log in as root, it just displays some text on a black screen (boot-type text) that I never have too much time to read, and then displays the login screen again. I managed to fix this once by completely logging out and then logging back in - is this supposed to work like that?

3) Ndiswrapper
     Once and for all, can someone tell me how to get this to load on startup? Every time I try to run "ndiswrapper -m" in the terminal, I just get "module configuration already contains alias directive." I would settle for figuring out how to run code in the terminal on startup

I think that's it for now. I know that the answers to these questions may be out there, but I've searched for hours and found nothing helpful. Side note: even with all these problems, I'd rather use Ubuntu than Windows XP!

---

### Post by frogitts on 2007-05-11
> 3) Ndiswrapper
Once and for all, can someone tell me how to get this to load on startup? Every time I try to run "ndiswrapper -m" in the terminal, I just get "module configuration already contains alias directive." I would settle for figuring out how to run code in the terminal on startup

Well, I've figured one of my problems out! Here's what happened:

I needed to run these three lines every time I started in order to get my wireless to work:
```
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

I found that I could blacklist the bcm43xx driver (which is effectively the same as rmmodding it - rmmod removes it while blacklist prevents it from starting) by editing /etc/modprobe.d/blacklist to include the line
```
blacklist bcm43xx
```

To this, I typed 
```
sudo gedit /etc/modprobe.d/blacklist
```

into the terminal, which gave me privileges allowing me to edit that file.

However, just to be sure, I also wanted to run those same lines of code on startup. To do that, I edited /etc/rc.local using the same command (sudo gedit) as before. I just inserted my code before the line "exit 0"

[Thanks to klep and kangol69 for those answers! ]("http://ubuntuforums.org/showthread.php?p=2634754#post2634754")

---

