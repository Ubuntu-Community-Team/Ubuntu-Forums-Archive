---
title: "I need a video card that works with Ubuntu 8.10"
date: 2009-06-07
forum: Hardware
---

### Post by MorbidPh8 on 2009-06-07
Ok I have a Geforce 2 440mx. It worked just fine in WinXP. Well I made the switch to Ubuntu 8.10 and lame no 3d acceleration. So Im looking for better cards when I found this one. It's a Geforce FX5500 256mb AGP. I found one for a good price as well. Now I did some searching and it seems everybody is having problems getting there video cards working properly. Now will this card work with Ubuntu 8.10? Will I be able to install it and the drivers with out a problem? I just want to be able to play some games and get the desktop effects to work. If this card wont work... Is there a list of compatible cards out of the box with Ubuntu 8.10? I like using Ubuntu but if I can't get 3d to work then I'll have to go back to Windows which I don't want to do.... Please Help.... I have been searching for days with no clear answer... Thanks

---

### Post by s3MA00RRNY on 2009-06-07
One thing to clear up. NO NVidia cards work out of the box with Ubuntu. You must install the restricted drivers manually, because they are not open source. This is done by going to System > Administration > Hardware Drivers. If after installing those drivers and enabling desktop effects in System > Peferences > Appearance > Visual Effects, it still doesn't work, then you probably will need the other graphics card. Or you can try getting the drivers direct from NVidia, but that can get a little sticky. Go to [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) for supported graphics cards.

---

### Post by MorbidPh8 on 2009-06-07
Well I have to get another card as far as a can tell old nvidia cards wont get any 3d acceleration in Ubuntu.
I've tried every method and driver I can find.... So Im going to buy a newer card than the one I got. I like the Geforce FX5500. I understand about the restricted drivers. I tried installing them for my old card... I just want a video card I can get to work. When I search Google. All I get are people with video problems with a lot of differnt cards. Theres got to be a list of video cards that do work right? I just don't want to buy a better card and still be in the same situation. As it is right now I can't even get Google Earth to work because of my video card. There some games I wanna play too, but wont load due to the video card. I don't mind installing restricted drivers. I just want the card to work properly after I install the drivers. Also the card doesn't have to be a Nvidia card. I hear theres even more problems with ATI.  So if anybody can say the Geforce FX5500 does work with 3d acceleration under Ubuntu. Then I'll buy it tomorrow.... Other than the video issues Im really loving Ubuntu.

---

### Post by s3MA00RRNY on 2009-06-08
Yeah, you're probably expecting too much when you want it to play games. The weakest graphics card you can have for the newest Madden NFL game is a GeForce 3. I can't imagine how slow it would run though. If your computer has a GeForce 2, how pathetic are the other components. You may want to consider buying a new computer.

Edit: BTW I have a GeForce card and it works well (plays Age of Empires III in Wine on max settings). It is a hair newer though. GeForce 8400M GS. My grandmother has a really old one that runs on the 97 drivers in Ubuntu (which still works amazingly). I think it's a Quadro NVS.

---

### Post by MorbidPh8 on 2009-06-08
Yea the card is old that is why I want to get a new one. Im running a P4 1.8ghz 512mb Ram I put it together with a bunch of old parts. My card how ever is older than the rest. I just want to buy a newer agp card. If I buy a card and can't get it to work on ubuntu. it will suck bad. So Any ideas? Is there a list anywhere of video cards that are known to work well with ubuntu? I don't want to have to buy and return muiltiple cards just to find one that works... It really sucks beacuse it's problems like this that keep alot of people from using linux. I know it's not the OS fault but the card makers and there closed source drivers.. Hell maybe I will just get the card if it doesn't work. Ill have to figure something else out.

---

### Post by s3MA00RRNY on 2009-06-09
I pretty much already gave you the list, BTW. Check out the link in the previous post.

---

### Post by jerrrys on 2009-06-09
this is a little help...

[http://worldwindcentral.com/wiki/Video_Card_Compatibility](http://worldwindcentral.com/wiki/Video_Card_Compatibility)

---

### Post by MorbidPh8 on 2009-06-09
Ok.... The first site you gave me only told me what drivers support what cards.....  So ok 173.14.xx driver works with the Geforce FX5500... Doesn't really tell me if it will work with Ubuntu... It also says 96.43.xx drivers for my Geforce 2 MX 440. I know for a fact that driver doesn't work because I have installed them every possible way, with no results. So still I ask is there a site that list what hardware is known to work right with Ubuntu????? If I search Google for Geforce FX5500 and Ubuntu. I find a couple of people who got it to work with lots of people who can't get it to work at all.... Geez I just want Desktop effects and OpenGL apps to work thats all........ Well im off to do some more searching...........

---

### Post by MorbidPh8 on 2009-06-11
Is there anybody on here at all that can help? There gotta be somebody with this card installed working? Ahhh microsoft is calling my name ahhh...  The dark side is so much easier on my eyes.... Ok j/k seriously I've done a bunch of searching and can't find a deffinite answer on what video cards work on Ubuntu. Are there 3d accelerated cards that are made for Linux? Not just for Windoze but we also have Linixu drivers? Thanks..................

---

### Post by jocko on 2009-06-11
> **MorbidPh8 said:**
> Ok.... The first site you gave me only told me what drivers support what cards.....  So ok 173.14.xx driver works with the Geforce FX5500... Doesn't really tell me if it will work with Ubuntu... It also says 96.43.xx drivers for my Geforce 2 MX 440. I know for a fact that driver doesn't work because I have installed them every possible way, with no results. So still I ask is there a site that list what hardware is known to work right with Ubuntu????? If I search Google for Geforce FX5500 and Ubuntu. I find a couple of people who got it to work with lots of people who can't get it to work at all.... Geez I just want Desktop effects and OpenGL apps to work thats all........ Well im off to do some more searching...........

> **MorbidPh8 said:**
> Is there anybody on here at all that can help? There gotta be somebody with this card installed working? Ahhh microsoft is calling my name ahhh...  The dark side is so much easier on my eyes.... Ok j/k seriously I've done a bunch of searching and can't find a deffinite answer on what video cards work on Ubuntu. Are there 3d accelerated cards that are made for Linux? Not just for Windoze but we also have Linixu drivers? Thanks..................
If there is any list with hardware that works in ubuntu, ALL nvidia cards that are supported by the 71, 96, 173 or 180 series nvidia drivers (or whichever driver versions are available in the intrepid repos) are on that list, even your old Geforce 2 card.
If you have really installed the recommended driver using the hardware driver manager, you should have 3d acceleration and you should be able to activate desktop effects.
There are no cards that are "made for linux". The cards are made for pc, then it's up to the hardware manufacturers to decide which operating system they develop drivers for (or release the specs and code to the open source community as ati is doing).
In my experience nvidia's proprietary linux drivers work better and are easier to get everything working ("everything" means not only basic 3d acceleration, but also tv-out, multiple monitors, decent video playback and so on...) than ati's proprietary drivers.
Ati recently dropped linux support for a lot of their "older" cards (everything older than the HD2000/R600 cards).
So if you want a working ati card, either go for one that works well with the open source drivers "radeon" or "radeonHD" (I don't know which of the newer "older" cards have full 3d acceleration and which have only 2d acceleration with the radeonHD driver, but that information can be found on the [phoronix forums]("http://www.phoronix.com/forums/forumdisplay.php?f=43")), or go for one that is supported by the proprietary driver (HD2000 or newer cards).

---

### Post by jasonsjunk on 2009-06-11
I have a Nvidia 5200FX that works with the 173.14.xxx driver.  3D acceleration works granted this card isn't a speed demon and the P3 933 computer it is installed in won't set any records either.  I haven't tried to run Compiz or anything like that but some games like Alien Arena, Nexuiz and Open Arena are playable.  

Sometimes it is just easier to update the hardware rather than fight with the older stuff.  You can put together a new computer for only a couple of hundred $$$ and all of the PCIx cards are much better in terms of support and graphics.  

Use the old computer as a file or web server.  I use my old box as a MythTv frontend/web browser mainly.  One nice thing about those older Pentiums is they run quiet and cool.

---

