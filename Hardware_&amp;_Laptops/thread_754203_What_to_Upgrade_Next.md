---
title: "What to Upgrade Next?"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by Literati on 2008-04-13
Hi all,

I'm getting into the habit of enjoying tinkering with the insides of my computer :P 
I just finished upgrading from 512MB RAM to 2GB RAM (2x1GB) and notice a pretty big difference (Expecially in the amount of swap being used)

Here is the output from lspci 

```
matt@Matt:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
02:0b.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
02:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
02:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)

```

It's a pretty old, custom built, PC. What would you guys suggest upgrading next? I'm open to all suggestions.
My computer is open already, so if you need me to check something for you, let me know, and I'll check it out and post back! :)

Thanks!

---

### Post by Literati on 2008-04-13
Here's some extra info, if it helps:

Intel Pentium 4 CPU 2.40 GHz
2.0 GB RAM
Boot Drive: 80GB (This drive is old, how can I find out more about it?)
/home Drive: 400GB
DVD-RW Drive
CD-RW Drive (Don't use ever)
Video Card: Radeon 9600 (Don't game)
Sound Card: Creative Labs SB Live!

---

### Post by jacob01 on 2008-04-13
upgrade the video card and perhaps see how much you can over clock the processor and ram and ..... anythign else  :lolflag:

ohh and you could get a tv tuner, i guess they are pretty hard to get going in linux. That would give you a project for a lil while.

i don't really know what you are trying to make out of your computer, gaming rig, multimedia, server....

it seems pretty complete as it is. once you start upgrade one thing the next component will be the bottle neck and this becomes an ongoing battle until everything is new and top of the line. soo idk what you want to build   

im kinda building a little linux budget gaming rig so that my project. I had a relatively new dell core 2 duo desktop and got a new video card for it and i can see how i need more ram so yea. After than i would want to upgrade the mobo then processor and for that i would need a new power supply then with that new mobo and power for sli i would like sli so theres another video card, and it just keeps going. and then a new case lol

lol whats your budget on this build?

---

### Post by Literati on 2008-04-19
I don't really HAVE a project. 
I'm just fascinated by it, and figure that building and fixing it will help me learna and keep me busy. :)

I'm working on a 17 year old's budget here, so it can't be fantastic.
But once I save a bit of cash, I'm going to completely overhaul it, just for the heck of it. I'll keep what I have now, and then create a new computer from scratch. :)

---

### Post by em3raldxiii on 2008-04-20
I'd go with a new vidcard for sure.  Even if you don't use it for gaming, you are going to notice some performance boost on many apps with a better card.

Next, I would definitely upgrade your 80G HD to something better.  You can tell number of things about it just by pulling it out and reading the info on the top.  If it's 80G, it's probably an IDE hd (wide ribbon cable also give this away), and it might be only 5400rpm (slower than the 7200rpm standard nowadays).  So if you grabbed a higher performance HD you'll see a difference with how long it takes to boot, and how long it takes apps to start.  If your motherboard supports SATA hard drives, then that will make an even bigger difference.

If you use your computer for watching movies or listening to music, get yourself a nice 5.1 surround set of speakers, and upgrade your soundcard ... the SB Live! is getting pretty old and there are plenty of cards that produce nicer sound.  You don't have to stick with SB, either.

Your motherboard might be maxed out for RAM now, so that's probably not going to help you ... besides, on your rig that's definitely not the bottleneck.

Overclocking your processor is a definite possibility.  You can fairly easily get another 10% out of it ... possibly more.  That can get you a small performance boost across the board.  Depends a bit on your processor and motherboard though.

Also, bigger/better monitor, wireless mouse/keyboard, fancier case or "chassis", going with a RAID array on your harddrives, higher performance DVD burner (or heck, blu-ray? hehe).

At some point, your bottleneck is going to be your Motherboard ... and upgrading that can make a HUGE difference ... but might necessitate upgrading other parts because of non-backwards-compatibility.

If you are in North America, check out this site:  [http://www.ncix.com](http://www.ncix.com) for buying hardware -- HUGE selection, good service, great prices (and price matching), and usually they have some kind of shipping deal that makes it cost effective.

Good luck!

---

