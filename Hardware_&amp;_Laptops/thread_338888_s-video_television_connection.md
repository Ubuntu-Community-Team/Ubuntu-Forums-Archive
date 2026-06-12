---
title: "s-video television connection"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by Michael_aust on 2007-01-15
I am buying my self a mini-itx system to act as my new desktop (I dont want power, I am more concerned about size). The system has a Via M2-12000 board featuring a s-video out connection.
 
 Due to limitation in space I do not have room for a monitor, so I will be connecting the machine to my Television. My television is an LG 20" LCD flatpanel, which I bought this year. The television has both a s-video and scart connection. Te tv supports both 50hz and 60hz refresh rates.
 
 My plan is to connect the machine to my television rather than a monitor. To do this I will a s-video - s-video cable, or a s-video - RGB/Scart with a extra cable to input sound through the scart also.
 
 I have read up on how to set up the xorg.conf file to output via the s-video connection in the various formats (s-video output and rgb scart) and how to putput in different types NTSC and Pal.
 
 Now my question is, I will be using the via drivers for the cle266 chipset from xorg. I wont be using the openchrome drivers as it wont be a game machine and they are essentially the same, except openchrome is like a development branch, correct?
 
 What can I expect from image quality? Is the image likely to be exremely blurry and unfocesed?
 
 This machine will be the only desktop I have in the house, all my university work will be performed on the machine through TV. I will be sitting roughly 1 - 1.5 metres away, so I will obviously need a resolution of 1024x768 or below, anything higher means I will be unable to read the screen. The resolution I will be using is likely to be 700 x xxx or 800 x 600.

The computer will be acting as a desktop machine, running kde and application like konqueror and openoffice etc.
 
 Will my idea of connecting the machine through the tv result in a terrible picture that is unreadable. I understand people use this procedure for mythtv and freevo, so surly the image would be good for using as a desktop?
 
 My main concern is that the image will be fuzzy/blurry and really flickery making it useless to use, which obviously is bad as it will be my only usable computer in the house.
 
 What are your opinions on my idea? Has anyone tried this before? If so what was the image quality like? Was it usable? Was it almost as good as with a standard monitor? Does the image scaling the television do cause any problems etc?
 
 Thanks in advance
 
 Michael.

---

### Post by danomatika on 2007-01-15
I have fglrx (the ATI proprietary driver) working fine with the Radeon X300 in my Thinkpad T-43.  The S-video out works quite well (the picture is sharper then on windows IMO).

In my small experience, the tv out quality depends on the tv your viewing it on.  For instance, if I hook this thing up to my dad's hdtv using svideo, the picture quality is very fuzzy indeed, ok for movies.  On the other hand, when I use standard composite (yellow rca jack) through my friends vcr on his regular old analog tv, its awesome at 1024x768 (max on this card).  Obviously, it is not as sharp as the laptops 1400x1050 lcd, but medium+ font text is readable and movies looks great.

Fuzz and flickering are really not that much of a problem.  I haven't ever used tv out as a main monitor, really only as a desktop extension for movies/games.  I haven't tried a lower resolution for desktop use.

Basically, my suggestion is grab a friend with tv out on a laptop and try your tv out.  Check svideo and regular video.  They are adapters from svideo to the composite on the scart connector, try one of those too.  I'm not really sure, but I think mileage varies between video cards, drivers, and tvs.

---

