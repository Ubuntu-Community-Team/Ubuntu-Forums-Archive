---
title: "Copy speed?"
date: 2011-11-18
forum: Hardware
---

### Post by Moozillaaa on 2011-11-18
I'm copying multiple terabytes, and the copy speed is not really that fast...

AMD Athlon 64 x 2 6400+ 3.2Ghz  

2 x (2 x 64KB L1 cache) 
2 x (2 x 1MG L2 cache)

2 G DDR2 5300 ramsticks

That PC is offline, nothing else is 'running' on it; what should be the copy speed about?


ed.:
Both drives are onboard - 1 drive is port 1 PATA, other is port 3 SATA
SATA 3 Gb/s
64 Mg cache

---

### Post by dabl on 2011-11-18
Data throughput is going be limited by the PATA channel.  The max (burst) rate is 133 MB/s (assuming the most recent ATA standard), but you won't see anything like that on a sustained copy -- it will be closer to 30 MB/s.

[http://www.dewassoc.com/kbase/hard_drives/media_transfer_rates.htm](http://www.dewassoc.com/kbase/hard_drives/media_transfer_rates.htm)

But I have never heard of a TB class PATA drive --  :confused:

---

### Post by Moozillaaa on 2011-11-18
> **dabl said:**
> Data throughput is going be limited by the PATA channel.  The max (burst) rate is 133 MB/s (assuming the most recent ATA standard), but you won't see anything like that on a sustained copy -- it will be closer to 30 MB/s.

[http://www.dewassoc.com/kbase/hard_drives/media_transfer_rates.htm](http://www.dewassoc.com/kbase/hard_drives/media_transfer_rates.htm)

But I have never heard of a TB class PATA drive --  :confused:

I don't know exactly what TB class PATA is; FoxConn board has 6 SATA channels, but 10.04 Disk Utility shows 4 SATA channels 

(1.5tb, 2 x 2tb, 3tb), and 

3 PATA channels (2 are SATA drives(2 x 2tb), 1 an IDE (250g, which is actually ON an IDE header (slave) ) ).

Means nothing to me tho', except for 16.8MB/s transfer SATA - PATA :confused:...

---

### Post by dabl on 2011-11-18
> **Moozillaaa said:**
> I don't know exactly what TB class PATA is; 

3 PATA channels (2 are SATA drives(2 x 2tb), 1 an IDE (250g, which is actually ON an IDE header (slave) ) ).


Ah -- OK.  In your original post, you said "copying terabytes" and then "both drives", and I was trying to imagine what kind of PATA (ATA/IDE) hard drive you could possibly have.

I dunno, I would expect you would get closer to 30 MB/s.  It would be interesting to see what happened if you booted some other Linux distro, like aptosid or Parted Magic, and tried the same copy process.  In other words, it would be nice to figure out whether the limit is in your hardware, or your installed OS.

---

### Post by Moozillaaa on 2011-11-18
With a live load of Parted Magic (or aptosid), should I get 30 MG/s copy speed?

I still have 6.75+ Tb to copy, after this 2Tb is finished...




Thanks for feedback here, btw...

---

### Post by Moozillaaa on 2011-11-21
> **dabl said:**
> Data throughput is going be limited by the PATA channel.  The max (burst) rate is 133 MB/s (assuming the most recent ATA standard), but you won't see anything like that on a sustained copy -- it will be closer to 30 MB/s.

[http://www.dewassoc.com/kbase/hard_drives/media_transfer_rates.htm](http://www.dewassoc.com/kbase/hard_drives/media_transfer_rates.htm)

But I have never heard of a TB class PATA drive --  :confused:

Very good call dabl...

31.4 MG/s continuous, 3 copy 'channels' of 650+ GB partitions each - 2 @ 10.5MG/s , 1 @ 10.4MG/s, sustained...

---

