---
title: "what tv card works with ubuntu ?"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by jamesford on 2005-10-20
i was just thinking about getting a tv card preferably with fm tuner for my computer but it must work with ubuntu. im not sure about the terminology but i want to be able to view and capture tv programmes and preferably listen to and capture fm radio

so any idea what will definately work ?

also, any software suggestions to use with the card? drivers?

---

### Post by KingBahamut on 2005-10-20
I did some searching and I found the hauppage cards to be the most effectively used. You can use ATI allinwonder cards with the gatos driver but it takes some setting up to do. The Hauppage cards - WinTVGo and the like, are moderately priced from 50 to 200bux. Those should take care of you pretty good. 

[www.hauppauge.com](www.hauppauge.com)

---

### Post by SickTwist on 2005-10-20
[Hauppauge WinTV-PVR-150MCE]("http://www.newegg.com/Product/Product.asp?Item=N82E16815116620") (also available in [low-profile form]("http://www.newegg.com/Product/Product.asp?Item=N82E16815116629")) - TV tuner & radio tuner (plays with [gnomeradio]("http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/"))
[Hauppauge WinTV-PVR-150]("http://www.newegg.com/Product/Product.asp?Item=N82E16815116625") - TV tuner & Remote

These cards have MPEG-2 hardware encoders meaning they will encode video using a chip on the card. As a result, recording will require less CPU power. Recording is as easy as:

cat /dev/video0 > myvideo.mpg

These cards are more optimal for capturing video/TV as opposed to just watching it. They are not compatible with [TVtime]("http://tvtime.sourceforge.net/") as TVtime is not able to decode MPEG-2 on-the-fly (see [supported cards]("http://tvtime.sourceforge.net/cards.html")). However, you can watch TV with Totem/Mplayer/Gxine.

The driver these cards use is [ivtv]("http://ivtvdriver.org/index.php/Main_Page") which will **need to be compiled** to use them. [Abarbaccia.com]("http://www.abarbaccia.com/") is a site dedicated to [MythTV]("http://www.mythtv.org/") on Ubuntu and it has detailed directions how to compile ivtv (the directions are for Hoary but hopefully they will be updated soon).

By-the-way, [NewEgg]("http://www.newegg.com/") is a great place to buy this stuff. I've bought from them many times with no problems.

---

### Post by KingBahamut on 2005-10-20
Newegg my hardware saviour.

---

### Post by jamesford on 2005-10-20
thankts for suggestions. so those windows media center edition cards will work then on ubuntu then ?
ive found the Hauppauge! WinTV PVR150 MCE at a place here in norway so i might go for that. my only worry is that if it doesent work it might not help returning it complaining it doesent work on linux..

---

### Post by thespinesplitter on 2005-10-20
you are planning to use mythTV right... well if so head over to [www.revision3.com](www.revision3.com) and check out the online TV show system and get the episode on mythTV, it pretty much turns your computer into a DVR

---

### Post by SickTwist on 2005-10-20
[QUOTE=jamesford]thankts for suggestions. so those windows media center edition cards will work then on ubuntu then ?
ive found the Hauppauge! WinTV PVR150 MCE at a place here in norway so i might go for that. my only worry is that if it doesent work it might not help returning it complaining it doesent work on linux..[/QUOTE]

I have personally installed a WinTV PVR-150MCE on a box running Ubuntu Hoary for a guy I live with. I have not had a chance to test it with Breezy yet (just upgraded him a few days ago) but if you want I can try to get it going with Breezy tonight and let you know how it works out.

---

