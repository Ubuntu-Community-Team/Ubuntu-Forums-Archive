---
title: "Intel Matrix RAID5 RAID 5 problem"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by w_boba on 2006-02-15
I have ASUS P5WD2 Premium motherboard with 4x300 SATA drives. I configured all 4 drives as a RAID5 volume on built-in Intel Matrix Storage controller, but when I boot machine from Ubuntu CD, partitioner shows only 4 separate SATA drives. Doesn't matter if I configured RAID or not.

Does anyone managed to install Ubuntu on this motherboard on RAID5 array ? Or any other motherboard with Intel Matrix Storage controller in RAID5 mode ?

PS: I can install WinXP on this RAID5 and it boots up fine with almost 900GB drivespace on one partition.

---

### Post by w_boba on 2006-02-28
I did try "fakeraid" solution, it did not work.

---

### Post by clparker on 2006-02-28
I also Have Matrix Raid; Anybody know if Its gonna be supported in Dapper?

---

### Post by w_boba on 2006-03-21
That is why Microsoft  is better :)

If you ask questions in MS Support, they (at least) give you answer "this is not supported" ot "this will/will not be supported in the future release". But you have feeling, that you are important and someone did see your question.

In this support forum you just being completely ignored.

That is why people buing MS software.

---

### Post by theanorak on 2006-03-22
[http://www.intel.com/support/chipsets/imsm/sb/cs-020663.htm](http://www.intel.com/support/chipsets/imsm/sb/cs-020663.htm)

Raid 5 not supported under linux.

---

### Post by countryboy on 2006-04-06
Ditto that point about nobody every replying to a post - I have posted about 5 problems in the last few weeks with no reply :-k 

Anyway, I have been working on two Dell Precision 380 servers, both with the Intel SATA Raid (which I think is what you are talking about).

I spent about a week trying to get the FakeRAID to work from the HowTO, but without luck. Basically I figured out that the only way is to delete any RAID volumes using the Intel Matrix software and then use uBuntu's soft raid to do the RAID. It works very well, I am able to mirror two 160gig SATA drives and pull them out one at a time without problems.

RAID 5 however is proving a problem as I gather you can't put the /boot partition on a RAID 5 array. However I got around that by creating a 250mb mirrored boot parition across the 3 disks and then a 280gig RAID 5 parition across the three disks for my root parition. Not very elegant but the only way I could get it to work.

So, the gist of this post is that the Intel Raid that you are using (one SATA controller) cannot be used.

---

### Post by w_boba on 2006-07-13
FreeBSD 6.1 has support for this RAID controller built into GENERIC kernel.

---

