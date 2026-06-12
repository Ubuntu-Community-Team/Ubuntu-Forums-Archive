---
title: "X problems when upgrading to Ibex"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by Mayfairy on 2009-03-22
I just upgraded from Hardy to Ibex. Everything seemed to go quite well but after I rebooted I got an error saying "(EE) Default device is not PCI"

I fiddled with the settings a lot and finally found some threads to help me (used another computer). 
What I did was apt-get remove --purge Nvidia* after which I downloaded the latest Nvidia drivers 180.29 and installed them. 
From lspci | grep VGA I got an address 2:0:0 which I added to my xorg.conf as busid "PCI:2:0:0" after which starting X gave me a login screen that flickered in black and white occasionally showing me the login screen behind it. I couldn't enter my login details.

After some more googling I changed the HorizSync and VertRefresh to reflect those of my monitor (Samsung SyncMaster 226BW). Starting X after that showed my background and it tried to load gnome-panels which disappeared soon. I saw a mouse cursor that turned into a loading clock every once in a while and some outlines of windows were flickering on the screens. This went on for quite a while.  

Then I Ctrl-Alt-F1'd into tty and got a message saying something about module type1 not loaded. With some google advice I commented module type1 out from xorg.conf and rebooted. 

After this the black and white blinking on my login screen happened again. No matter what I did (even copying over my xorg.conf with the settings that got me to desktop earlier) I couldn't make it go away and I'm still getting this blinking. 

Any advice on what to do here?

EDIT: tty is giving me 4 lines saying "no block devices found"

---

### Post by FrostDust on 2009-03-22
What model video card are you using? Some of the older Nvidia and ATI cards aren't supported by the new version of Xorg in Ibex.

---

### Post by Mayfairy on 2009-03-22
Finally an answer. Thanks! :)

I'm using Club3D's Geforce 6600 GS.

I read that some people with really new cards had similar problems though, at least to the "remove every Nvidia thing and fetch the VGA address from lspci info" part.

---

### Post by FrostDust on 2009-03-22
After a bit of googling, I found [this post]("http://www.nvnews.net/vbulletin/showthread.php?t=130440&highlight=6600") on the Nvidia forums. Short story is that even though it's listed as being compatible with a certain driver, there may a bug which inhibits the card from functioning properly.

Try a different driver version.The posting mentions 180.37 and 185.13 as working with 6600s

---

### Post by Mayfairy on 2009-03-22
No go. I've fiddled around with the settings a lot and seem to have experienced nearly every error message there is. 
Can't do othan than try and try.

EDIT: Latest info:
I can get to login screen, I can see the Nvidia logo before that, resolution seems to be ok, BUT I'm seeing a black screen for 1 second, then a really quick white screen followed by even quicker view of my login screen after which again 1 sec black screen and over again. 

Choosing the right HorizSync and VertRefresh rates on xorg.conf corrected this earlier but now that I look at them they're still the right ones and this keeps happening.

---

### Post by Mayfairy on 2009-03-24
Finally managed to get my box working. As the most radical measure I did a clean install of Ibex on top of my old install without formatting it. 
Good thing I kept my /home on another partition. 
Took a bit fiddling around after that to get things working but in the end it turned out ok. 

One thing I noted though is that I couldn't make desktop effects work with my Nvidia 6600GS card no matter what I did. 

Luckily I had already ordered a new Nvidia 9800 GT card which I installed and voila, when I logged in I had desktop effects working really nicely.

---

