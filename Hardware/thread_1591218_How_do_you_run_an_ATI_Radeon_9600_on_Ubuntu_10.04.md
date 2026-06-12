---
title: "How do you run an ATI Radeon 9600 on Ubuntu 10.04?"
date: 2010-10-08
forum: Hardware
---

### Post by ZeroCore on 2010-10-08
Okay, lately I've been trying to get my graphics card to run on Ubuntu 10.04, and I have been unable to do so.

I have Ubuntu 10.04, obviously, as well as an ATI Radeon 9600; it's an older card but the only one that I have and I can't afford a new graphics card right now and won't be able to in the foreseeable future for a long, long time. That said, I really NEED to figure out how to run the one that I have.

I know that the driver ATI has online won't exactly work on 10.04 seeing as how the 9600 class of graphics cards is now considered legacy hardware by ATI. However, it doesn't change the fact that I need to figure out some means of getting this card to work. 


Any help would be appreciated. 


Anyway, just to reiterate the situation:

Software: Ubuntu 10.04
Hardware: ATI Radeon 9600 (just a standard 9600, not the pro or mobile versions)
Hardware Maker: ATI
Type of Hardware: Graphics card

---

### Post by mastablasta on 2010-10-09
What exactly is not working? What did you do so far? 

I am asking because i have ATI Radeon 9600XT and it works out of the box with opensource drivers. works quite well actually...

edit: does it work in other operating systems?

---

### Post by ZeroCore on 2010-10-09
Here's the issue:

1: Desktop effects don't work, even though I have the card plugged in.
2: Whenever I try running any of my games (games that I'd normally run on windows and on windows with steam), their menus will work just fine BUT when I go to start a game, the game will load to 99%, freeze, and then quit. The operating system will still work afterwards, the game just stops running. In addition to this, the start-up menus for some steam games (like portal) will feature a start menu which actually shows an in-game environment. In this in-game environment start-up menu, several objects that are supposed to be there in game are missing. 

AND no matter what I do, this is ALWAYS the case.

---

### Post by mastablasta on 2010-10-10
> **ZeroCore said:**
> Here's the issue:

1: Desktop effects don't work, even though I have the card plugged in.

driver issue. you could try and upgrade to latest opensource drivers by adding the propper PPA.
read more here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Did you maybe try to instal Fglrx (official ATi drivers)? Because you shouldn't.

> 
2: Whenever I try running any of my games (games that I'd normally run on windows and on windows with steam), their menus will work just fine BUT when I go to start a game, the game will load to 99%, freeze, and then quit. The operating system will still work afterwards, the game just stops running. In addition to this, the start-up menus for some steam games (like portal) will feature a start menu which actually shows an in-game environment. In this in-game environment start-up menu, several objects that are supposed to be there in game are missing. 

AND no matter what I do, this is ALWAYS the case.

how are you running these games? Through WINE i guess?
This may also be a driver issue. Drivers for these older cards were nto made by ATi but by community and are sort of drivers iin the making. so some things might not work/run perfectly. Perhaps what you could do is check the game settigns and maybe tweak the game performance a bit. Since i am not familiar with those games you play (haven't got arround to Half life 2....) i can't give any more specific advice on what to tweak.

---

### Post by ZeroCore on 2010-10-10
> **mastablasta said:**
> driver issue. you could try and upgrade to latest opensource drivers by adding the propper PPA.
read more here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Did you maybe try to instal Fglrx (official ATi drivers)? Because you shouldn't.



how are you running these games? Through WINE i guess?
This may also be a driver issue. Drivers for these older cards were nto made by ATi but by community and are sort of drivers iin the making. so some things might not work/run perfectly. Perhaps what you could do is check the game settigns and maybe tweak the game performance a bit. Since i am not familiar with those games you play (haven't got arround to Half life 2....) i can't give any more specific advice on what to tweak.


Thanks for the link; now I have more questions though.

1: is Accelerated 3D support the same as a driver?
2: Where can I find these open source drivers?
3: my card says that it's a RV350 card. Is RV350 a type of driver?

---

### Post by mastablasta on 2010-10-10
> **ZeroCore said:**
> Thanks for the link; now I have more questions though.

1: is Accelerated 3D support the same as a driver?
no. driver is "driving" the hardware :-) it enables 3d acceleration on newer card. it makes it work.
> 
2: Where can I find these open source drivers?
open source drivers are installed by default. however, newer version is available through PPA (see the link i posted). btw have you tried today's new ubuntu  version. it seems it works better with my card. maybe it has updated drivers?! i don't know,
 > 
3: my card says that it's a RV350 card. Is RV350 a type of driver?
it means your card uses RV350 graphics chip - GPU.

---

### Post by ZeroCore on 2010-10-10
> **mastablasta said:**
> no. driver is "driving" the hardware :-) it enables 3d acceleration on newer card. it makes it work.

open source drivers are installed by default. however, newer version is available through PPA (see the link i posted). btw have you tried today's new ubuntu  version. it seems it works better with my card. maybe it has updated drivers?! i don't know,
 
it means your card uses RV350 graphics chip - GPU.


Once again, thanks for the info.

Anyway, I knew what a driver was, I was just wondering if the software I'd mentioned was one. I should have asked if it was a driver (my mistake, sorry that I wasn't clear on that). 

When you say Ubuntu's new version, you mean 10.10 right?
 
I don't have that version; lucid lynx is the only one that I have. 



Also, I checked my machine again, and it says that I do have the proprietary software on there, BUT it doesn't really read it as being there and working (my guess is because the proprietary driver is incompatible with my card, which makes sense, as the driver says that my card isn't supported). 

You said that the open-source driver is included with 10.04? If that's the case, where can I find it on the hard disk, and do I need to access it to activate it (if so, how do I)?

---

### Post by mastablasta on 2010-10-11
EDIT: Forgot to mention yet by new version i mean Ubuntu 10.10.
 
Why try it? for example the system loading screen on 10.04, doesn't seem to work well with my ATI, however i tried 10.10 live and worked flawlessly. it seems they fixes a few things in this new release. i just hope they add same fixes to 10.04.
 
> **ZeroCore said:**
> 
 
Also, I checked my machine again, and it says that I do have the proprietary software on there, BUT it doesn't really read it as being there and working (my guess is because the proprietary driver is incompatible with my card, which makes sense, as the driver says that my card isn't supported). 
 
fglrx is ATI Catalyst driver. this card is in legacy support. and the driver the ATi provides is for old X.org. It doens't support new one that is in new Ubuntu.
 
> 
You said that the open-source driver is included with 10.04? If that's the case, where can I find it on the hard disk, and do I need to access it to activate it (if so, how do I)?
 
 
This i don't exactly know. to the best of my knowledge it is part of the kernel and is configured by using a text file called xorg.conf ([http://en.wikipedia.org/wiki/Xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf)). someone else will have to give advice on this since it's really been a loooooong time i configured one of those.
 
Windows XP for example uses the same kernel, so older drivers work, while here everyhting is upgraded. Older ATI drivers don't work, but community made opensoruce ones that are included in kernel.
 
Basically if you have any ATI drivers installed you need to remove them and purge them. then opensource ones should be used automaticly i believe.

---

### Post by ZeroCore on 2010-10-11
> **mastablasta said:**
> EDIT: Forgot to mention yet by new version i mean Ubuntu 10.10.
 
Why try it? for example the system loading screen on 10.04, doesn't seem to work well with my ATI, however i tried 10.10 live and worked flawlessly. it seems they fixes a few things in this new release. i just hope they add same fixes to 10.04.
 

 
fglrx is ATI Catalyst driver. this card is in legacy support. and the driver the ATi provides is for old X.org. It doens't support new one that is in new Ubuntu.
 

 
 
This i don't exactly know. to the best of my knowledge it is part of the kernel and is configured by using a text file called xorg.conf ([http://en.wikipedia.org/wiki/Xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf)). someone else will have to give advice on this since it's really been a loooooong time i configured one of those.
 
Windows XP for example uses the same kernel, so older drivers work, while here everyhting is upgraded. Older ATI drivers don't work, but community made opensoruce ones that are included in kernel.
 
Basically if you have any ATI drivers installed you need to remove them and purge them. then opensource ones should be used automaticly i believe.


In short; purge fglrx and use X.org, right?

---

### Post by mastablasta on 2010-10-11
yes. maybe purge & restart will also do the trick.

---

### Post by ZeroCore on 2010-10-11
> **mastablasta said:**
> yes. maybe purge & restart will also do the trick.
 
 
Okay, I'll try that the next time I'm using the computer with the issues I'm having (which will be this next weekend).
 
Anyway, I was just wondering something else as well:
 
I can get this open-source driver from the Ubuntu software center, correct?
 
I got something on there which was named X.org, and it listed itself as a driver for ATI cards. I installed it as well as a few other things which were listed as X.org. When I went into the administrator section, I was a tad surprised to see the ATI catalyst control center there. When I tried to activate that, it said that either the driver was not installed or had malfunctioned. 
 
Any ideas as to what's going wrong?

---

### Post by Yellow Pasque on 2010-10-11
You tried to install the proprietary ATI driver on a system without a supported card. To recover: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

---

### Post by ZeroCore on 2010-10-12
> **Temüjin said:**
> You tried to install the proprietary ATI driver on a system without a supported card. To recover: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)
 
 
Okay. I'll do this and then try getting X.org to function.

---

