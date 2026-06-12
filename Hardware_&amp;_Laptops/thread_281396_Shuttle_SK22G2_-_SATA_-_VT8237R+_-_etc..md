---
title: "Shuttle SK22G2 - SATA - VT8237R+ - etc."
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by CrustyRatFink on 2006-10-21
](*,) 

Hi.

I just bought a Shuttle SK22G2 barebones (expressly to install Ubuntu on), and I've burned most of a day fighting with this.  It's got a gig of RAM and a AMD64x2 processor.  

The basic story is that this box uses the VT8237R+ southbridge, and after replacing with several drives, I always get the same result: lock or crash.  Annoyingly, the built-in "Chrome9" graphics aren't detected either, but I can live with running it as VESA for now (I installed OpenChrome, but that didn't do anything).  

Dapper installs (after a few reboots) and appears to be complete.    If left alone, the system will sit and run.  (FWIW, Edgy is the same story.)  The frequent locks and reboots though make the system unusable.

All the memtest on the RAM is fine.  The box loads up XP fine on any disk.  Try to install Dapper (or Edgy) though, and the Seagate even makes funny chirping sounds.  The WDC drive doesn't make funny sounds, but it crashes just as much.

Basically, the box will boot (usually), but if I try to do anything disk intensive, it locks (sometimes hard rebooting).  If it boots, something like apg-get update will kill it halfway through.  Sometimes a complete freeze, sometimes a reboot.  Never any trail left behind.

Before I get into painful details, is there some known condition that causes this SATA controller to fail like this?  SATA's been around forever by now, and this chipset is also really common.  I'm wondering if there's some tricky solution that I haven't found in my hours of searching.  This is sort of embarrassing after all my arm waving at the office about how great Ubuntu is.

Thanks!

---

### Post by CrustyRatFink on 2006-10-23
This is interesting... something happened since I posted that.  I've upgraded to Edgy on that machine, and it didn't work the first day.  I've subsequently updated a couple of times, and... something changed, but I'm at a loss as to what.  Still, the punchline is that it more or less works now.  The graphics still don't work, but I've added a PCIe nvidia card, and that takes care of that.

The machine has only locked a couple of times in the last day or two (previously, it was every 5-10 minutes).  So, it's still not completely solid, but it's very usable (it's our home public use machine, for games, mail, browsing, etc.)

So, my recommendation is that you upgrade to Edgy if you're using this combination.  Whatever they fixed seems to have helped.

---

### Post by CrustyRatFink on 2006-11-23
Hi Me!  

Oh, hi!  Long time, no see!

Well, me, I need to follow up with the information that this machine still crashes periodically-- a couple of times a day.  Symptoms run the range from flat-out crash to lock-up and rapidly looping sound (ala, the sound of a CD skipping).  

Should anyone else be reading this... and have any info... I'd love to hear it.  Is there anything to be done to get this chipset to play nice?

CRF

---

### Post by CrustyRatFink on 2006-12-23
OK, and I mean this the best possible way, is there any solution to this before we (are forced to) pitch Ubuntu?

This machine STILL crashes a couple of times a day-- just seizes up.  That's something I'd expect from Windows 98.  Turns out that my insistence that Linux is cool isn't cutting it anymore.  Too many people losing their mail halfway through or games when they're almost the world champs.

C'mon, throw me a bone.  Any ideas what I might look for?

---

### Post by firemankurt on 2006-12-31
I just ordered the same computer from NewEgg so maybe we can work together to get issues resolved.  I hope I don't regret buying this machine but I just could not see investing in a single core system when I could afford this MB and cool case.

Here is my order:
CPU AMD|A64 3200+ 2.0G AM2 512K R - Retail
BRBN PC SHUTTLE SK22G2B K8M890CE R - Retail 

(I could not afford a dual core processor yet but just wanted the ability to upgrade.)

1GB RAM is next but waiting for a little birthday money in the next couple days.
I have a 200GB HD and DVD-RW that I will use too.

If you have any tips let me know.  I will post any devine revelations here as well.  Thanks for the only post I could find about this system.

Kurt Jensen
Ferndale WA USA;)

---

### Post by CrustyRatFink on 2007-01-15
I hate to say it, but you might want to consider all your options here-- even XP-- if you already bought the machine.  If not, re-read my posts.  It's a real pain unless you like spontaneous combustion in your computing environment.

At least in my house, my wife has forbidden Ubuntu outside the walls of my geeky little office, and I've just stopped using it in most places.  It just doesn't work on this machine, and I've had XP on it without issue.  It, as with most desktop Linux, just isn't cooked.  The simplest thing (switching users, hibernating, accidental keypress, etc.) can send Ubuntu into seizures even on a machine that does "work" with it.  

You gotta learn to live with that if you're going to play with it.  It's just the nature of "free as in beer."

Don't know if a different distro would work better, but I'm pretty tired of farting with it.  I still use Linux in several work machines.  Certainly, I'd take a Linux web server over a Windows box any day.  After that, it gets pretty iffy, pretty quick.  So, this machine may end up serving web pages.

Otherwise, if I can get this guy going (hopes are not high at this point), I'll likely redeploy it as my kid's tux paint box.  The world's most powerful tux paint dedicated computer!

Good luck!

> **firemankurt said:**
> I just ordered the same computer from NewEgg so maybe we can work together to get issues resolved.  I hope I don't regret buying this machine but I just could not see investing in a single core system when I could afford this MB and cool case.

Here is my order:
CPU AMD|A64 3200+ 2.0G AM2 512K R - Retail
BRBN PC SHUTTLE SK22G2B K8M890CE R - Retail 

(I could not afford a dual core processor yet but just wanted the ability to upgrade.)

1GB RAM is next but waiting for a little birthday money in the next couple days.
I have a 200GB HD and DVD-RW that I will use too.

If you have any tips let me know.  I will post any devine revelations here as well.  Thanks for the only post I could find about this system.

Kurt Jensen
Ferndale WA USA;)

---

### Post by salvo on 2007-01-25
I guess firemankurt has nothing new to report.  CrustyRatFink, if you are using one of Shuttle's supported RAM sticks, which one did you go with?  Are you using their latest BIOS (FX22V1.x dated 12/20/2006)?  And speaking of BIOS, did you try tweaking any settings?  How about the Live CD?  If that comes up better one way or another, then you might benefit from determining what is different.

I am currently enjoying an SK21G running XP64; it's been rock solid.  After lengthy research, I have weighed the risks and decided to introduce Kubuntu on an SK22G2.  I am well aware of the frustrations it has brought to others; however, it seems that none of the Shuttles are spotless.  This will be my first outing with Linux, but not with unix (OpenStep years ago).  I am ready to play the "fool" and climb the learning curve, whatever the cost.  

I will be making my purchase early next week, and will keep you posted . . . .

---

### Post by salvo on 2007-01-26
> **salvo said:**
> I guess firemankurt has nothing new to report.

I see from his feedback on NewEgg that he was very pleased with his results.

---

### Post by salvo on 2007-02-07
Brief update:

Kubuntu 6.10 Live CD boots fine.  OpenOffice and Konqueror ran fine.  Video scrolling was sluggish; I noticed that video scrolling is much better on Knoppix 5.0.1 Live CD.  For me this is not likely to be much of an issue since I plan to remote desktop into it most of the time.

---

### Post by salvo on 2007-02-10
6.10 installation was uneventful.  Bare bones installation runs just fine.  Onboard video is sluggish and is perfectly fine if you plan only to administer it; it's marginally acceptable if your graphics needs are simple; otherwise, I recommend a video card.  I plan to remote desktop to it; so the video performance will meet my needs.  Your mileage may vary.

---

### Post by zvbxrpl on 2007-10-09
I'm thinking about purchasing a SK22G2 to run Ubuntu Gutsy.  I noticed that a NZ company offers Ubuntu with this box:

[http://www.talktechnow.co.nz/Shuttlesystems.pdf](http://www.talktechnow.co.nz/Shuttlesystems.pdf)

I know nothing about this company and this isn't an endorsement (I'm in UK).  But presumably it must be possible to configure the SK22G2 stably with Ubuntu, or they probably would have chosen another box in Shuttle's range.  Just a thought.

---

### Post by barratt_sab on 2007-11-02
I've just build an SK22G2 with Athlon X2 and OCZ RAM, and put 7.10 on it - and it works very well so far (about a week in).  At present, I am using the onboard graphics, which are fine for a typical "office" user.

I've put more information here:

[http://two.xthost.info/SK22G2/](http://two.xthost.info/SK22G2/)

---

### Post by tseller on 2008-05-07
CRF,

I bought a shuttle SK22G2 barebones in december 2006. I added 2GB patriot RAM (don't know further specs off hand), and a WD hard drive.  And a DE/DVD player/burner.  From day 1, this thing crashed right and left.  Maybe only one day in the last 1.5 years has it not crashed.  Either it reboots itself, or pseudo bluescreens, by which I mean it looks like it's trying to write a blue message on a black background, except that all the characters are 50x magnified and spread out, so that I have zero idea what it says.  I suspected that it might be my USB controller driver since the crashing was more frequent if I had something plugged into USB.  But other times I suspected it was the DVD drive.  I was lucky to burn a CD without a crash.  Finally, last week I bought a new hard drive to do a fresh install, and things were crashy at first until I finished updating the USB controller drivers (but upgrading to XP SP2), then things seemed to be fine.  But! now, tow days later, I have had two crashes.  So I am despairing again...  

I thought I'd share this with you in case it made a difference to you or somebody.  Mostly, I hope Shuttle takes this seriously. My videocard  was built into the MOBO, as in I did not buy a special one.  Someday....

---

