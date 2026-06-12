---
title: "Ubuntu 11.10 with Emachines E180HV Monitor problem"
date: 2012-01-07
forum: Hardware
---

### Post by itpro007ca on 2012-01-07
First,the hardware:

Biostar NF61S AMD64x2 micro-atx motherboard
AMDx2 Cpu
2gb ddr2 800 ram
SATA2 WD 160GB HD
Nvidia GE6100 Video,integrated audio,lan,etc
LG DVDRW 

Display: Emachines E180HV widescreen LCD monitor


*installed Ubuntu 11.10 alonside XP

Problems:

*on bootup -no grub menu(I suspect that it's there,but I can't see it,because after updating grub,it shows xp hom,as being there).....I see a bouncing box "input not supported"....but, after wating some time,the system does boots into Ubuntu.

I note under "Systems" and "drivers" that the driver is Nvidia 173.Under "Display' it says "unknown."The resolution is 1280x1024,where as the display's native res.(I see after doing an online search)is :1380x768...

*On shutdown,I see the same "input not supported" error msg,but sometimes the usual "........[ok]" messages.

(I'm glad I didn't try this on my Win7 laptop!}

Any ideas?

btw: For now,I used the Windows disc and 'fixmbr" to get xp back up until I figure this 'problem' out,

Would going Kubuntu be any different?
(I have made live cds of both)

btw: I tried to restore Grub from the live cd,but couldn't figure it out.

---

### Post by jerrrys on 2012-01-09
You do not get these options in your monitor settings?

[ATTACH]210517[/ATTACH]

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvidia+173&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvidia+173&sa=Search&cof=FORID:9)

Edit: will the live cd run ok?  try without installing.

---

### Post by itpro007ca on 2012-01-09
> **jerrrys said:**
> You do not get these options in your monitor settings?

[ATTACH]210517[/ATTACH]

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvidia+173&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Nvidia+173&sa=Search&cof=FORID:9)

Edit: will the live cd run ok?  try without installing.

I ran the Live CD before I installed 11.10.Seemed ok,so I installed it.

Update:

*changed from nvidia 173 driver to 'recommended' and now get various modes,plus 1368x768.

*Systems>Display still shows 'unknown'as far as monitor is concerned,but it's getting there,but,at least,Nvidia Xconfig now shows Emachines E180HV monitor.

*Firefox -now looks perfect instead of 'stretched.'
*Tried to download and run 'ExtremeTux" but got sound,but no video,so I guess no "3D?"

At least,compared to others,even though I get the error at bootup,it does boot to Unity and everything runs fine,except,it looks like no 3D.No Quake 3 Arena,or Torcs,just yet! Rats! lol

From doing a search on the forum for "nvidia ge 6100",it appears the blank screen/no grub on bootup and on shutdown is a common problem.

(GRUB actually is there,because this afternoon,after hitting the down arrow key 5x and hitting [enter],I was able to boot into Windows XP!)

I might try the 'sticky' changes to the grub and see if that helps.ie:makes it appear,unless it's a video mode problem,also.

---

