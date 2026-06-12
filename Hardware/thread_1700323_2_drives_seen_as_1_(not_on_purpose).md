---
title: "2 drives seen as 1 (not on purpose)"
date: 2011-03-04
forum: Hardware
---

### Post by tommywright on 2011-03-04
I have a very strange issue.  Win 7 took a dump on my gaming machine a few months ago.  It starts up but it's just broken... but that's not my problem.  I just want the data off that drive so I first booted the machine with Ubuntu's disc but I couldn't get Linux to see the hard drive.  So then I added a new hard drive and just installed Ubuntu straight out.  

I've never had Ubuntu on such a powerful machine so I've been playing for months now with it pretty much forgetting what I installed it for in the first place.  Now I'm back to trying to get data off that other drive but again, Ubuntu doesn't see the second drive.

The strangest thing is that the boot screen sees the two drives as one big drive.  Strange right?  Well... now that I think about it, I didn't set any jumpers on those drives so they probably are both seen as masters.  Would that cause them to be seen as one drive?  Is that a sata thing?  Does it try and automatically try to make a raid array out of 2 drives?

Anyway, if anyone has ever seen this before... let me know.  It may be as simple as moving the jumper but I doubt it.

---

### Post by Hedgehog1 on 2011-03-05
tommywright,

Nothing like running Ubuntu on a fast machine, huh?  There is no going back.

To your real question:

The Master/Slave jumpers are only for IDE (PATA) drives on the same cable.  SATA drives are 1 drive to 1 SATA Port (ignoring fancy port replication cards).

When you say the system is seeing the 2 drives as one, do you mean you are seeing a single drive, but with double the hard disk space?

I am trying to understand.

Would you please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.  This will tell us what your system is seeing.

***The Hedge***

:KS

---

### Post by tommywright on 2011-03-05
I'm at work... like always... but I can tell you what it will say.  It will say I have one 1tb hard drive when in fact, I have two 500gb hard drives.  Even the boot screen shows one drive at 1tb.  

When I get home tonight, I'll post what fdisk says.

---

### Post by CharlesA on 2011-03-05
It sounds like the machine is configured for RAID-0, if you've got 2 500GB drives that are being seen as one 1TB drive.

---

### Post by tommywright on 2011-03-05
I know right?  But I built the machine myself so I know it's not (at least ***[COLOR=black]I[/COLOR]*** didn't set it up that way).  It's one of those ASUS gaming mother boards... maybe it's set that way by default?

---

### Post by psusi on 2011-03-05
That is what it sounds like, though that can't happen by accident.

---

