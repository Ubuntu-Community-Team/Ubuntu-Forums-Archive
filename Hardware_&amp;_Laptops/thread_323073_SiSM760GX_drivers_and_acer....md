---
title: "SiSM760GX drivers and acer..."
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by YolLuTRaC on 2006-12-21
Hello everyone.

This is concerning the SiSM760GX and BCM4318 devices found at least in the acer aspire 3000 series under Dapper Drake. (Ubuntu 6.06) for the new ones.

I'm quite new with ubuntu dapper and had multiple problems making my laptops working well. The two main problems that occured to me are the video card and the wireless. It occurs that none of these two have any support from there own companies i.e. Broadcom and SiS.. Broadcom is for legal reasons and SiS the just rely everything to the resellers like acer for example. Acer does not give much support for the linux users for probably lucratic reasons i guess. For these reasons which seems to be quite enough since a lot of people just give up after some time left me to a conclusion.

WE SHOULD ALL FLOOD THE ACER SUPORT WEBSITE AND ASK THEM TO GIVE US SUPPORT!

Sorry for the caps be I wanted people to read this specific sentence before beeing bored...

So here we are I'm not saying it will solve the problem but if I would be them and have a lot of costomers that would ask me support for one OS I would invest some time in it... Anyway for the broadcom part I found finally after a long reasearch that some people did a quite good job. For the BCM4318 wireless card... I attached a zip file that will enable the wireless card. I don't quite remember on which forum i found it but it works. Untar it and run the shell script. After just follow the normal instructions in the Dapper Drake starter guide for wireless tools/wpa/whatever...

For the screen resolution reconfigure xorg using the sis driver and it should do weird stuff but still give you more choice. Search on the forum and you'll find how to do it quite easily.

Don't forget to go write something to acer!

Also if by any chance someone finds out a way to make opengl and my SiSM760GX to be compatible and also to enable my 3D acceleration that'd be sweeeeeet.

Yours,

Gabriel

---

### Post by compuguy1088 on 2007-01-07
Yes, I found myself in a similar predicament with my Aspire 3003 LCi, which has the Broadcom 4318, and the SiS 760 graphics. I tried to get the wireless to work with the bcm43xx, which worked so poorly, it was useless. I didn't really want to use ndiswrapper, so I decided to ditch the broadcom card, and bought a Intel 2200 BG mini-pci card, which is overall much better. On the graphics front, there really is no solution. There is only one person, to my knowledge that is working on drivers for SiS cards, and no real push on the developer front to improve them, because of the fact that SiS does not want to release the specifications of there cards. Though this has not prevented people from writing drivers (like the bcm43xx) that have turned out decent, though needing some work, there was a larger percentage of people with broadcom cards that pushed this to occur. In reality, the 760 chipset, is a really miserable pieice of junk, but in my mind any accelleration is better than none :mrgreen:. Anything that is 3d intensive, right now just pushes it to the CPU (because of the fact its using software rendering; ala Mesa). Basically thats my whole of a story, the laptop works fine for what it does, but if would be nice if the graphics worked completely than half patched up.....

---

### Post by sammulder14 on 2007-02-15
Hey guys,

Me my selve owns a aspire 3000, with serveral games i had trouble  with error,s leading back 2 direct x and the video card SiSM760GX(D3DERR etc).
I can,t make sence of it  simply cause some   games with graphical challeges do run and  some lower grapic  games etc  just don,t run and SiS and the game support of the games in qeustion just don,t offer any information.

If u find any usefull patches etc 2 fix these problems post em :P.

Greetings sam,

---

### Post by TiLK on 2007-04-07
Hi guys. I have same problem as you. There are some Linux drivers on SiS webside, but no one is for SiSM760GX. But there are similar series anyway. Couldnt help us, even its not for ubuntu?

[http://www.sis.com/download/](http://www.sis.com/download/)

---

