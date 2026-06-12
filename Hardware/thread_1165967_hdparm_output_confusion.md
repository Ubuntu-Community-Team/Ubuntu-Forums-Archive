---
title: "hdparm output confusion"
date: 2009-05-21
forum: Hardware
---

### Post by dontcarefilmer on 2009-05-21
Hi, I recently got another sata hard drive to help backup my system ready for a fresh install of ubuntu 9.04. The drive worked fine to backup everything, but afterwards it takes a very long time to do anything.

I ran hdparm -Tt and it came out with:

/dev/sda:
 Timing cached reads:   940 MB in  2.00 seconds = 470.00 MB/sec
 Timing buffered disk reads:  222 MB in  3.02 seconds =  73.51 MB/sec

/dev/sdb:
 Timing cached reads:   874 MB in  2.00 seconds = 436.49 MB/sec
 Timing buffered disk reads:  read(2097152) returned 573440 bytes

Why does the second drive give a different type of output for the buffeted disk read, and is this why it is running so slow?

Thanks.

---

### Post by dontcarefilmer on 2009-05-27
Ok, I changed the sata lead to the motherboard and it fixed the speed issue, must have been a faulty cable.

But I still get the same output from hdparm.

Although this issue isn't crippling anymore I would still like to put it to rest, so does anyone have an idea? Anyone at all?

---

