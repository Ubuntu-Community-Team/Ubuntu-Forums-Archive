---
title: "[SOLVED] As of today, ATI or Nvidia?"
date: 2008-11-15
forum: Hardware
---

### Post by dorkdork777 on 2008-11-15
I'm seeking to buy a new computer, which will be used for general production, including meddling with 3D modeling. So obviously, if I'm going to be sticking with Linux, I'll need 3D drivers for whichever graphics card I get. I have an Nvidia GeForce 6200, and I know from experience that the 3D driver for it is fairly buggy and generally not nice.

But having no experience with any form of Linux on any other computer, I have no idea if the newer NV cards are better with Linux than older ones (like mine), and also how decent ATI's offerings are. I've heard ATI planned to open up their drivers completely, including 3D support - all those news articles date back to last year, but I can't find any mention of them actually doing it.

So the question is: Nvidia or ATI, and is there anything else I should know? :)

---

### Post by dorkdork777 on 2008-11-16
Bish Bash Bosh, Real Good Nosh!

Also *bump* :)

---

### Post by LoloftheRings on 2008-11-16
I'm about to buy a new card, I would like to know too what's best. I need 3D support for gaming.

---

### Post by Miguel on 2008-11-16
If you don't care about open source drivers and all you want is a moderately stable system with good 3D performance **today**, get nVidia. ATi currently is almost as fast as nVidia in most relevant games, but stability is subpar and some issues regarding Xorg 7.4 and tearing with Xvideo exist. On the other hand, support by free drivers is very nice.

The only reasons one can have to buy ATi is supporting them for opening their specs (3D works out of the box with X1000 cards and will soon work too in HD2000) or you are buying a laptop and can't really choose. Well, you could also buy a card for gaming under windows and not really care about linux, in which case the 4850 is a pretty good deal.

But whatever you do, don't buy an ATi 3850x2. These **do not** work

---

### Post by bobnutfield on 2008-11-16
There are those that will disagree, but from personal experience and other sources, ATI=pain, usually.  nVidia is better supported in Linux.  I have both, nVidia in my desktop and ATI in my laptop.  Since AMD has taken over ATI, the situation has improved, but still not the same support as nVidia.  ATI is slow to support the new releases of Xorg, and as a consequence, is ususally behind nVidia in supporting the latest video technology.  However, under Windows, ATI would get the nod.

---

### Post by peakshysteria on 2008-11-16
My ATI EXCALIBUR X700 PRO is working very smooth at this end. After AMD bought ATI they have improved the drivers significantly. And they will improve them further in the time coming. At the time ATI seems to be ahead of all competitors. Including Nvidia.

As a linux n00b (i still feel like one) I must admit I used a really long time to get the driver for my card up and running (but once again, now I know, all is easy as soon as you find out how to do it). Though the majority seems to have less trouble with it. I'm still running Hardy Heron as there seems to be reports of trouble with some ATI cards on Intrepid Ibex. Nvidia seems to have more serious problems with Intrepid than ATI when it comes to 3D rendering. But the reports seems to be a bit conflicting still. But most sources seems now to point out ATI as being in the lead. Also [ATI have monthly updates]("http://ati.amd.com/online/rss/atilinuxdriver.rss?OCT-rss") on their drivers. I don't think Nvidia have that kind of work done for their drivers (Nvidia people may prove me wrong).

Hardy Heron seems to work very fine for ATI users (including myself) and most Nvidia users. It would be nice to hear some reviews from Intrepid users (both ATI and Nvidia users).

---

### Post by dorkdork777 on 2008-11-16
Brilliant, thanks a lot :D looks like it's a new NV card for me, this makes it a LOT easier :P

EDIT: just saw the post above mine... looks like there's still debate. Any more thoughts/opinions?

---

### Post by Neostar on 2008-11-16
I've been using an ATI Radeon 9800 Pro 128MB and that seems to work fine for me. I think my next upgrade should be a 2400HD or 2600HD depending on the support and if the AGP version goes down in price.

---

### Post by ajgreeny on 2008-11-16
I'm not a gamer and so my recommendation may not be appropriate, but my ATI Radeon 9200SE works brilliantly with the open source ati/radeon driver installed with the system install.  I suspect if I wanted to play graphics-intensive games it would not be much good, but offer the info for what it's worth to you.

---

### Post by binbash on 2008-11-16
Nvidia.ati is too slow to support new releases of Xorg.you can see this at intrepid release.

---

### Post by Sephoroth on 2008-11-16
In my experiences, my Nvidia GeForce 6800 has always ran great once restricted drivers were enabled.  The only time they didn't work out of the box (2D Rendering) was during the Hardy Beta (though they worked on the official release).

Most typically I've heard problems involving non-integrated ATI GPUs compared to that of Nvidia.  It seems like ATI is improving though.

---

### Post by Skripka on 2008-11-16
ATi-makes GREAT cards, that are FAST and tweakable, their pricing scheme forced Nvidia to RELY cut prices on their GPUs (thank you ATi/AMD), and ALL the money that goes into R&D into making those great fast cards comes out of the budget for writing decent drivers to run said cards.  They NOW, though-make a very nice windows driver...their Linux driver looks and works like someone's homework done 10 minutes before class started.

Nvidia-not necessarily as great a cards anymore, in comparison.  GREAT drivers, on the whole.  I actually like the Linux Nvidia driver better than the Windows driver-for functionality as well as adjustability.


YMMV of course.

---

### Post by dorkdork777 on 2008-11-17
OK, thank you all SO much! So it looks like I'll be getting an NV card now, but I might upgrade to an ATI down the line once they open-source their drivers. :)

---

### Post by peakshysteria on 2008-11-18
Tell us which card you bought and how it performs as soon as you have it up and running :)

---

### Post by LoloftheRings on 2008-11-18
Thanks all, it's gonna be a Nvidia for me too :D
The day after intrepid's release, I upgraded my hardy and reinstalled hardy the same day. Getting the right driver was a hell. All tutorials on the web also didn't help me any further. I also had some problems with my wifi. Ah, I'll just stick to Hardy:)

---

### Post by Hadraniel on 2008-11-19
After noticing the HD3200, which is built-in in my 780G chipset board (GA-MA78GPM), is not sufficient for games, I had a hard time to select my new card.

I ended up choosing between nVidia 9800GT and ATI Radeon 4850. You'll notice, a lot of people ending up at this choice, if you search at google or even in this forum ("9800gt vs 4850").

I was close to buying the NVidia card, for NVidia ist known to work better with Linux. I finally chose the 4850, as it offers more performance, at the cost of higher price and energy consumption/heat .. and after reading the latest NVidia cards to have problems with Linux aswell.

Anyway, I have thermal problems now in my NSK3480 case, which I'll solve by adding some quiet fans (it was running entirely passive), but the Radeon 4850 is working fine (almost out of the box!) with my Ubuntu 64bit and the fglrx driver. I even have compiz-effects.

I also have flickering during video playback, which can be workarounded by using VLC and setting video device to "X11 video". Unfortunately, the UVD is not being utilized (no video accelleration). Did not test any 3D apps so far, (games, wine, Crossover Gaming), though.


In my old computer, a NVidia 7600GS was working perfect and out of the box. For people now choosing, and from what I had to cope with radeonhd, ati, fglrx with both HD3200 and 4850, I'd say ATI is closing up, fast.

---

