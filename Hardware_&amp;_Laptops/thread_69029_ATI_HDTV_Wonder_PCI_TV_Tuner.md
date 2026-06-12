---
title: "ATI HDTV Wonder PCI TV Tuner"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by jeffreyvergara.NET on 2005-09-25
hello, I just bought ATI HDTV Wonder PCI (w/o Remote) and plug it into my Ubuntu PC, im using Breezy, I checked the Device Manager and I saw Winfast TV2000 XP insted of my ATI HDTV Wonder PCI, I checked the properties and I think it's actually my ATI Tv Tuner. (see attachment)

What TV Tuner software/player do you recommend? I tried TVtime but screen is only Black.... I also tried MythTV but it's hard to configure or I just don't really know how to set it up.

---

### Post by jeffreyvergara.NET on 2005-09-25
..sob...

anyways, will this TV Tuner work with Ubuntu?

---

### Post by jeffreyvergara.NET on 2005-09-27
*bump...
does anyone used this? I tested it on Windows XP before, but it seems I can't make it to work either. It was detected by the system properly but the media player software I used can't detect it. In Ubuntu, i used MythTV but I can't configure it properly, so I used TvTime and Zapping but both did not detect my TV tuner card, but when I check the device manager the TV Tuner card is on the list of devices.. (see post above)

---

### Post by kscelt on 2006-04-01
Apparently since linux kernel 2.6.15, kernel support is ther for this card - just saw this , and have not tried it out - hate all the myth-tv bull that goes into setting it up - might try another app first.

[http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder)

---

### Post by dflipb on 2008-01-05
I finally got this freaking thing working today!!!!!

I had to go to the mythtv website where they have a list of working hardware.
I followed the instructions for ati hdtv wonder

[http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder)

the key part for me was getting the firmware dvb-fe-nxt2004.fw

and put it in the /lib/firmware/"what ever the other firmware folder you have in here"

it all seemed to go much smoother then!

also use schedulesDirect  and make sure in your preferences on their website, you select the version of the program you are using.  This way, when myth goes to find the listings, it will be served to you in the format that the program is looking for.

Hope that helps.

Mark

---

