---
title: "Slow SCSI reads"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by jfdill_2 on 2006-02-13
I am testing throughput on a Dell PowerEdge 1850 with bonnie++ 1.03 and have observed that block reads are a whole lot slower than block writes.  I am getting similar numbers from both the internal Perc 4e/Si to hardware RAID-1 of 10k Ultra320 disks, and Adaptec 39160 Ultra160 to an external Promise VTrak 15110 running RAID-5 with 450 GB SATA disks.  I capped memory at 256 MB with mem=256m at boot time and am using a 512 MB file size.  Maybe write cacheing is working much better than expected for some reason, and I should try increasing the file size, but reads should still be better than I am observing.

Granted, I expect some performance hit to double writes on RAID-1 and parity on RAID-5, but not a 4:1 ratio.  I will provide additional data as the discussion progresses, but wanted to find out if anyone else has observed similar behavior.  We are trying to make a decision whether to go with Debian Stable with 2.4 kernel (haven't been able to get the 2.6 series kernel to work on Debian with the Perc 4e/Si) or Ubuntu Breezy and the 2.6 series kernel.

Block writes are phenomenal at about 115 MB/s, but block reads are only about 30 MB/s.  With the Debian Stable kernel 2.4 block writes are only about 50 MB/s, but block reads are about 80 MB/s.

I ran about 590 cycles of bonnie++ over the weekend for some "burn-in" testing, so the 115 / 30 speed seems to be fairly average, although I haven't calculated the exact average as yet.  Here is an excerpt from the bonnie++ log:  Edit:  I can't get the bonnie logs to paste in here and be legible :( will have to try something else.

---

### Post by jfdill_2 on 2006-02-13
It looks like I was running off a 386 uniprocessor kernel.  I have run the tests again with the latest linux-image-2.6.12-10-686-smp, using the full 2 GB RAM and 4 GB sampe file, and I am getting about 88 MB/s writes and 81 MB/s reads, which is more like what I had expected.

---

