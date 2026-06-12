---
title: "Error says hard drive is full.  It's not."
date: 2010-12-05
forum: Hardware
---

### Post by dogeatery on 2010-12-05
I have a Transcend external hard drive that attaches via USB.  It's been a great piece of hardware and I've come to depend on it now that I am traveling out of country with an 8Gig SSD netbook.

Lately, though, I've been having a problem.  I installed Peppermint a few weeks ago and at first things went normally.  Then one day, while I was downloading some torrents, I got an error message saying the destination drive (my Transcend external hard drive) was full.

I knew this wasn't right.  I checked the volume's properties and it says I have 78 Gigs of free space left, out of 250.

Now other programs, including PCManFM and Wine are giving me the same error messages.  Anyone know what's going on???

---

### Post by dogeatery on 2010-12-06
In case anyone's wondering, I've already checked the .Trash folder.  It's empty.

Is there somewhere else where phantom data gets stored?

Is this a common bug in Ubuntu?  I can't find much else about it anywhere

---

### Post by efflandt on 2010-12-06
Does any partition look almost full when you do: **df -m**

Linux reserves some space for root only in case something runs away and fills up a partition.  I forget how much that is, but it might be a specific partition other than your external drive.

---

### Post by dogeatery on 2010-12-07
Thanks for the reply.  I will run this command tonight after work and post my results.

---

