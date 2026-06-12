---
title: "Best SSD for multiple virtual machines? [solved]"
date: 2019-07-12
forum: Hardware
---

### Post by bunny9000 on 2019-07-12
Found an answer.

---

### Post by TheFu on 2019-07-12
And what is the answer?  I'm curious.  Help out the community.

I've bought an SSD - a Micron 1100 - for storage of my LVs containing VMs.  For me, it was a trade off between the SSD I wanted, but couldn't afford and the lower-end SSDs which I didn't want to touch after having 2 cheapo SSDs fail years before expected.  I have a **Samsung SSD 860** in a laptop that was a great deal at the time for a few days.  The price of that model went back up when I needed an SSD for a new VM server build.  I really wanted a 970 NVMe, but after waiting about 2 months for the price to drop, which never happened, the Micron 1100 was a deal.  It isn't the same, but hopefully it is close enough.

---

### Post by nought2 on 2019-07-12
Not sure if this counts.

Very recently I commissioned a new machine. Boot drive is Samsung 970 EVO Plus M.2 NVMe SSD.

Performance is nothing less than sensational. 

Ubuntu and W10 boot up in seconds. At a guess, less than 10sec.

Backup images of this M.2 drive saved to USB 3.0 external HDD complete in 5-10min. I have seen reports of backup images saved from the same Samsung NVMe M.2 drive to an identical partner complete in 5sec.

It is a new world of computing.

---

### Post by bunny9000 on 2019-07-14
Hi all.

So the conclusion to the aborted question.

I found a video online that covered most of the current brand name SSDs. The samsung evos come out pretty much on top most of the time with other 3d nand SSDs not far behind. Other drives like the lower end kingstons have similar read, but loose out on write performance . I'm still not going to touch unknown brand SSDs and then some have good burst performance.

Since I run a few vms I needed an SSD with good write performance.

The other issue I had was the limitation of my spinning drives to run more than one or two vms. But this really depends on the OS and if the drive has to do anything else. A couple of windows server OS vs 3 to four linux os - I expect you could increase performance by running two spinners in raid 0. 

I also managed to dig out another spinner so I can run roughly 3 vms on each spinner and four on the SSD. My pc has a maxium RAM of 16GB so I'm limited by that.

I have a samsung SSD as my boot drive and I have enough space to run four vms on it so overall for the work I'm doing I have enough drives to run the number of vms I require. 

I expect with enough space my four core cpu could handle five to seven VMS before over saturating an SSD with enough space, but potentially be into CPU bottleneck and soon after RAM bottleneck.

The 3D nand SSDs are in a fairly similar ball park with price. The cheaper drives use less advanced tech and are cheaper. For most users running the OS and web browsers that's not a problem. I was, initially under the illusion samsung drives were more expensive because they had the known brand and while they are, other companies are catching up and drives from five years are slower than what's on offer now.

To me, SSD buying for more server grade and professional use is a little more tricky while on a home users budget - you know - $0. Most SSDs will out perform a spinner, but you have to be careful. It appears that if you want a fast SSD at the moment you have to pay the higher cost. There isn't a secret cheap SSD that's the fastest thing in the world and has reliability. 

So - I'm saving for a 500GB SSD so I can retire one of my spinners.

Hope that helps someone a tiny bit.

---

### Post by Dennis N on 2019-07-14
Older to newer technology:
SLC > MLC > TLC > QLC
newer technology = cheaper to make but has fewer P/E cycles.
in general, larger drives last longer (higher TBW).
some unallocated free space extends life span.

If all running, how would you allocate more than 3 vm + host to 4 cores?

---

### Post by TheFu on 2019-07-14
Thanks for the explanation. It would also help if you used the "**thread tools**" button near the top to mark this thread as solved.

I would caution against using RAID0 with any spinning disks or with cheap SSDs.  Failures still happen often enough with these that total data loss across all the disks in the RAID is too likely.  However, running a few quality enterprise-grade SSDs in RAID0 is something businesses are doing for performance.  Of course, RAID never substitutes for backups.

SSD price relates to a few things.  Mainly the SSD storage technology used which directly impacts the durability for the device.  QLC, TLC, MLC, SLC are from cheapest to most expensive solutions.

I've run over 20 VMs on a 1st generation Core i5 quad core "VM Server" concurrently on RAID5 disks. It is common for people to over allocate RAM, disk, and CPU to VMs when it isn't necessary.  Just because your desktop runs nicer on 4G of RAM, doesn't mean that most servers need that.  None of my VMs get more than 2 vCPUs.  Most get only 1 vCPU and less than 1GB of RAM allocated, a few only get 384MB of RAM.   I tune my server VMs so that no swap partition is needed, so the RAM provided is actually what is needed to perform the server tasks.

---

