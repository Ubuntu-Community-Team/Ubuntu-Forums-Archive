---
title: "can't burn dvds/cds anymore"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by Coogan on 2007-08-17
A few weeks ago, my DVD burner up and basically stopped writing blank DVDs and CDs.  The burner is a 4-year old 2.4x burner I'd had in a previous Windows system, so I figured I'd burned out the write head.  Since I don't burn much on my Vista system anymore, I swapped out the burners between the two.  When I loaded up Vista, my suspicions were (I'd thought) confirmed; Windows couldn't read anything I put into the older burner.

I dropped a blank DVD into the newer burner (now in the Ubuntu system), but sure enough, it was still not able to write to it.  Everything seems to be fine - I'm at a loss as to what the problem is.  Gnome recognizes the blank disc.  DVD+RW-mediatool recognizes all characteristics of the blank disc.  But as soon I as I go to write anything to it, it errors out.  First, it burned a bit to the disc for a few seconds, then said "Finished!" and ejected the disc; this was a 3.8 gig ISO file.  The 2nd attempt, it errored with "unspecified error" (or something like that) after spending a minute preparing to write.

The drive reads with no problems; I was able to insert several movie DVDs and Totem played them all without a hitch.  But for some reason it just cannot write to a blank anymore.

As far as the logs, I've found "cdrom: This disc doesn't have any tracks I recognize!" all in my kern.log files.

Any suggestions?  Like I said, I'm at a complete loss, and I don't want to buy a new burner and find out it's a build problem.  I've even reinstalled the cdrecord package from Synaptic, with no success.

This is a Dapper LTS build, btw.

Coog

---

### Post by Total_Biscuit on 2007-08-18
> **Coogan said:**
> I dropped a blank DVD into the newer burner (now in the Ubuntu system), but sure enough, it was still not able to write to it.  Everything seems to be fine - I'm at a loss as to what the problem is.  Gnome recognizes the blank disc.  DVD+RW-mediatool recognizes all characteristics of the blank disc.  But as soon I as I go to write anything to it, it errors out.  First, it burned a bit to the disc for a few seconds, then said "Finished!" and ejected the disc; this was a 3.8 gig ISO file.  The 2nd attempt, it errored with "unspecified error" (or something like that) after spending a minute preparing to write.
The quick finish is what normally happens (to me, anyway) when attempting to burn a file that's bigger than the 2Gb ISO file size limit.  Were any of the files inside that ISO image larger than 2Gb?

---

### Post by Coogan on 2007-08-18
Checked the ISOs and no, the largest sized files in them were just over 1 G.

Coog

---

### Post by Coogan on 2007-08-19
Any other info I can offer?  I don't mind replacing the burner but I'd like to make sure it's not a problem with Dapper.

Chris

---

