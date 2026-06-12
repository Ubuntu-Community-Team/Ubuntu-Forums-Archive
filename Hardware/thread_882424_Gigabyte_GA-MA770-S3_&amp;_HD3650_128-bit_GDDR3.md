---
title: "Gigabyte GA-MA770-S3 &amp; HD3650 128-bit GDDR3"
date: 2008-08-06
forum: Hardware
---

### Post by Duo Maxwell on 2008-08-06
Hi I'm building a new comp for a friend, but I'm wondering about Ubuntu compatibility, but I'm wondering about the hardware picks I've made, specifically the mobo and GPU A complete parts list is here [http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12572567](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12572567)

I really like the layout and I/O on this mobo, but theres a bad review or 2 for it in Ubuntu, any help wld be great.

I went all AMD due to them doing allot these days to support open source, evn though thre isn't and 3d docs for the HD2-4 series cards yet.

---

### Post by wolffangalchemist on 2008-08-06
you might want to go Nvidia on the graphics card as it's Linux drivers are better than ATI's.

as for mobo i was thinking of this for my self it could work for your friend too.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157126](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157126)

---

### Post by Duo Maxwell on 2008-08-07
Hi Wolf, that mobo looks kinda meh, no firewire/ieee1394 isn't good for any kind of DV cams or audio gear, as well as no spdf, that and IGP mobos are generall of a lower bild qality to mobos that require a dedicated GPU, not to mention that it's leeching ystem ram.


Thats only for the time being though right? at the current pace of their driver releases compared to the old ATI days and the fact that they have been releasing docs to the x.org team should leave us with decent drivers inside a year right? I'm just asking about the GPU as does it have a relatively stable driver at this time or not? I should have specified that the mahine wont be used for gaming, but I still prefer to build it with a real GPU with 128-bit GDDR3 as a minimum, doesn't matter if it's nvidia, matrox, seeing as it's useful for an possible future apps and Compiz mods that don't yet exist that aren't games, think Google Earth and Celestia. Not to mention any future GPGPU accelerations that could be aded to existing apps.

---

### Post by wolffangalchemist on 2008-08-07
[http://ubuntuforums.org/showthread.php?t=708441&page=1](http://ubuntuforums.org/showthread.php?t=708441&page=1)
seems some others where having problems with that specific ATI card.
if you want to go ATI the by all means do  on the ati driver guide it says.
```
Full 3D support (r100 and r200 series)

All these cards and derivatives have full 3D acceleration support

7000 / rv100 based cards
7200 / R100 based cards
7500 / rv200 based cards
8X00 / R200 based cards
9000 / rv250 based cards
9100 / R200 based cards
9200 / rv280 based cards

There is a bug related to the DVI output on the rv280-based cards, please check Radeon_9200/9250_%28RV280%29_and_DVI
```
these cards are the most compatable with the drivers from ATI(apparently)
so you have something to go on when choosing your friends card.

i only suggested that mobo as i heard it works well with linux and there's a review or 2 on it that says so.
when i save up some money I'm planing to build a cheap gaming pc so your needs are different i understand.(i want to play WoW with opengl and my ATI integrated card will only do it in d3d :( ) 
on that note. how is Regnum Online is it any good i might try it.

---

### Post by Duo Maxwell on 2008-08-07
> **wolffangalchemist said:**
> 
on that note. how is Regnum Online is it any good i might try it.

Sorry to hear about the wowcrack not going in ogl for yah, A while back though Phoronix [http://www.phoronix.com/scan.php?page=article&item=ati_r500_gaming&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_r500_gaming&num=1) did a preview on the state of 3d in the alpha grade open source R500 series cards, they worked...ish... But then the documentation for them had only been released like a month before, the older cards in the R200 lines and back have long since been fully open sourced by ati, since they where such old tech and the fact that the only bit of them still in use was the rage 128 chips in servers, which also seems to be finally discontinued.

Here's the current state of the open source drivers vs the newly released intel X4500HD, their newest and fastest IGP [http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=5](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=5) as you can see, the intel driver, with intel already havingworked the driver out themselves for the x.org team, it does stomp the amd cards running on oss drivers in a good number of tests...

But the HD4870 looks to be absolutely dominating even on linux with the highest FPS even at 1920x1200 with 8x anti-assailing and 16x anisotropic filtering [http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4870&num=8](http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4870&num=8)

As for Regnum, it's a free time killer with tons of linux players, I've been off it for like 4 months now though, I had daaged my crappy video card and never got around to replacng it(massive OC to a Geforce 6200 [NV44A]) so fort wars and hunts got hard to deal with due to low fps, that and I was burning out on it since I was lving up 5 different chars over like 6 months, would like to get back to it someday though.

When last I played it was still little more then a bunch of nondifficult quests and forced war once you get to Lv32, at which you had no choice but to leave the relative safety of your countries walls.

Tip, mages and marksmen have wars pretty easy, at least for scoring massive amounts or kill points, warriors and hunters fare better in open land skirmishes as they won't be cut down by a barrage or fireballs and arrows, that and the hunter s for stealth, not range and knockdown power like the marksman.

It's no wowcrack, but what d you want for free? It's at least better then Planeshift though, which I could never figure out what to do and nobody would help me figure out anything in the game. [http://www.regnumonline.com.ar/forum/showthread.php?t=15225](http://www.regnumonline.com.ar/forum/showthread.php?t=15225)

If I remember right the linux client officially unofficial, they only have an 8 man dev team in argentina and the dev Surak was still doing the linux client in his spare time while he was still maintaining the windows client.

---

### Post by Duo Maxwell on 2008-08-09
bump, nobody using this mobo?

---

