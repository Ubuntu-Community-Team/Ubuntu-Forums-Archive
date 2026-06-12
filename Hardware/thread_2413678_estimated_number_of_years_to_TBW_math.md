---
title: "estimated number of years to TBW math"
date: 2019-02-28
forum: Hardware
---

### Post by bjlockie on 2019-02-28
My nvme drive has a warranty of 100TBW.
If I divide "Data Units Written:" by "Power On Hours:" I get the average written per hour.
If I divide 100 000 (100TB) that by 24 by 365 I get the number of years to get to 100TBW.
Right?
This is strictly the time to TBW, what things fail because of age?

$ sudo smartctl -a /dev/nvme0n1 | grep 'Data Units Written:\|Power On Hours:'

---

### Post by TheFu on 2019-03-02
Is this an Ubuntu question?

Time has nothing to do with the actual lifespan for SSDs.  Lifespan is about the capability of having storage cells that haven't failed. Once a cell fails, it is done, never to be used again.  If you want to make an SSD last longer, don't fully use it. Leave 20% unallocated.  

You can also to some research about QLC, TLC, MLC and SLC storage for how each, generally, impacts lifespan.

You've probably already seen these articles:
* [https://blog.westerndigital.com/ssd-endurance-speeds-feeds-needs/](https://blog.westerndigital.com/ssd-endurance-speeds-feeds-needs/)
* [https://forums.tomshardware.com/threads/endurance-of-sata-ssds-and-how-long-they-usually-last.3397579/](https://forums.tomshardware.com/threads/endurance-of-sata-ssds-and-how-long-they-usually-last.3397579/)

Don't get hung up on time, it is all about writes.

---

### Post by Impavidus on 2019-03-03
The question is to get an estimate of the time before end of warranty, based on the amount of data written per unit of time.

Logically, it's:
(estimated time for reaching end of warranty in years)=(100000 GB write warranty)*(power on hours)/(365*(data units written)*(power on hours per day))
assuming the data units written are in GB and are counted correctly. Writing a single byte may mean writing an entire block, which may be what's meant by a data unit. These devices can't reset a single byte at a time.

It may still be a somewhat crude estimate, as data usage patterns may slowly change.

---

### Post by oldos2er on 2019-03-03
Moved to Hardware.

---

### Post by bjlockie on 2019-03-04
> **TheFu said:**
> Is this an Ubuntu question?

Time has nothing to do with the actual lifespan for SSDs.  Lifespan is about the capability of having storage cells that haven't failed. Once a cell fails, it is done, never to be used again.  If you want to make an SSD last longer, don't fully use it. Leave 20% unallocated.  

You can also to some research about QLC, TLC, MLC and SLC storage for how each, generally, impacts lifespan.

You've probably already seen these articles:
* [https://blog.westerndigital.com/ssd-endurance-speeds-feeds-needs/](https://blog.westerndigital.com/ssd-endurance-speeds-feeds-needs/)
* [https://forums.tomshardware.com/threads/endurance-of-sata-ssds-and-how-long-they-usually-last.3397579/](https://forums.tomshardware.com/threads/endurance-of-sata-ssds-and-how-long-they-usually-last.3397579/)

Don't get hung up on time, it is all about writes.

I want a rough estimate of how many years at average current write usage average have left.

---

### Post by bjlockie on 2019-03-04
> **Impavidus said:**
> The question is to get an estimate of the time before end of warranty, based on the amount of data written per unit of time.

Logically, it's:
(estimated time for reaching end of warranty in years)=(100000 GB write warranty)*(power on hours)/(365*(data units written)*(power on hours per day))
assuming the data units written are in GB and are counted correctly. Writing a single byte may mean writing an entire block, which may be what's meant by a data unit. These devices can't reset a single byte at a time.

It may still be a somewhat crude estimate, as data usage patterns may slowly change.

I don't see power on hours per day in the smart data.

---

### Post by TheFu on 2019-03-04
Appears that the drive capacity is necessary and not provided.

From the first link - wd blog - they provide the formulas.
> 
SSD write endurance is Terabytes Written (TBW), which describes how much data can be written to the SSD over the life of the drive.
Drive Writes Per Day (DWPD).

Converting between TBW and DWPD is simple:

DWPD to TBW:  TBW = Capacity(TB) * DWPD * 365 * Warranty(Years)

TBW to DWPD:  DWPD = TBW / (365 * Warranty(Years) * Capacity(TB) )

So, use the 2nd formula and compare that with the SMART data after you convert it to DWPD. Just be consistent with the units.  Always use TB, for example.  And realize that these are statistical estimates.  Some drives will last a little longer and some will last a little shorter.  The environment matters too - is it hot or cold? Does the machine have vibrations or get bumped?

---

### Post by oldfred on 2019-03-04
Some life tests:
       [http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb)

---

### Post by bjlockie on 2019-03-05
> **TheFu said:**
> Appears that the drive capacity is necessary and not provided.

From the first link - wd blog - they provide the formulas.


So, use the 2nd formula and compare that with the SMART data after you convert it to DWPD. Just be consistent with the units.  Always use TB, for example.  And realize that these are statistical estimates.  Some drives will last a little longer and some will last a little shorter.  The environment matters too - is it hot or cold? Does the machine have vibrations or get bumped?

Can I assume it'll last longer than the warranty period if the DPWD is less than the max and some days have significantly more writes than other days?

---

