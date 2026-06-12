---
title: "Another flash problem"
date: 2005-11-10
forum: General Help
---

### Post by pxgray on 2005-11-10
Hello,
     This is my first post to the Ubuntu forums, and let me just say that I have used many great Linux distributions before, but Ubuntu has definitely been the greatest so far.  I was so surprised how everything pretty much worked right out of the box, and the only thing that needed to happen was tweaking.  I am running into one problem, however, and I just can't seem to find anyone having the same problem.  After installing the flashplayer-mozilla package, Firefox crashes whenever any site tries to load a flash animation.  If I use Konqueror it's a little happier, the flash simply displays as a white box, and it appears to actually load the player, as right clicking the box brings up the Flash menu, and it's possible to click links inside the flash.  No picture and no sound comes out, however.  Has anyone had this problem before?  Any ideas?  Thank you for your help.

pxgray

---

### Post by bryan986 on 2005-11-10
I suppose you could try the flashplayer-nonfree package

---

### Post by Kapre on 2005-11-10
[QUOTE=pxgray]Hello,
     This is my first post to the Ubuntu forums, and let me just say that I have used many great Linux distributions before, but Ubuntu has definitely been the greatest so far.  I was so surprised how everything pretty much worked right out of the box, and the only thing that needed to happen was tweaking.  I am running into one problem, however, and I just can't seem to find anyone having the same problem.  After installing the flashplayer-mozilla package, Firefox crashes whenever any site tries to load a flash animation.  If I use Konqueror it's a little happier, the flash simply displays as a white box, and it appears to actually load the player, as right clicking the box brings up the Flash menu, and it's possible to click links inside the flash.  No picture and no sound comes out, however.  Has anyone had this problem before?  Any ideas?  Thank you for your help.

pxgray[/QUOTE]

pxgray - can u try loading Epiphany (also a mozilla browser) and see if the result is the same. Install it via Synaptic. If you have time, maybe you can also read [this]("http://www.ubuntuforums.org/showthread.php?t=84652&highlight=firefox+crash") thread.

K

---

### Post by pxgray on 2005-11-10
I have tried directly downloading the file from Macromedia's site and installing it with the included script.  I believe that the flashplayer-nonfree package is simply a replacement for the included script.  With that version installed I get the same behavior as with the flashplayer-mozilla package.

pxgray

---

### Post by Kapre on 2005-11-10
[QUOTE=pxgray]I have tried directly downloading the file from Macromedia's site and installing it with the included script.  I believe that the flashplayer-nonfree package is simply a replacement for the included script.  With that version installed I get the same behavior as with the flashplayer-mozilla package.

pxgray[/QUOTE]

pxgray - Would you mind installing Automatix? This has all the plugins and it worked for me. Maybe you can give it a try.
K

---

### Post by pxgray on 2005-11-10
> pxgray - Would you mind installing Automatix? This has all the plugins and it worked for me. Maybe you can give it a try.
 K

I originally installed it from the Automatix script, and had the same behavior.  I removed that and installed the website version, and then removed the website version and manually installed the flashplayer-mozilla package via apt-get.

pxgray

---

### Post by pxgray on 2005-11-10
*bump*

Anyone have any ideas?  I'd really like to have working flash.

pxgray

---

### Post by Mordok on 2005-11-10
I don't know if this has any bearing on anyone's problem but I'll throw it out anyway, just in case.  I use Ubuntu Breezy 64 and Macromedia's Flash doesn't work in the 64 bit environment.  Someone mentioned there were alternatives and I installed libflash0C2, libflash-mozplugin and libswfdec0.3.  It seemed to work for a few days and then last night, out of the blue, Firefox kept dying at this one site.  Today I did a search in Synaptic and found swf-player that hadn't been installed and so I installed it and went back to that site and it seems all is well.  At least for now.  Maybe tomorrow it will be broken again, but I'll face that when I get to it.

Bottom line would be to search Synaptic for things like "flash" and "macromedia" and see what pops up that might apply and install it and see what happens.  Good luck.

---

### Post by pxgray on 2005-11-10
[QUOTE=Mordok]I don't know if this has any bearing on anyone's problem but I'll throw it out anyway, just in case.  I use Ubuntu Breezy 64 and Macromedia's Flash doesn't work in the 64 bit environment.  Someone mentioned there were alternatives and I installed libflash0C2, libflash-mozplugin and libswfdec0.3.  It seemed to work for a few days and then last night, out of the blue, Firefox kept dying at this one site.  Today I did a search in Synaptic and found swf-player that hadn't been installed and so I installed it and went back to that site and it seems all is well.  At least for now.  Maybe tomorrow it will be broken again, but I'll face that when I get to it.

Bottom line would be to search Synaptic for things like "flash" and "macromedia" and see what pops up that might apply and install it and see what happens.  Good luck.[/QUOTE]

I tried installing the libflash-mozplugin package and its dependencies, and it will not load in Firefox or Konqueror either.  This is becoming quite a mystery to me because I have never had problems like this running the flash plugin in Linux.  I appreciate the help guys, I'm still working on it.

pxgray

---

### Post by kvaju on 2008-06-09
did you solve the problem?
my cpu is 100% alvays when i goto flash site.

---

