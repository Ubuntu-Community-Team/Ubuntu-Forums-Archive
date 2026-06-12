---
title: "Hardware and software recommendations - Media Server / NAS"
date: 2010-01-18
forum: Hardware
---

### Post by dufftime on 2010-01-18
Greetings from a Ubuntu n00b / soon-to-be-huge-fan!

(A little background...)

Right now I'm running Tversity on my gaming WinXP desktop to stream media to a PS3 downstairs.  I've been researching a NAS / Media Server solution for the past few weeks for backups and to store my growing media collection - and I want to stop running a media server on my gaming desktop 24/7.  I had actually settled on the HP MediaSmart EX490 (I love that case...) and was just waiting for it to go on sale, when on a whim I decided to try FreeNAS on an old Pentium III (Coppermine!!) I had laying around.  I like OS X and WinXP for desktops, but really wanted to get something *NIX-ish for my server.  Plus the fact that I would be paying for a WHS license with the HP EX490 really irked me, considering this is where *NIX shines.

I was impressed with the speed and ease setting up the FreeNAS server.  Fuppes and Firefly worked right away and for the most part did exactly what I needed.  However, I wanted to be able to extend the functionality of the server so tried Karmic Koala.

The install went fine on the same Coppermine P3 (1GB RAM).  For UPnP I installed MediaTomb, Firefly for iTunes, and Miro TV to download video RSS / podcasts.  To my surprise, this Pentium 3 was streaming faster and without stutter (even some HD) where Tversity would have playback issues - and this running on an AMD X2 5600+!  Starting playback of mp3's was quicker, pictures loaded faster, and fast-forward/rewind was seamless.  This whole time I thought it was my wireless-G network that was the bottleneck when it was actually Tversity (or XP). That's when I decided to go with a DIY Ubuntu build! :D

This server will also be used for backups from my WinXP desktop, WinXP laptop, and wife's MacBook (10.5.6 I think) and plan on using rsync, or some utility based on rsync for this purpose.  I might put a small web, FTP, whatever site on at a later date... there's a whole new world I'm looking forward to explore :D

For storage I'd like to go with RAID 5, but am a little nervous reading about restoring if/when one of the drives dies.  It seems simple enough, but when the **** hits the fan, I need to be able to look my wife in the eye and say our baby pictures will be OK.  I DO know RAID != backup so will be investing in an online backup service like Mozy.

I normally order my hardware from NewEgg, but I have the early part of this week off and want to get it built before I start traveling again Thursday, so I'm headed to my local Fry's.

So here's what I currently have in my Shopping Cart:

[B]CPU:  AMD Sempron 1400 - $37
[/B]I wanted to reduce power consumption, as it'll be on 24/7.  These are also supposed to run quite cool on stock cooling.  Based on my trial run on the old P3, I figured any single-core CPU would be fine for my needs.
[http://www.frys.com/product/6006428](http://www.frys.com/product/6006428)

[B]Mobo:  ASUS M4A785T - $90
[/B]I don't really care that much, as long as it has 6 SATA ports and IDE with Gb LAN.  I want to reuse an old 320GB IDE drive for the OS install.
[http://www.frys.com/product/6136519](http://www.frys.com/product/6136519)

[B]RAM:  4GB DDR2 PC6400 PNY - $70
[/B]Whatever is cheap/on sale.  Going up from 2GB to 4GB doesn't seem like that much more $$$.
[http://www.frys.com/product/5939834](http://www.frys.com/product/5939834)

[B]PSU:  Antec Earthwatts EA 380D Green 380W - $45
[/B]Something efficient, clean, and quiet!!  380W should be more than enough power.
[http://www.frys.com/product/6139349](http://www.frys.com/product/6139349)

[B]Storage:  3 x 1.5TB Samsung Ecogreen F2 SATA - $100/ea = $300
[/B]These will be software RAID 5 for NAS storage.
[http://www.frys.com/product/5976794](http://www.frys.com/product/5976794)

[B]Case:  Silverstone Lascala LC13B-E HTPC ATX Case - $130
[/B]As this will be sitting downstairs by my A/V components (underneath the PS3 and DirecTV box), I'd prefer it to look nice and a bit like a stereo component.  Quiet is a must!  I might also go with a cheap-o-ugly case and stick in a cabinet underneath my components, but I'm worried about sufficient air flow.
[http://www.frys.com/product/6116779](http://www.frys.com/product/6116779)

**Total $672**

My hardware questions:

[LIST=1]
[*]Is there anything above that looks bad Ubuntu compatibility-wise?
[*]Are the hard drives OK for RAID 5?  Will the power-saving features of the green drives affect RAID, or will RAID prevent it from saving power?  I read some people saying it's fine, and others saying these drives weren't meant for RAID and causes early drives failures.  In any case, I'd appreciate the reduced power draw and quiet.
[*]The motherboard specs say "RAID 0, 1, 10 support" and do not explicitly state RAID 5.  I assume this is the "hardware"-ich based RAID from the mobo, right?  Ubuntu software RAID 5 only needs a SATA connection, correct?
[/LIST]
My software / install questions:

[LIST=1]
[*]I feel more comfortable installing Ubuntu 32-bit - is there a compelling reason to try Ubuntu 64?
[*]Do I really need Firefly, or can MediaTomb also present itself to iTunes on my network?
[*]Miro TV seems like alot of overhead for essentially downloading podcasts - I won't be using it for anything else.  Is there something else I can try?
[*]Should I go with ext3 or ext4 for the NAS filesystem?  I'd prefer the performance boost but don't want to risk any corruption (which I thought were Jaunty specific bugs?)
[/LIST]
Thanks in advance for any suggestions / comments / answers.  I know it was a long one so appreciate all that made it through this wall-of-text post!

-dufftime

---

### Post by cascade9 on 2010-01-18
If it was me, I would probably try to get a 'e' (energy efficient) model AMD CPU-e.g.- Athlon II X2 235e, Athlon II X4 600e, Phenom II X3 700e, Phenom II X4 900e. They have the same TDP as the semperon 1400, and a lot more guts. Not that you need that, but it can come in handy. 

I'd probably also go for WD Green Power drives over Samsung Ecogreen, but that its just as personal preference. 

M4A 785T uses ATI onboard video. It works, but nVidia (onboard or an addon card) works better. 

DDR2 works fine in motherboards that support it. The M4A785T is a DDR3 board, so that RAM wont work. 

Lascala LC13B-E is going to be a bit crowded with 4x3.5'' drives. It only fits that many, maximum, so your going to have drives sitting on top of each other. Not good IMO. I'd probably think about getting a slightly bigger case..maybe a LC16, they have a nicer drive arrangement. 

> **dufftime said:**
> 
My hardware questions:

[LIST=1]
[*]Is there anything above that looks bad Ubuntu compatibility-wise?
[*]Are the hard drives OK for RAID 5? Will the power-saving features of the green drives affect RAID, or will RAID prevent it from saving power? I read some people saying it's fine, and others saying these drives weren't meant for RAID and causes early drives failures. In any case, I'd appreciate the reduced power draw and quiet.
[*]The motherboard specs say "RAID 0, 1, 10 support" and do not explicitly state RAID 5. I assume this is the "hardware"-ich based RAID from the mobo, right? Ubuntu software RAID 5 only needs a SATA connection, correct?
[/LIST]

1- Nothing that wont work. ATI video is the biggest issue I can see. 
2- They will work under RAID. The power saving is from spindle speed (5400 RPM  uses less power than 7200) and other harder to qualify mods (eg. lower power controller board). You'll see lots of opinions both ways on 'do these drives work well in RAID'. Some people have the belief that you should only use 'enterprise' level drives for RAID (by enterprise, I mean the more expensive drives with a higher MTBF etc).  Other people will run whatever they can get. The enterprise level drives are probably a safer bet, but normal drives will do the job. 
3- Yes, as far as I know, on both questions. 

Ohh, as for 64bit- its faster, woohoo! If you are ever planning on doing any audio/video conversion on the server then its worth trying. (on the fly video conversion would be much better on 64bit...buit with a semperon 1400 its never going to be fun, one reason why I like the 'e' series AMD CPUs). 

If your never going to do any real number crunching, then 32bit should be fine.

---

### Post by dufftime on 2010-01-19
Thank you very much for the response cascade.  You saved me from a return trip to Fry's with the wrong mobo.

I would have loved to get a faster "e" series of AMD but Fry's did not carry them (nor did NewEgg, Amazon, or mwave.com, not even eBay).  I'm guessing it's discontinued, but why the scarcity?

Fry's did not have any of the 1.5TB Samsung EcoGreen's in stock - actually they didn't have any 1.5TB's so I passed on it and just ordered from NewEgg.com.  I figure I can stand up the OS and set up the streaming to my local IDE drive and install the 3 x 1.5TB later RAID 5 when NewEgg/UPS delivers.

I found out the Antec 380 didn't come with a power cable... so weird.  I wasn't 100% sure I had one at home and just got a Corsair CX400 instead for $10 more.

Lastly, I settled on a Cooler Master CM690 for a case, which I'm wondering if it was a wise choice.  It's a great case for your desktop PC, but it might be the best and quietest for a NAS server.  It does have plenty of room for hard drives and the cable management was really nice... I'm going to see where I can stash it for now.

I'm running MemTest off the Ubuntu LiveCD (66% now) and will be installing Karmic Koala shortly.

Thanks again!

---

### Post by cascade9 on 2010-01-19
> **dufftime said:**
> Thank you very much for the response cascade.  You saved me from a return trip to Fry's with the wrong mobo.

I would have loved to get a faster "e" series of AMD but Fry's did not carry them (nor did NewEgg, Amazon, or mwave.com, not even eBay).  I'm guessing it's discontinued, but why the scarcity?

No problem..it can get kind of confusing when AM3 motherboards can come with either DDR2 or DDR3. 

The 'e' series CPUs always seem hard to find. I'm 99% sure that they are still in production, but finding one can be an issue. I can get a 235e here ($90 vs $70 for a normal X2 240), the other 'e' seires I am yet to see. But they are fairly new, besides being low volume production so thats not much of a shock to me. 

I'm also pretty sure that they are the same CPUs, from the same line as the other Phenom II/Athlon II CPUs, just instead of testing them for Mhz, they test them for low voltage. Since there is a conenction between voltage and Mhz, its possible that what might pass as a X4 965 might also pass as a X4 900e. Since AMD is currently selling a lot of X4 965s they might not even be testing for 900e CPUs. 

They might get more common in the next 6 months to a year. 

> **dufftime said:**
> 
I found out the Antec 380 didn't come with a power cable... so weird.  I wasn't 100% sure I had one at home and just got a Corsair CX400 instead for $10 more.

Lastly, I settled on a Cooler Master CM690 for a case, which I'm wondering if it was a wise choice.  It's a great case for your desktop PC, but it might be the best and quietest for a NAS server.  It does have plenty of room for hard drives and the cable management was really nice... I'm going to see where I can stash it for now.

I'm running MemTest off the Ubuntu LiveCD (66% now) and will be installing Karmic Koala shortly.

Thanks again!

Much nicer PSU. I'm a big fan of corsair power supplies. 

CM690 is a fine choice. Not noisy, 120mm fans, big enough to put soundproofing in later. 

Good luck with your new computer and on your install ;)

---

### Post by dufftime on 2010-01-19
I got Ubuntu on the OS installed and humming along.  I'll spend more time organizing all the media after my storage drives arrive.

Right now my CPU is doing just fine.  Firefox (??) seems to be the most resource intensive app I run on it, and I'm just doing it to add my video feeds from Miro TV.  I might replace it with a fast "e" model later if I end up transcoding.

I swapped out the front 120mm annoying blue LED fan with another variable speed one which helped with the noise a bit.  Even though the LED was drawing almost no power, it is annoying me that I was wasting electricity on it.

I really like the Corsair PSU.  You can tell you got a solid, well-built product and it's barely audible.  Well worth the extra $10.

I'll check back in after I get the RAID 5 finished.

-dufftime

---

### Post by MobileNet on 2010-01-31
Hi All,

I'm new to ubuntu, and I'm interested to build a NAS using my the following:

SuperMicro 5015A-L Server 
Atom N230 all-in-one motheboard (support 64-bit)
G.Skill 2GB DDR2-800 CL4
1TB WD Green Drive = System HDD
4x 2TB WD Green Drives in RAID5 (using Rosewill RSV-S4-X eSATA RAID5 External Enclosures, SiliconImage 3726)

This server will run non-stop and I want to use it to store data. I already have a MPC connected to my TV for video, etc.

Question:
1. Should I use the Server or Desktop version?
2. I wants to use it to share my HP Laserjet 3030 All-in-one (connected via USB), can ubuntu support all-in-one printer to scan and fax? and maybe network fax from Windows desktop?
3. Does ubuntu support remote control like remote desktop from Windows? Server is not connected to any monitor, remote is needed.
4. Optional: Use it as download server (BT/ed2k/FTP/http...etc)
5. Optional: Stream media to my iPhone (or iPad, I'm planning to get it), any software recommendation? 

Any one have any suggestion? :D

---

### Post by dufftime on 2010-01-31
I got a reply to my post! :p

> **MobileNet said:**
> Hi All,

SuperMicro 5015A-L Server 
Atom N230 all-in-one motheboard (support 64-bit)
G.Skill 2GB DDR2-800 CL4
1TB WD Green Drive = System HDD
4x 2TB WD Green Drives in RAID5 (using Rosewill RSV-S4-X eSATA RAID5 External Enclosures, SiliconImage 3726)

This server will run non-stop and I want to use it to store data. I already have a MPC connected to my TV for video, etc.


Double-check the specs on that server.  I believe the Atom processors use laptop memory, so DDR2 667 - it's a different size too.  Oddly NewEgg lists the RAM as DDRII (??) 400/533.  I was going to go with Atom on my build but wanted 6 SATA ports on my mobo, something I couldn't find.

I also used RAID 5 (3 x 1.5 TB).  I'm wasn't sure I wanted to trust my data to the 2 TB as it seems 2TB is at the physical limit.  Maybe I'm being too cautious...

> 
Question:
1. Should I use the Server or Desktop version?
2. I wants to use it to share my HP Laserjet 3030 All-in-one (connected via USB), can ubuntu support all-in-one printer to scan and fax? and maybe network fax from Windows desktop?
3. Does ubuntu support remote control like remote desktop from Windows? Server is not connected to any monitor, remote is needed.
4. Optional: Use it as download server (BT/ed2k/FTP/http...etc)
5. Optional: Stream media to my iPhone (or iPad, I'm planning to get it), any software recommendation? 

Any one have any suggestion? :D
I'm fairly new to Ubuntu myself, but I'll answer what I can.

1.  I went with Desktop.. not sure what the difference is with Server distro.  The GUI (GNOME) was nice to provide an initial comfort level.  Now my server is pretty much headless and I go command line / web interface (PuTTY / Deluge / MediaTomb).  If necessary, I use NoMachine (it's like Remote Desktop) to get to the GUI.

2.  No idea.  Out of curiosity I tried to install printer drivers to my Brother MFC but didn't get far.  It wasn't necessary so didn't look into it much. 

3.  See #1.  You can also use X11 with SSH tunneling, but I was lazy.  I might look into it one day but for now I use NoMachine when I need to get on.

4.  If you plan on running a BT client on your server I recommend deluge.  It has a really nice web 2.0 UI so you can add torrents via web browser. Haven't looked at FTP or HTTP much, but will someday.

5.  I'm using MediaTomb to stream to my PS3 and really love it.  It can do pretty much everything.. and if you need it to do more, just use Google or script the solution :).  I am trying to avoid transcoding to my PS3 as it seems you can't fast-forward/reverse, but sometimes it's unavoidable.  For Video RSS (podcast) aggregating, I'm using gPodder and for iTunes streaming Firefly.  There might be some more Apple friendly streamers... I haven't look at it.

Good luck!
dufftime

---

