---
title: "Issues with Marvell 9172 Controller (SSD)"
date: 2015-02-06
forum: Hardware
---

### Post by nechen on 2015-02-06
I recently purchased a new PNY OPTIMA 120GB SATAIII SSD which advertised 500MB/s~ on the R/W but, ironically enough, I can't find advertised speeds ON PNY's website, or Newegg, or anywhere else for that matter.

Anyway I know the Marvell controllers run off the PCI-e x1 2.0 bus which has a max bandwith of 500MB/s so I thought this would work out okay (The Intel ICH10 SATA3 ports are full on my mobo) however these are my results with an hdparm test:

```

/dev/sdd: Timing cached reads:   30902 MB in  1.99 seconds = 15527.84 MB/sec
 Timing buffered disk reads: 1124 MB in  3.00 seconds = 374.40 MB/sec

```

I know for regular use 374 isn't that terrible but I'm curious if anyone here has messed around with their Marvell controllers on 'Buntu 14.04

The only other thing I can think of is my Soundblaster card is currently occupying the only PCI-e x1 2.0 slot on my mobo so I'm wondering if this is chewing up the other 150MB/s~ bandwidth?

Thoughts?

---

