---
title: "Display problems on Amilo L7320"
date: 2009-05-25
forum: Hardware
---

### Post by OkoSanto on 2009-05-25
Hi,

currently, I'm running Kubuntu 8.10 on a Fujitsu-Siemens Amilo L7320 notebook. Screen size is 15.4", and the optimal resolution, 1280x800, displays fine. 

However, when I want to display lower resolutions (1024x768 to connect to a beamer/external monitor, or right now, 640x480 to play starcraft through wine), the image gets all jumbled. Hard to describe, but basically, it looks just like this picture (taken from another, unsolved, post on the forum): 
[http://i.servut.us/i/Kuva064.jpg]("http://i.servut.us/i/Kuva064.jpg") (taken from possibly related post [http://ubuntuforums.org/showthread.php?t=1151852&highlight=amilo+xorg]("http://ubuntuforums.org/showthread.php?t=1151852&highlight=amilo+xorg") ).

I'm thinking it has something to do with the monitor, since the problem is not there when I take a screenshot (i.e., the screenshot looks just as if everything were fine, but the image on the screen is a mess). I'm thinking this might be solved with the correct Xorg.conf settings, maybe refresh rates?

I've been trying to find out the refresh rates, but ddcprobe returns "edidfail"... any hints? Do these rates matter much with an LCD screen, anyway?

EDIT: for completeness' sake: video card is a VIA unichrome, and I'm using the openchrome driver (at the moment I don't think it is a video card driver, though I wouldn't really know)

---

### Post by WabbitTwax on 2009-08-19
i have a similar problem. can you please post your xorg.conf file here?

---

### Post by Phillip Hutchinson on 2009-10-22
> **OkoSanto said:**
> Hi,
 
currently, I'm running Kubuntu 8.10 on a Fujitsu-Siemens Amilo L7320 notebook. Screen size is 15.4", and the optimal resolution, 1280x800, displays fine. 
 
However, when I want to display lower resolutions (1024x768 to connect to a beamer/external monitor, or right now, 640x480 to play starcraft through wine), the image gets all jumbled. Hard to describe, but basically, it looks just like this picture (taken from another, unsolved, post on the forum): 
[http://i.servut.us/i/Kuva064.jpg](http://i.servut.us/i/Kuva064.jpg) (taken from possibly related post [http://ubuntuforums.org/showthread.php?t=1151852&highlight=amilo+xorg](http://ubuntuforums.org/showthread.php?t=1151852&highlight=amilo+xorg) ).
 
I'm thinking it has something to do with the monitor, since the problem is not there when I take a screenshot (i.e., the screenshot looks just as if everything were fine, but the image on the screen is a mess). I'm thinking this might be solved with the correct Xorg.conf settings, maybe refresh rates?
 
I've been trying to find out the refresh rates, but ddcprobe returns "edidfail"... any hints? Do these rates matter much with an LCD screen, anyway?
 
EDIT: for completeness' sake: video card is a VIA unichrome, and I'm using the openchrome driver (at the moment I don't think it is a video card driver, though I wouldn't really know)
 
Sorry to bother you but how did you get your screen to display 1280 x 800 mine is set at 1600 and you can not change it!
 
Regards
 
Phillip

---

