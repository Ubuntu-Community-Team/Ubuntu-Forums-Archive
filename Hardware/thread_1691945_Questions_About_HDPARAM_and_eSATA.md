---
title: "Questions About HDPARAM and eSATA"
date: 2011-02-20
forum: Hardware
---

### Post by partyk1d24 on 2011-02-20
Hey everyone, 

I know this is kind of similar to a couple other posts but something just isn't clicking. So I just bought an eSATA drive to store my virtual images on. While copying them I noticed it was going to take like 12 minutes. I thought this was strange since I was supposed to be getting 3.0 Gbps. 

I looked online and ran this...

/dev/sdb1:
 Timing cached reads:   6492 MB in  2.00 seconds = 3246.88 MB/sec
 Timing buffered disk reads:  254 MB in  3.01 seconds =  84.36 MB/sec


What is the difference between buffered and cached. Also, does that buffered read look right? Shouldn't it be higher?

Thanks Guys!

---

### Post by fjgaude on 2011-02-20
The cache reads are an indication of the speed of your CPU and SDRAM. The buffered read is the sequential reads from your hard drive.

Your drive speed is likely that of drives a generation or two back. <sigh>

---

### Post by partyk1d24 on 2011-02-20
What does that mean "drives a generation or two back."? I just bought it today, it was a samsung. So I am not imagining this it IS running supper slow? I am using an eSATA drive and there have been some posts about that being an issue with x64.

Any idea how I can speed it up? It seemed to work fine when I booted up under Windows.

Thanks

---

### Post by fjgaude on 2011-02-20
Well, just because you just bought it doesn't mean it is the latest and fastest yet of the hard drives. The vendors have to get rid of all the over-production of drives one way or another.

Were you able to test the drive speed under Windows?

---

