---
title: "Any SATA horror stories?"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by MattDTownsend on 2007-06-25
I don't believe this is Ubuntu-related, but I'm posting here in case it might be.

---

When I decided to build a new system last summer, I was quite surprised to see that SATA was now the default choice for hard disk connections, at least in North America.  Frankly, I'd never even heard of it, and when I saw how small the connectors were, and how loose they looked, I had my doubts.

It wasn't long before I started having problems -- i/o errors that seemed to suggest the hard disk had just stopped -- like I had pulled it out whilst it was on.  Of course, there's no OS in the world that cares for this.  The system effectively locks as stdout shows lovely messages about sda1.

I noticed that reseating the cables before restarting would fix the problem, albeit temporarily.  Well, things improved a bit after I decided to hot glue the cable onto the disk and the motherboard -- with stability, disconnects seemed to occur much less often.  After a while, though, the problems seemed to return. . .to the extent that my southbridge was fried.  Even my ATA drive couldn't be seen.  I ordered a new motherboard, sent the drive back to seagate for good measure, and installed a new WD 500 gb SATA drive.

And, for a week or so, everything seemed fine.  Guess what's back, now?  Those seemingly random disconnects.  I just finished hot gluing the cable onto the drive, but I hope to avoid aiming that thing at my new ASUS board.

What the hell is with this?  The only other friend I have who's on SATA now. . .when I brought up the general topic of the interface, asked me if I knew a way to "secure" the cables because they seem "too loose."  I pointed to my hot glue gun.  And when I was in Toronto a few weeks ago, I walked into a computer repair shop and asked the owner how I might solve my SATA problems and if they were common.  He pointed behind me.

To his hot glue gun.

He said that a sizable number of customers kept returning units because of SATA disconnects.  With the most chronic problems, he eventually forced the manufacturer to send him ATA133 replacements.

Seriously, is this in my imagination?  Does anyone else think something is fishy with this technology?  Why should I have to hot glue ANYTHING inside of my box to make it work?

Thoughts:
* Is SATA a lemon technology?
* Possible power source troubles?  That's all that's original to this system, now.
* Go back to IDE?
* If it's just me with this problem, then why would a computer repairman share similar tales about totally different systems running totally different OSes with parts bought in a totally different country?

---

### Post by Luke Davis on 2007-06-26
Sorry to hear about your trouble with SATA. MattDTownsend.
I myself have never had a SATA cable become disconnected and I know that it is not a lemon technology as it is faster then the old IDE drives which helps to remove a bottle neck in PCs. If you don't want to hot glue your MoBo, you can buy other MoBo's with locking SATA connectors so that the cables don't come free. This is the new generation of SATA connectors and I expect will become standard on all MoBo soon. If you don't want to do that I would suggest that you tie all the cables inside your computer. I hope this helps and reassures you that SATA is a necessary improvement in hard drive technology.

---

### Post by Dokatz on 2007-06-26
I bought a SATA drive back when I upgraded to 64 bit (When 3000+ was the standard) years ago...
My IDE drive failed eventually, And all my SATA drives have always been chugging along and I've never had ANY sort of trouble with them; Be it on windows or ubuntu, freeBSD, Fedora, Knoppix or uh...Sabayon?

So no horror stories personally; And now that I think about...Nobody I can recall had a SATA drive fail lately. Might just be luck.

EDIT:

Also, SATA is a breath of fresh air of a standard if you've ever tried to hook up a dozen or more IDE drives all in one tall tower...You're in for some drawn-out Oragami...If you get my drift)

---

### Post by MattDTownsend on 2007-06-26
It's good to hear that SATA isn't a lemon.

Actually, this MAY be ubuntu, kernel or hald related.  The glue didn't help (this time), which isn't surprising because the WD cable looked much nicer than the last one I had. . .didn't think it was a problem.  I paid attention to the stdout and caught the keywords "emask" and "exception."  

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603)

This is almost certainly my problem.

Anyone have experience with this?  I've decided to pull my two DVD drives until further notice.  I don't use them that much, anyway, and if I can keep an uptime of a few days without a problem, then I'll resort to crossflashing.

---

### Post by dabl on 2007-06-26
I concur that the new SATA cable/connectors are visibly less confidence inspiring than those good old 40-pin IDE ribbons.  (Of course, once you've accidentally pulled a ribbon cable out of it's stuck connector .....).

But, on one PC I've been running a pair of WD Raptor 74G drives for 3 years now, mirrored, and with zero issues.  On my new Linux box, I've been running a pair of WD Raptor 150G drives for 6 months, alongside a Maxtor IDE drive, and no problems there, either.  And of course the performance of the SATA drives kinda blows away the old ones.  So, no horror stories here!  :)

---

### Post by stchman on 2007-06-26
I have never been a big fan of SATA.  The SATA lovers propagate myths and such.

- SATA are not faster.  The areal density and spindle speed are the bottlenecks not the interface.
- SATA drives are no more reliable.  The only difference between a SATA drive and a PATA drive is the interface


I personally think SATA is a PITA.  When all OSs fully support SATA I will jump on board.  Thankfully Ubuntu does.

Now in server applications SATA is excellent as they are hot swappable and far less expensive than SCSI.  For the average desktop user there is no benefit of going SATA.

---

### Post by tonymaro on 2007-06-28
One time while swapping video cards I completely snapped the card-edge connector off the hard drive.  Yeah, that effectively separates you from your 180 GB of data.  The first time I saw a SATA drive my thought was "Darn that connector looks flimsy."

[http://www.maro.net/ossramblings.php?itemid=212]("http://www.maro.net/ossramblings.php?itemid=212")

On the other note of disconnects - I'm having that problem on a board right now and it seems driver related, not cable related, so don't assume all your flaky SATA issues are cables.
[URL="http://www.maro.net/ossramblings.php?itemid=326"]
http://www.maro.net/ossramblings.php?itemid=326[/URL]

---

### Post by Atomic Dog on 2007-06-28
No question there are horror stories about snapped off SATA connectors on motherboards, and on drives.  You must be more careful inserting and removing these connectors than the old 40 pin IDE connectors.  

I treat SATA connectors very gingerly, and make sure I don't break anything.  Other than that, SATA is the bomb!

---

### Post by Rui Pais on 2007-06-28
> **stchman said:**
> I have never been a big fan of SATA.  The SATA lovers propagate myths and such.

- SATA are not faster.  The areal density and spindle speed are the bottlenecks not the interface.
- SATA drives are no more reliable.  The only difference between a SATA drive and a PATA drive is the interface


I personally think SATA is a PITA.  When all OSs fully support SATA I will jump on board.  Thankfully Ubuntu does.

Now in server applications SATA is excellent as they are hot swappable and far less expensive than SCSI.  For the average desktop user there is no benefit of going SATA.

++

In my case my conclusions with SATA (2 drives till now) are: 
1) much noiser, i distinctly hear the disc access.  (And I have read threads about noise that appears periodically on SATA). 

2) SATA drivers on Linux are a little "lemon", as you say (here we say green). Kernel sometimes detect my sda as sdc. And with mixed SATA/PATA some times they are hda/sda and sometimes sda/sdb :rolleyes: (i sometimes think that UUID was invented as a workaround for this :( ) 

Others weird issues include hdparm not working anymore, and amazingly (don't know if thats is been solve by  now) when a PATA is detected as sdX hdparm refuses to work on them too.

---

### Post by samuraiCat on 2007-06-28
Nope. My Caviar 250G SATA drive hasn't snapped, died, been noisy, disconnected, or been slow. I dig it!

---

### Post by hardyn on 2007-06-28
I think the cables is reason enough, trying to get two 80pin ATA cables in the a small uATX case really sucks!

---

### Post by david_2001 on 2007-06-28
sda:  Samsung SP2504C SpinPoint 250Gb now six months old.
sdb:  Maxtor Diamondmax 10 200Gb which celebrates its 2nd birthday in a few days time.

No problems with either.

---

### Post by logos34 on 2007-06-28
sata is a lot of hype.  I completely missed the hot-glue issue but maybe that's because I'm all pata and haven't been to computer parts store in a long time.  The advantages of sata all come down to dedicated channels for each device (no master/slave bottlenecks) and thin data cables.  'It's the cable, stupid' (flexibility, airflow. etc).  But the connectors are really fragile and WD was the only manufacturer early on to have snap connectors to keep the cables from slipping off.  The engineers should have been shot.  All my drives are IDE, but I did advise some stupid relative of mine (she really is a bitch) a couple of years ago to get a 'faster' sata 150.  So for a dollar a gig back then she got a drive that is actually slower than my pata.  I clocked avg. read speed at 45 MB/s (I get 55-60 on a ata133).  And the intel board she was using and XP home only showed udma5 mode.  Boot time is slow. The thing is slow. (But I'm savoring my schadenfreude.  Bitch).  At the time I just chalked it up to windows ata drivers which run in emulation mode for sata.  I know there were no sata drivers to load--checked.  Unless the sata controller on the intel 915 was the issue. 

Maybe the sata II/300 are a lot better now.  But if you look closely at the manufacturer specs you'll see that satas are often just IDE models with a different interface--the buffer-to--host and buffer-to-disk rates are identical.  NCQ is no big deal.  More hype.  150 or 300 MB/s -- those are THEORETICAL burst rates you might get for like a nanosecond.  (I'm exaggerating but I'm on a rant here).  Ok, so it makes RAID a lot easier. But other than that I just don't see much to write home about here.  You will hardly even notice the diff on a 7200rpm disk in everyday use.  But you might snap a connector.

---

### Post by logos34 on 2007-06-28
Here's a case in point of hype/myth (from dabl above)

> I've been running a pair of WD Raptor 74G drives for 3 years now, mirrored, and with zero issues. On my new Linux box, I've been running a pair of WD Raptor 150G drives for 6 months, alongside a Maxtor IDE drive, and no problems there, either. And of course the performance of the SATA drives kinda blows away the old ones

The reason it 'kinda blows way the old ones' might have something to do with the fact that they're raptors  screaming at 10,000 rpm.  And when you mirror them your read rates go up even further.  It's your spindle speed and RAID1 that's giving you that performance, not sata per se.

---

### Post by hardyn on 2007-06-28
> **logos34 said:**
> .  So for a dollar a gig back then she got a drive that is actually slower than my pata.  .

It could have been a cheap drive, the seagate momentus in my notebook, that i paid WAAAY too much for, @ 5400 rpm, is as fast or slightly faster than a cheap 7200 rpm.

the mechanics of a hard disk have been the same since the mid 90s, there isn't much more they can to there other than improve precision and interface.

did you think that the reason that the raptors are capable of 10000rpm and the accompanying  transfer rate is perhaps  because of the SATA interface?

---

### Post by dabl on 2007-06-28
> **Rui Pais said:**
> 
Others weird issues include hdparm not working anymore, 

Try sdpam  ;)

---

### Post by logos34 on 2007-06-28
> **hardyn said:**
> It could have been a cheap drive, the seagate momentus in my notebook, that i paid WAAAY too much for, @ 5400 rpm, is as fast or slightly faster than a cheap 7200 rpm.

well, it was a seagate [sta16023AS or something if I recall].  Yes, and some 4200rpm notebook drives are actually faster than 5400's, depending on what parameters your are measuring (random seek vs. sustained transfer, etc etc).  

> did you think that the reason that the raptors are capable of 10000rpm and the accompanying  transfer rate is perhaps  because of the SATA interface? 

Well, I'm no hard disk technician, but a raptor's data transfer rate doesn't even saturate the bandwidth of IDE ATA 6 interface (133 MB/s).  It's the spindle speed, your latencies and random seek times are way low because of that, not the interface.  The platter is spinning 40% faster.  And then you add RAID on top of that and your rates are just way off the charts compared to ide.  That's where the speed is coming from, not sata.  Like you said the nuts and bolts of hard drives haven't changed much and there's not a whole lot else they can do to get more speed out of them (perpendicular technology is one, but that's mostly about size).  If they could figure out a way to really speed up the transfer of data from disk to buffer and vice-versa, it hardly matters that you have a sata interface capable of 3.0 Gigabits/s.

---

### Post by z0phi3l on 2007-06-28
Contrary to some naysayers around here, SATA is the way to go, faster drives, smaller cables, all around better interface.

If you are having problems, try actually buying some decent cables and replace the cheap ones that sometimes come with the drives.

---

### Post by pseudonym on 2007-06-28
> **z0phi3l said:**
> Contrary to some naysayers around here, SATA is the way to go, faster drives, smaller cables, all around better interface.

If you are having problems, try actually buying some decent cables and replace the cheap ones that sometimes come with the drives.
In any case, the debate is kinda academic, since AFAIK all drive manufacturers have either ceased production of PATA or have had it in end-of-life phase for some time now.

---

### Post by Nythain on 2007-06-29
well then... sounds like im not the only person having this problem... i've been inquiring about weird hard drive behavior for the last few days... at first i thought it was a usb issue, since its an external hard drive... so after bustin the bad boy open i realized it was a sata drive and not IDE wich lead me to this thread where people seem to be suffering similar issues as me... see one of my few threads here
[http://ubuntuforums.org/showthread.php?t=485972](http://ubuntuforums.org/showthread.php?t=485972)

---

### Post by logos34 on 2007-06-29
> **pseudonym said:**
> In any case, the debate is kinda academic, since AFAIK all drive manufacturers have either ceased production of PATA or have had it in end-of-life phase for some time now.

The man does have a point.  they are phasing it out slowly but surely, for hard disks at least  (ATAPI for cd/dvd will be around for a while longer).

---

### Post by Rui Pais on 2007-07-01
> **dabl said:**
> Try sdpam  ;)

Hi, sorry the late reply (almost forget it).

I don't use sdparm or hdparm (except for benchmark) I never seen any speed ups with that so i give up...
But you cut my quote, making possible different meanings that i have in mind... so i'll quote myself (no cuts ;))
[QUOTE=Rui Pais]Others weird issues include hdparm not working anymore, and amazingly (don't know if thats is been solve by now) when a PATA is detected as sdX hdparm refuses to work on them too.[/QUOTE]
the problem is not using sdparm for sata (not very useful in fact since [libata doesn't support 32 bits I/O]("http://linux-ata.org/faq.html")), but what to use when pata is detected as sata. Neither hdparm nor sdparm work in that case. 

Again i don't have any problem with that, but some users have, specially those who suffer from bad performance pata, that can work nicely with dms and 32bits on, [here a thread]("http://ubuntuforums.org/showthread.php?t=400356") on it.

Here a general wiki on problem with SATA under Linux:
[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux)

It don't means that everyone will have issues, or any SATA HD will failure miserably. 
Means that problems exist and support for sata is recent. Thats all.

---

