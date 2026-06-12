---
title: "In the search for a new laptop - Dell?"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by Zdravko on 2007-12-04
Hi there!
I want to buy myself a new laptop - Dell more precisely!  Here, where I live, I saw the following ad (excerpt):
 
Inspiron 1501 - AMD Turion 64 X2 TL56 Dual Core 
Turion 64 X2 TL56 Dual Core, 1GB DDR2, 120GB HDD, DVD+/-RW; 
 
System 
Processor: AMD® Turion™ 64 X2 Dual Core Mobile Technology TL56 (1.8GHz, 2x512KB L2 cache) 
Chip set: ATI Radeon®Xpress 1150 
Memory: 1GB DDR SDRAM 
Video Card: ATI Radeon® Xpress 1150 256MB HyperMemory™ (integrated) 
Monitor 
Type: 15.4" WXGA TrueLife™ Display 
Resolution: 1280x800 
[SIZE=2]Discs[/SIZE]
Floppy:    No Floppy 
HDD: 120 GB HDD 5400 rpm 
Optics: DVD+/-RW Double Layer drive 
Net/Interfaces
Net: Integrated 10/100 Fast Ethernet 
Modem: Internal 56k V.92 Modem 
Interfaces: One PC Express Card 54/34 mm card supported; Kensigton Lock Slot; VGA; 4 USB 2.0; RJ-11, RJ-45; 3-in-1 media card reader; Microphone-in port, stereo headphones/speakers port 
Wireless:    Dell™ Wireless 1370 802.11b/g 
Software 
OS: Free DOS 
Warranty: Promotion: 3-Year Extended Warranty Pack FREE 
 
-- 
This one for about 630 € 
 
Now the questions come:
1. Will Ubuntu (here I mean the newest version - Gutsy, or even Hardy Heron) function without any problems?
2. Are there any specific components that may eventually not cowork with Ubuntu? 
3. The Video Card is from ATI. I've heard there are no drivers for Linux yet. Is that true? If so, what are the consequences?
4. (Don't laugh at me!!) Will this laptop be able to run Vista Business Edition properly? 
 
Thanks in advance!
 
Cheers :KS
Zdravko

---

### Post by marpstar on 2007-12-04
To answer your questions:

1. Everything appears like it'll work OK.  Don't know much about the Dell wireless card, other than that they are usually Broadcom chipsets, which I've not had any problems with in Ubuntu.  I've got an IBM x60 that has an Intel chipset and every piece of hardware has worked no problem since Ubuntu 6.10.

2. Again, you might want to research the wireless card.  ATI cards are gradually getting more support.

3. There are Linux driver's available, though not as advanced drivers as the Windows drivers available.  Again, ATI is starting to develop better Linux drivers.  I've got Intel graphics in my IBM and I've not had any video problems with it.

4. The computer will run Vista, though you may want to consider a memory upgrade to 2GB to get Vista running as smoothly as possible.  It makes a world of difference.  Ubuntu, from my experience, will run comfortably on 512MB.

---

### Post by Zdravko on 2007-12-04
Okay. I will wait for a few more answers before I go to buy it.

---

### Post by Zdravko on 2007-12-05
Bump.
I was also thinking of the processor. Is this a dual core 64-bit processor? Will Ubuntu run on it?

---

### Post by coskierken on 2007-12-05
I have an Asus A8JP with the ATI X1700 mobile Radeon.  This card is supported by ATI, but not well.  Indeed, support for ATI is growing.  Ubuntu supports ATI with their restricted drivers.  It works good (not great).  I would check the X1150 for compatibility in 64-bit mode.  The rest of the Dell should work with 64-bit.  I used 64-bit with my Asus (T7200 Core2Duo Intel) and had only minor problems.  I am trying 32-bit again as 64 does not support flash or Java very well.  The ALSA drivers gave me the problem of the mic not being captured, but finally install the Gnome ALSA mixer and it was just a software switch which I had guessed.  Since my laptop is based on the Intel chipset, everything worked.  IMHO, don't get Vista, but have them put in XP.  Until you get more into Linux, some things work  better in XP.  I really only use it to play movies to my TV as I have not figured out how to force the TV out from the ATI card and ripp DVD to MP4 in Nero.  The other problem I had was choppy Video playback of mp4 files in movie player.  I installed Xine, which uninstalls gstreamer and everything works fine now.  If you have this problem, find a link for uBackup! (my friend compiled it) and it has an option in utilities which downloads and installs everything you need for smooth video playback with Totem (Xine) with all the plugins for mp4 and more.  As far as Vista Business Edition, Open Office 2.3 included in Ubuntu opens all Microsoft Office files and you can even save them off in that format if you wish.  I hope this helps and you will enjoy Ubuntu or one of its other versions. :):lolflag:

---

### Post by Zdravko on 2007-12-05
> **coskierken said:**
> IMHO, don't get Vista, but have them put in XP.  Until you get more into Linux, some things work  better in XP.
I am afraid I have no choice. The laptop I pointed to, has a FreeDOS OS. I already own a legal copy of Vista Business Edition. If I insist on removing FreeDOS and replacing it with WinXP, this will result in an increase of the price - approximately 100€. I won't be able to spend that much money. :confused::(

---

### Post by Zdravko on 2007-12-07
I just stumbled upon this site:
[http://www.ubuntuhcl.org/pub/reviews.php?product_id=78](http://www.ubuntuhcl.org/pub/reviews.php?product_id=78)
There is only 1 review about 1501 and it is rather positive! Should I go for it?

---

### Post by Zdravko on 2007-12-07
[http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)
This site features a nice walk through of most problems.

---

### Post by bro on 2007-12-09
Don't buy an ATI card if you run linux. 
Support is growing as mentioned above, but still lousy. I have a x1400 on one machine and 3d desktop effects do not work properly - even with the newest driver. 
I have a dell with intell graphics too that works excellent. Nvidia will propably work good with proprietary drivers but I have no personal experience with that. 
(AMD) 64 bit is propably better supported by Ubuntu and software that runs on it then by that other OS. And you can always install 32-bit Ubuntu as well. 

I have a D830 Dell Latitude and it works completely without any proprietary software.

---

### Post by Zdravko on 2007-12-09
Hmm, I will reconsider my choice then. Later, I may post my second offer here.

---

### Post by Ub1476 on 2007-12-09
Wouldn't it be better to have a slightly higher resolution if you were to buy a 15,4"? I think 12800x800 is regular for the 13" displays..

---

### Post by eggdeng on 2007-12-09
> I have a x1400 on one machine and 3d desktop effects do not work properly - even with the newest driver. 

I have 3D working with my X1400 on 6.06 using the fglrx driver from the repos ( 8.25.18 ). I tried the newer drivers & couldn't get them to work either and it was a chore to get the old one working again - in the end it was a question of making sure everything was uninstalled & starting from a clean slate.
In any case, I would willingly swap out my ATI for an Nvidia, at least until they get the drivers up to scratch. I've read that Intel integrated graphics work well but have trouble with 3D apps like Gogle Earth. Can anyone confirm that?

---

### Post by Zdravko on 2007-12-10
Yes, it would be nice to do so.

---

### Post by sloggerkhan on 2007-12-10
I'd a avoid an ATI card. It's not that they don't work. However, I have an x700 and it's not very flexable for a laptop. For example, if I were to take it around and needed to hook it up to a projector for a presentation, I can't expect it to work because of ATI drivers.

So yeah, while it's functionally, OK if you never move it and don't change anything, I don't think I'd get one on a laptop anytime soon.

---

### Post by bro on 2007-12-10
> **eggdeng said:**
> 
In any case, I would willingly swap out my ATI for an Nvidia, at least until they get the drivers up to scratch. I've read that Intel integrated graphics work well but have trouble with 3D apps like Gogle Earth. Can anyone confirm that?

I have intel with a number 965 and it works a million times better then ATI. Google-earth works too, but has some weird flashes now and then when it wants to display the extra layers of information. I imagine this can be solved with better drivers as well.

---

