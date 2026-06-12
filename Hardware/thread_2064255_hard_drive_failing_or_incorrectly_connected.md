---
title: "hard drive failing or incorrectly connected?"
date: 2012-09-28
forum: Hardware
---

### Post by broecher on 2012-09-28
I realize this is not really an Ubuntu specific question but I thought someone would probably be able to help me pretty easily. And I also need to get up to 50 posts!!

I am trying to install ubuntu on an old laptop for my kids. As soon as I click install ubuntu, it starts giving me ata1.01: status: {DRDY ERR} errors until it just re-starts from the CD. This error is normal for a hard drive failure I believe.

But since I just ordered the hard drive, I am not sure if it is the wrong hard drive, or if it is really broken.

The connection looks fishy to me... 4 prongs on the hard drive don't connect to anything.

You can See in pic1 that there are 44 pin receptors. There is no separate power cable that I can see.

Pic2 shows the tray for the hard drive. Pic3 shows the hard drive in the tray. the pins line up well with the opening in the back of the tray, but there are 4 pins separated a bit from the rest a bit that are not exposed through the opening. The number of pins that are exposed through the opening is 43 and it appears that it would fit properly.

Thanks for you help!!

---

### Post by JKyleOKC on 2012-09-28
The standard IDE ATA connector is 40 pins. The four that are obscured by the back panel are probably for the jumper that switches the drive from master to slave status. There should be a diagram on the top of the drive that shows where to place the little black jumper to set the desired operating condition. If there isn't, then you will need the spec sheet for the drive to find out.

Having the proper jumper setting is essential; a wrong choice can damage the drive, your motherboard, or both.

---

### Post by broecher on 2012-09-28
This drive is 43 + 4 pins
according to this website

[http://www.cwfree.com/utl/hard%20drive%20chart%20full.png]("http://www.cwfree.com/utl/hard%20drive%20chart%20full.png")

my hard drive is a 2.8 inch laptop IDE PATA.  The picture doesn't show jumpers...

---

### Post by JKyleOKC on 2012-09-28
There should be a label on the top of the drive, with a diagram indicating the connections. However I only have 3.5-inch IDE drives so cannot be sure that all laptop drives follow this convention. Most drive controllers, whether on the motherboard or on a separate card, have the ability to handle either two or four drives, with two drives on each cable. One of the drives is called the master and the other is the slave, and the controller tells which is which by the position of a jumper that connects two of those four extra pins. Unfortunately, the exact jumper coding varies from one make of drive to another. Some of mine have had 8 pins in the jumper area while others have only four. That's why we can't tell you where the jumper should be on your drive.

As for the 43+4 rather than 40+4, if the connector fits on the 43 with nothing left out in the cold (other than the four pins off at the end by themselves) then it would still apply. In the 3.5-inch drives with 40 pins, there are actually only 39 because one of them is removed and its hole on the connector is plugged, so that you cannot put the connector in upside down. I think it's probably similar on yours...

---

### Post by broecher on 2012-09-28
OK so I found the jumper specs online for my drive. No jumpers means its master which is what I want.

So I can assume I connected it properly and the errors mean that the drive is faulty right??

---

### Post by jmore9 on 2012-09-28
What is the name / model number on the drive ? How big is it ?

---

### Post by broecher on 2012-09-28
its a toshiba HDD2153 MK1516GAP 12.07 GB (hmmmm.. it also says 8455MB)

This is the page I looked at to check that jumpers should be off:

[http://storage.toshiba.com/techdocs/HDD_TechNotes_480040_revg.pdf]("http://storage.toshiba.com/techdocs/HDD_TechNotes_480040_revg.pdf")

It doesn't say the exact model number but its pretty close....

---

### Post by ahallubuntu on 2012-09-28
Check the S.M.A.R.T. status of the hard drive.  Try the Parted Magic Linux CD to check S.M.A.R.T.  status (click on "SmartControl") and see if any Attributes are highlighted in red.

That looks like an ancient (and tiny!) hard drive - wouldn't be surprised if it has issues.

---

### Post by broecher on 2012-09-28
Ubuntu live CD asks language, lets me pick from try ubuntu or install ubuntu, etc.... I have tried ubuntu on the laptop and it did work. But when I choose install I get a  black screen, it shows this error over and over with new number each time:

[   191.300850] ata1.01: status: { DRDY ERR }
[   191.300850] ata1.01: error: {ABRT }
[   191.300850] ata1.01: exception Emask 0x0 SAct........
[   191.300850] ata1.01: BMDMA stat 0x5

There were a couple more lines but it just suddenly continued with the install!! - will post back when it finishes

BTW this laptop is from the year 2000 or 2001. It has a windows 2000 sticker on it. The hard drive is defiantly old also. I didn't want to spend anything on this old of a laptop... If I get it working my kids won't know the difference!!

---

### Post by JKyleOKC on 2012-09-28
It does sound as if that drive is on its last legs. The numbers on those error messages you were getting are the seconds since starting to boot, and should never go past 30.something before the system is fully booted. My guess is that there are flaky sectors and the drive is doggedly trying to read them. Apparently it finally managed to get past that problem area, but it might take hours yet -- and I doubt that your kids will have the patience to wait that long for it to come to life.

---

### Post by broecher on 2012-09-28
deleted

---

### Post by broecher on 2012-09-28
Good point - definitely not going to make them use a laptop that takes that long to boot. Will have to see if this install ends, and then try a few boots. It's moving really slow right now but that could be because I opted to use a 12.04 alternate install CD. 

It seems like an OK machine if I could just get this hard drive problem resolved. This is one of those just for fun projects where I'm tyring to make something out of nothing.... 512mb ram, pentium 3, battery lasts at least 30 minutes - haven't run it dead yet, keys and pad work well. I thought it was worth the $5 I paid, and the $10 for the hard drive :( hehe

Thanks for all the advice!

---

