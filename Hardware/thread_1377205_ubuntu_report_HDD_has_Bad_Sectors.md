---
title: "ubuntu report HDD has Bad Sectors"
date: 2010-01-10
forum: Hardware
---

### Post by marcocervantes on 2010-01-10
[LEFT]Ubuntu upon logging-in report that my HDD has bad sectors, but while i was under Windows 7, there was never any problem with bad sectors. How can i check this or fix this? Or could Ubuntu just be wrong? 
[/LEFT]

---

### Post by Dark_Stang on 2010-01-10
If your hard drive is failing that isn't a problem with Ubuntu or Windows 7, it's a bad hard drive. The solution is posted in the message. "Backup all data and replace the disk."

---

### Post by marcocervantes on 2010-01-10
but thats the problem, i know its not a bad hard drive, its just a few months old.

---

### Post by appier on 2010-01-10
The second thing I would advise you to do is to download the disk tools recommended and run some tests on the hard drive to find out if the report is an aberration and the hard drive really is OK or if it truly is failing.  If it is only a few months old, it is most likely still under the manufacturers warranty.  In which case you can send it back to them for servicing or replacement.

Having said that...

**First, back up all of your critical data just in case it is going bad.**  If it were me, after that, I would take a screen capture, print it for warranty reference, replace the disk, and send it in just to be on the safe side.

Of course, it depends upon how important your data is to you.

Hope it goes well!

---

### Post by marcocervantes on 2010-01-10
I used the test that comes with the Ubuntu CD. that is what i got. My disk has no errors.

---

### Post by jongkind on 2010-01-10
These are probably false alerts. See this bug:
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136]("https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136")

---

### Post by Duncan J Murray on 2010-01-10
> **marcocervantes said:**
> I used the test that comes with the Ubuntu CD. that is what i got. My disk has no errors.

Hmmm - are you sure you're not just testing the CD?  I think that is a test to check that your installation CD has been correctly printed before installing an operating system from it.

All best,

Duncan.

---

### Post by Duncan J Murray on 2010-01-10
Also, I have a 6 year old laptop which I use every day - bad sectors aren't the end of the world.  I have 43 bad sectors on my laptop, but it causes no problems...  I think the filesystem just works around it.

Duncan.

---

### Post by Dark_Stang on 2010-01-11
> **Duncan J Murray said:**
> Also, I have a 6 year old laptop which I use every day - bad sectors aren't the end of the world.  I have 43 bad sectors on my laptop, but it causes no problems...  I think the filesystem just works around it.

Duncan.
The problem with bad sectors is they tend to spread like cancer after a while.


Have you run the manufacturer's diagnostic test or just one that came with Ubuntu?

---

