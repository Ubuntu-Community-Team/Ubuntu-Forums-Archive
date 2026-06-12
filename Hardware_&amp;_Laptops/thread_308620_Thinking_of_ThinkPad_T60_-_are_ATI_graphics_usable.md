---
title: "Thinking of ThinkPad T60 - are ATI graphics usable?"
date: 2006-11-28
forum: Hardware &amp; Laptops
---

### Post by meldroc on 2006-11-28
I'm currently in the market for a new laptop, and have my eyes on a ThinkPad T60, with a Core 2 Duo and an ATI Mobility Radeon X1300 or X1400, and is rumored to work well with Linux.  The alternative graphics chip on ThinkPads is the Intel Graphics Media Accelerator 950, which I'm unthrilled with - Intel graphics are fairly sucky as far as 3D performance goes, though the drivers are open-source.  No, Lenovo doesn't offer NVidia graphics on ThinkPads.  Yes, I'll be gaming on this laptop, so I need that 3D hardware acceleration.

When I've talked to various Linuxheads, I'm hearing a lot of "OMG, ATI's Linux drivers SUCK!!!  STAY FAR AWAY FROM ATI!!!"  Then in other places, I see a lot of people who are able to make ATI work in X, being able to run beryl and other cool eye-candy.

So I need to know before I fork over $$$$$ on a laptop - are the ATI drivers usable?  Now's the time for me to know about all the problems.  If I'm going to be constantly fighting with the ATI card, having X crashes, buggy rendering, etc., I'm going to lose patience very quickly.  I prefer to use NVidia cards - I have them in my desktop boxes, and say what you want about NVidia keeping their drivers closed-source, but those drivers do work reasonably well.  I just upgraded to Edgy on my desktop box, and I have yet to try things like beryl, but I can get my games and screensavers and such working with 3D acceleration without things blowing up in my face.

If ATI's drivers are buggy or slow enough to make it not worth the trouble, the alternative is to go with the Intel graphics, which I'm not thrilled with, because they'll be pretty slow when compared with ATI or NVidia.  Unfortunately, Lenovo doesn't give you the option of a ThinkPad with NVidia graphics, so if I can't get ATI working, I'll have to start looking elsewhere for a laptop that does have NVidia.

---

### Post by meldroc on 2006-11-28
Bump.  One thing I've read googling around is that the ATI drivers can't handle suspend/hibernate, meaning that if you close your laptop to kick it into suspend mode or hibernate mode, when you open it up, instead of waking up correctly, the display is scrambled, and you're forced to reboot.  Same thing if you try to switch virtual terminals - causes a crash.

This is not acceptable.  Has anyone had success making these feature work?  Suspend/hibernate's pretty important in a laptop.

---

### Post by pveith on 2006-11-28
I use an ATI graphic adapter (an Asus X300) as on my desktop and the open-source driver, which work pretty good (even with beryl). So i can not second the ATI Bashing, but than again i not much of a 3d-gamer and google earth is onlay crawling...

A freind of mine has an Asus laptop with an ATI card an can suspend and hibernate. So i can not second the ATI does not support suspend/hibernate...

Hope that helps.

---

### Post by d3v1us on 2007-02-03
ThinkPad T60
1.66ghz CoreDuo
1gb ddr2
ATI x1300 64mb
Ubuntu Edgy

i have had very little luck getting ATI drivers working on this thing. i've been through *so* many threads and wiki's.. i just can't get it straightened out.  i can't get the aticonfig to work, there's this little line that perpetually hovers under my mouse, and i still can't tell that there is even a more-than-integrated video card (although i could see it when i used Dapper).. but i can change the resolution now (seems like a luxury).  i'm not very experienced with linux in general, but there are threads for everything, so i guess i rely on them a bit.  none of my friends that are avid linux (Ubuntu and others) have been able to help me either.  i know there are threads for 6.06, but not 6.10 (at least that are working for me).  good luck with yours if you end up buying it though.

---

### Post by s3lf on 2007-02-05
Hi!

I've no real graphic-problems .. I installed edgy according to this nice howto:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60)

Unfortunately the most recent beryl doesn't work - the one before the most recent one worked .. strange .. but that's not very important to me :)

For suspend/hibernate I had to stop/start powernowd.

[PS: Can you please tell my how many battery power your T60 notebooks consume (
(cat /proc/acpi/battery/BAT0/state  while not on AC)
My T60 consumes in Ubuntu > 15-16W even if I don't use it .. WindowsXP only 11W ! ]

---

### Post by Aifel on 2007-02-05
On my box my card works very well. I can run Beryl without issues, and can run most 3D games without major speed reduction. Some games don't work as well as others however (Neverwinter Nights=SUCK on an ATI Card). Im using a 128 MB Radeon 9200 PRO, btw. Of course, this is with the open source "ati" driver, so who's to say. I also know for a fact that FGLRX doesn't work well with Cedega or Neverwinter Nights at ALL. Running NWN w/fglrx causes he screen to mess up, and requires a quick X reboot.

I don't know anything about the suspend/hibernate issues, as I'm not using a laptop.
Good luck if you buy it.

---

### Post by Lorenz on 2007-05-13
I'm using an IBM T60 with an ATI x1300. 
No problems, both Compiz and Beryl work really fine :)

---

### Post by tux_rox on 2007-05-13
The brand new T61's come with nVIDIA Quadro NVS 140M cards.

Basically the same as the T60's, but with 14.1 widescreen and some other new features.

Link:  [http://shop.lenovo.com/SEUILibrary/controller/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=F2F5363C71FA4D61B176AD5FB80FA5D8]("http://shop.lenovo.com/SEUILibrary/controller/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=F2F5363C71FA4D61B176AD5FB80FA5D8")

---

### Post by Alvinius on 2007-05-14
Quadro cards are not gaming cards if that is what he wants to use it for.  But you might wait a bit, it looks like AMD (ATI) will soon deliver open graphics drivers. [http://enterpriselinuxlog.blogs.techtarget.com/2007/05/09/amd-will-deliver-open-graphics-drivers/](http://enterpriselinuxlog.blogs.techtarget.com/2007/05/09/amd-will-deliver-open-graphics-drivers/)

---

### Post by reidbold on 2007-05-14
That 140m is is a DX10 card, based on 8400m core. Will hang around with GF7600 & ATI X1600. It should game nicely for a while :)

---

### Post by sfynx on 2007-05-22
Hello! I have a T60 with an ATI card and I have had no luck getting compiz to work with the ATI drivers. In fact the resolution gets stuck at 800x600. If you have had success with an install, can you post any specific tips?

Thanks in advance!

---

### Post by opioid on 2007-08-29
NVIDIA 140M rocks, my advice is forget ATI, get discrete graphics :)

---

### Post by CURaven on 2007-09-07
> **Lorenz said:**
> I'm using an IBM T60 with an ATI x1300. 
No problems, both Compiz and Beryl work really fine :)


Lorenz

Can you post your config?  or point me to a webpage with instructions on getting BERYL to work.  I'm not a complete noob, I've had beryl working on my desktop.  I would love to use it on this T60.

---

### Post by Murdo on 2007-09-08
i would like to do the same, i have t60 with ati x1300, any help please

---

### Post by ramnarayan on 2008-02-17
> **Lorenz said:**
> I'm using an IBM T60 with an ATI x1300. 
No problems, both Compiz and Beryl work really fine :)

what version of Ubuntu

just upgraded to 7.10 and the graphics card is giving trouble

wish i had stuck to 7.04 which was working very beautifully

ram

---

### Post by Wynne G Oldman on 2008-03-09
Despair not. I tried Gutsy on my T60, no dice. I downloaded the Hardy beta, and the graphics work great. You can even install the latest ATI Catalyst drivers with Envy, if you wish. About bloody time! Seriously, much respect to the Devs for getting it together on this one. You've just doubled the amount of people who will be able to use Ubuntu!:guitar:

---

### Post by astrauch1968 on 2008-03-12
Hello Wynne,
your post gives me hope. I have a t42p (which has also an ati driver) and suspend/hibernate also does not work. So I will reboot more often and wait for 8.04. :-|

---

