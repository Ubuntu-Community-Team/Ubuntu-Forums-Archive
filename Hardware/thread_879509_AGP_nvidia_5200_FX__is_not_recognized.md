---
title: "AGP nvidia 5200 FX  is not recognized"
date: 2008-08-04
forum: Hardware
---

### Post by marufsiddiqui on 2008-08-04
Hi all,

I'm facing a problem here regarding my agp card. My AGP card is **nvidia 5200FX **I've just installed Ubuntu 8.04, after installation i got 800x600 desktop resolution but i usually use 1024x768px, then i try to change the resolution to 1024x768px by using Desktop Resolution but I could not find 1024x768px there was highest 800x600, what can i do now? what can the problem here?

I like to mention a few things. I've installed Kubuntu previously & it has 1024x768px. I'm still using it, but for the last 2/3 days i found that it also changed the resolution to 800x600 & i cant change it. (NB: I install this new Ubuntu in new drive, I've also WinXP SP2 but it does show 1024x768px, no prob here). that's why i'm really confused that what the problem could be. Is it with my AGP card? if yes then it should create problem in WinXP too.

plz give me a solution plz

---

### Post by Ncaronte on 2008-08-09
I have the same problem that you.
Fx5200 in windows go fine, but in ubuntu you have to install last nvidia drivers.
I tried by official and non-official drivers, at the end It's the same black screen in my ubuntu login screen.
Anyway I'm keeping trying.

---

### Post by Bittergal on 2009-02-11
I have the same problem.  I think the drivers tell xorg it's a pci card?  From Xorg.0.log:  
(II) Loading /usr/lib/xorg/modules//lib[COLOR="Red"]pci[/COLOR]data.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0

---

### Post by expelledboy on 2009-02-13
I have exactly the same problem. Has anyone solved this yet? What is amazing is that without the drivers installed in my case I can get a higher resolution. :/

---

### Post by crigon on 2009-02-16
[quote=expelledboy]I have exactly the same problem. Has anyone solved this yet? What is amazing is that without the drivers installed in my case I can get a higher resolution. :/[/quote]
Me too...

---

### Post by nixIT on 2009-02-16
I am too having a problem with the FX5200 and Ubuntu Hardy.  I followed all steps, even manually installing the 173 driver from nvidia's site.  When my system boots, I get the (x)ubuntu loading screen, then my monitor appears to go "out of sync".

I reboot, hit ESC and select the repair (I think) option and run xfix, which rebuild xorg.conf.  I can then load xubuntu, but my resolution is lower than my monitors native/default resolution.

I see some people have had success with this card and Ubuntu, I also had success with this card and Kubuntu back in the 7.04 days.

I have an older system AMD 1.3ghz but my monitor is a DELL 207WFP (20" widescreen).  The FX 5200 supports a resolution high enough for my monitor, the question is, how can I get the drivers, Xubuntu Hardy and my monitor to play nicely.

I looked at xorg.conf, and it appeared to be empty, or close to it, after i installed the drivers..  

For those who have the fx5200 working, can you post your xorg.conf file for us to use as a starting off point?

---

### Post by expelledboy on 2009-05-24
I fixed it..\\:D/ I changed the screen, forget why, and it worked?

Problem was it was to late.. I have already bought a new card... I have buried my good pal 5200fx outside in the garden. :-({|=

---

### Post by nixIT on 2009-05-25
do you remember what screen you changed it to?

---

### Post by expelledboy on 2009-05-26
> **nixIT said:**
> do you remember what screen you changed it to?

I dont think it matters what screen you change it to. I think you should try changing screens in the hope that you dont have two non-supported screens lying around the house. ;)

What I had found was that particular screen just didnt work in linux with those particular drivers. Hope this helps.

---

