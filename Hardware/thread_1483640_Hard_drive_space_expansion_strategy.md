---
title: "Hard drive space expansion strategy"
date: 2010-05-14
forum: Hardware
---

### Post by ohzopants on 2010-05-14
I currently have a 1TB drive in my HTPC desktop.  It has two partitions, one minimal / partition and the rest is dedicated to /home.

My issue now is that I am rapidly filling up the drive and I'm looking to add a second physical disk to the system.  This would be trivial if I could just accept having a separate mount point but I'd really like to have them considered to be one drive (e.g. one mount point).

I'm also considering buying the smallest drive I can get my hands on to use as /.

So far I figure my options are RAID, JBOD, or LVM and I've done some basic reading up on all of them.  The one thing I haven't been able to figure out definitely from the info I've found is whether I can do any of this WITHOUT losing the data I already have.

Has anyone been in a similar situation?  Any advice?

The closest I can think of in my head is to create a new LVM "group" with just the new drive, transfer the data from the old drive over to this group, wipe the old drive, then add it to the LVM.  Does that make sense?  (Yes, I know my LVM terminology is way off.)

P.S.  Failure to find me an elegant solution will force me to simply convert my HTPC to a gaming rig, get an Ion based system and a NAS. (Not that the pending release of a native Steam client has anything to do with that idea :))

---

### Post by srs5694 on 2010-05-14
> **ohzopants said:**
> The closest I can think of in my head is to create a new LVM "group" with just the new drive, transfer the data from the old drive over to this group, wipe the old drive, then add it to the LVM.  Does that make sense?  (Yes, I know my LVM terminology is way off.)

Yes, terminology aside, this makes perfect sense, and it's what I'd do in the situation you describe. With something approaching 1TiB of data, of course, it'll take a while to do the copying, but it will work. I've done this sort of thing before.

---

### Post by cascade9 on 2010-05-15
Why not get a 160-320GB drvie, use that for / and /home, then use the 1TB drive as a single data partition? 

I know, its one more mountpoint than you want, and its a really good idea to copy the data from your current /home somehwere while you change the partitions (yes, I know, you can resize partitions but I'd never do that without backing up the data 1st). 

Seems to be a lot easier than sodding around with LVM or JBOD (RAID wont help you at all...well, you could go mirror RAID but thats got issues).

---

