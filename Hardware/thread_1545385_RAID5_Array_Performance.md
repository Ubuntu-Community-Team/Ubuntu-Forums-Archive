---
title: "RAID5 Array Performance?"
date: 2010-08-03
forum: Hardware
---

### Post by WinstonChurchill on 2010-08-03
I'm considering setting up a RAID5 array with 3 HDD's in my desktop, both for redundancy and increased read performance. However, I've read in several places that RAID5 is notorious for slow random-write performance. So my questions are:

[LIST=1]
[*]How bad is this write penalty? Would it at least be as fast as the random-write speed for any one of the disks in the array? Is random-write performance much of a concern in a general desktop computer?
[*]Would copying large files be effected? The literature I have seen seems to imply that large linear writes are not nearly as impacted as small random ones.
[*]I have an AMD RAID controller which supports RAID5 integrated into my motherboard (Gigabyte - I can look up the model numbers if that would be of use to anybody) - would this controller perform parity calculations in hardware, or does it use the CPU? My CPU is an x4 3.4Ghz AMD, so if it does use it, how significant would the impact to disk performance and general computer performance be?
[*]If the onboard controller doesn't, how much would I have to pay for a RAID controller that does perform parity calculation in hardware?
[*]Would a RAID10 or RAID01 be a better solution? Obviously RAID5 would be preferable from the standpoint disk capacity efficiency (3 500's make 1TB in RAID5, but you need 4 500's for 1TB in RAID10/01).
[/LIST]

---

### Post by Fafler on 2010-08-04
1. I think you would get pretty close to the performance of a single drive. You have a fast CPU and the SATA drives work independently on their own interface.

2. Probably not. Atleast, you should be able to match the speed of a gigabit ethernet card.

3. It's software RAID. But a modern 3.4 ghz processor can do like a gazillion XOR operations every second. Don't worry. The laptop i'm using now is able to checksum 4224 mb/s on a 1.6 ghz Core Duo.

4. From time to time theres some cheap Adaptec and Dell controllers on eBay. But i still recommend software RAID.

5. Probably. But you'd waste more space and use more energy. That, and you can add drives to your RAID 5 array over time as you need more space.

---

### Post by WinstonChurchill on 2010-08-05
Thanks! I'm definitely going to give this a shot - I'll post hardware details and benchmarks once I get it up and running.

**EDIT: **I've got this up and running - my motherboard FakeRAID controller is terrible, so I went with mdraid in Linux. I get read speeds of around 250 MB/s, and write speeds of about 90 MB/s - the individual drives have average read-write speeds of about 120 MB/s. So, the write speed is a little bit of a penalty, but 90 MB/s is plenty fast - I think it's an acceptable loss for the redundancy and expandability that RAID5 offers. I'm also sure that that write rate would improve dramatically if I were to add a couple drives the the 3 I've got now. 

In short, if you're considering this, go for it.

---

