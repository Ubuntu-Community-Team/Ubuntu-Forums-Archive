---
title: "cdrw not burning discs correctly"
date: 2010-03-09
forum: Hardware
---

### Post by Klipstraat on 2010-03-09
Hi all - having some strange issues with my cd rw - when I try to burn a disk with k3b it says the burn is successful .. but when i re-insert the disk my system will not recognize it at all. 

If I burn an audio disk (.wav format) it gives err msgs on re-insertion into my laptop as well as when I try to play on a hifi cd player.. 

Same with any data dvd disk eg photos - my sys says it is burnt ok but the shop down the road's windows photo printer says the disk is empty / unreadable..

Brasero just goes nuts and locks up.. also tired of burning coasters...(guy I know gives them a second in his microwave.. some people just have the weirdest thought processes....) anyway I digress

I have tried SMART tools to diagnose - get this back

code : smartctl -a /dev/sr0  (btw - should the cdrw be listed as sr0?)

response :

Device: TSSTcorp CD/DVDW TS-L632D Version: HH17
>> Terminate command early due to bad response to IEC mode page

I am thinking that the cdrw has a dirty laser or some dust in it - my laptop does a lot of travelling /-  or an underpowered write strength

1/ K3b does a preburn diagnostic test doesn't it?
2/ Is there a nice gui cdrw diagnostic pkg available? 

I would like to test the laser strength somehow..

Using Karmic on a 64 bit Compaq nx 7300 (perhaps the machine is just getting old???)

Regards and thank you in advance for any input you may have

---

### Post by howefield on 2010-03-09
Some writers are averse to specific types/brands of media.

Do you have the problem with good quality media ?

---

### Post by IcarusR on 2010-03-09
Could try writing at a low speed.

---

### Post by efflandt on 2010-03-09
How does it do with CD-R?  I have been able to burn 16x CD-R isos in Brasero with no problems at all.

But the first time I tried CD-RW it took several blank and rewrites before I was successful (and I forget if that was with Brasero or k3b).  But I did not have any more success with k3b.

CD-RW may be more temperamental about ambient (room) temperature, so if temperature is too far off, it may not blank or burn properly (or may melt down).  I suspect in my case it may have been too cool in winter.  But the media was a store brand (Staples), so I do not know if it was that or the age of my computer and burner (2004).

The last time I bought CD-R disks they were 20 cents each or less.  So I have given up on CD-RW for now.

---

