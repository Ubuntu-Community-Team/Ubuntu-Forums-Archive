---
title: "ATI radeon xpress 200M"
date: 2006-10-06
forum: Hardware &amp; Laptops
---

### Post by Tyrael_Odium on 2006-10-06
Ok guys, here is the problem.

I am a fedora user (i dont know what you debian people think of us, but i know that suse people hate fedora users), and i have a pretty good install, i have everything working just the way i want it to on my laptop (a Compaq Presario R4000 series laptop, detailed specs will come later).
I really like linux, and i know that most linux distros are close to the same (worded wrong, what i mean is that all linux distros have the same basic functionality, and they all have their own distinct features). My real problem here is that i do not have any video support on my fedora partition (i am suck at 800*600 YUCK). The video card on my laptop is (you guessed it) the ATI Radeon Xpress 200M with 128MB dedicated Vram (100% of my system ram is being used as system ram).

Now i have tried to install the drivers using YUM, and following the guide at [www.fedorafaq.org](www.fedorafaq.org)  and what that did is it installed the drivers, and then when i tried to do "init 3" to get them working, it got caught in an endless loop of checking over this certan file, so i decided to jsut reboot my laptop, and when it tried to boot up, it just crashed out, and it wouldnt even let me go into text mode to try to get rid of the drivers. So then i did a clean install and got everythign working again, and then i tried to install the .run file from [www.ATI.com](www.ATI.com) and i followed their guide. It installed and it didnt give me any error messages, but i got up to a step where they wanted me to run a command, and when i tried i got an error message along the lines of "file does not exist" or something like that. 

(the exact command that they wanted me to run was "Launch the Terminal Application/Window and run /usr/X11R6/bin/aticonfig --initial to configure the driver")

so i moved to the previous driver pack, thinking that the radeon 9000 driver would work (to my understanding they are almost the same card), but i got the same crap. 

And both times when i reboot my OS, gnome was completely messed up. It would not allow me to open up more than 1 app at a time, and i could not minimize or cut or paste from one app to another, and every time i pressed the show desktop button i got an error message saying "desktop manager does not allow for the "show desktop" feature, or you do not have a desktop manager installed" (wierd huh). 

So i am wondering if either Debian or Ubuntu has an apt-get command to install the ati drivers properly so that i can avoid this problem? or if it will actually work on ubuntu. I have already ordered my shipit cd's and they should arrive in about a month (from what i have heard). I am really getting them for the live cd feature, incase something were to happen to my windows partition (hey so sue me, i just need to for some things).

If somebody could help me out i would really appriciate it. Thank you in advance.

---

### Post by Tyrael_Odium on 2006-10-07
bump

---

### Post by Frogger on 2006-10-07
Ubunutu has the same problem
But there is a simple work around.
Download the newest driver (the old one, as you have discovered) does not have support for the X-series of chips.
Then (here is the complex work around I spend 3 days trying to figure out) gain root access in a terminal (FC this is done with su, in Ubuntu this is done by typing sudo before the command) and type the command

nautilus

Then navigate to the folder and start the installer.

Thats it, it will install fine.

---

### Post by Tyrael_Odium on 2006-10-09
i will give it a shot and tell you how it works out. thank you for your help

---

### Post by medievalvent on 2007-11-20
I wasn't able to get the right resolution on my external monitor w/ 200M. I just ditched the fglrx completely in favor of ati drivers that came with Ubuntu. I have to say, it worked very well. I now have an integrated desktop (metacity).

---

