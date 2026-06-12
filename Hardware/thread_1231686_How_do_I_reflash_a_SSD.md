---
title: "How do I reflash a SSD?"
date: 2009-08-04
forum: Hardware
---

### Post by josephellengar on 2009-08-04
You know, "really" delete all of the data so that it is virgin and to get rid of the possible decrease in performance over time.  Thanks! :D

---

### Post by mtbsoft on 2009-08-05
You don't.  SSDs don't suffer from fragmentation and seek time/lag as there are no moving parts, unlike a disk which has to wait for the head to reach the correct cylinder and the disk to spin the correct part under the head.

By rewriting the entire recording "surface" of an SSD you would actually be reducing its life, as each memory location only has a finite number of writes possible before it fails.

Once you delete the data, it is to all intents and purposes gone and has no more influence on other data than before it was deleted.

---

### Post by josephellengar on 2009-08-05
> **mtbsoft said:**
> You don't.  SSDs don't suffer from fragmentation and seek time/lag as there are no moving parts, unlike a disk which has to wait for the head to reach the correct cylinder and the disk to spin the correct part under the head.

By rewriting the entire recording "surface" of an SSD you would actually be reducing its life, as each memory location only has a finite number of writes possible before it fails.

Once you delete the data, it is to all intents and purposes gone and has no more influence on other data than before it was deleted.

I'm not talking about fragmentation.  SSDs slow down over time because the deleted cells are not truly deleted.  Reflashing it brings its speed back to factory standards.  (I've done my research)  And the usable life for these things is now so long that I'm not really worried about the wear that it would cause.

---

### Post by mtbsoft on 2009-08-06
According to [Intel]("http://news.cnet.com/8301-13924_3-10168084-64.html"), the degradation in speed you are talking about is not as significant as some believe unless the drive is full, and other sources I've read suggest that most drives' speed degradation levels off after a while, presumably once the entire memory has been written to once.  It is also only the write cycle that slows down, reading remain unchanged, so static information such as applications should not be impacted.

As for the life of the drive, depending on the quality of the manuafacture, the cheaper of the two types of drive (MLC, as opposed to SLC) some reports suggest they can sustain as few write cycles as 2000 before problems start.  So regular reflashing (if possible) for minimal speed gain could significantly reduce the life of the drive, assuming you write regularly to it.  

If it is possible, I would expect the drive manufacturer would supply their own utility but I would still question the value of such an approach.

---

