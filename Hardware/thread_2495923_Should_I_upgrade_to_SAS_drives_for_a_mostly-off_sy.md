---
title: "Should I upgrade to SAS drives for a mostly-off system?"
date: 2024-03-07
forum: Hardware
---

### Post by papriak on 2024-03-07
I want to upgrade my "backup server" to a platform that supports ECC memory, and possibly swap out the SATA drives for SAS ones while I'm at it.

The system is typically booted once a week to upload backups from other computers, then shut down afterward.

Should I stick with SATA drives, or might SAS provide any benefits despite accumulating spin-up/spin-down counts?

---

### Post by TheFu on 2024-03-08
What's the problem?  I wouldn't put any money into a system that doesn't have issues.

---

### Post by papriak on 2024-03-08
> **TheFu said:**
> What's the problem?  I wouldn't put any money into a system that doesn't have issues.

The potential problem is memory errors.  I want to upgrade to ECC, and I hear SAS drives have better features than SATA ones.

---

### Post by TheFu on 2024-03-08
> **papriak said:**
> The potential problem is memory errors.  I want to upgrade to ECC, and I hear SAS drives have better features than SATA ones.

There are billions of PCs in the world not use SAS or ECC.  
How many of them have memory errors?  
Do you system manage financial transactions worth billions?  
Is the data required by law to be error free for huge fines?

Most desktop computers don't support ECC, even if they have slots that will accept the RAM.  You'll need a server board for that, which usually means replacing everything.

If you want the most cost effective way to ensure data isn't corrupted, you have 2 choices.
[LIST]
[*]Use ZFS.  ZFS is the only file system that validates what was sent to storage was actually written.
[*]After the data is written, use 10% par2 files to ensure if it ever does become corrupted, you'll be able to know about it.
[/LIST]
Both of those things are free and ZFS is a good idea for data with ECC and SAS.  For my money, rather than SAS, I'd go with NVMe storage for the most critical.  Failure rates for NVMe is much less.  For backup storage, you'll need 2 really bad days to have any data loss.  Do you already have the backups stored 500miles away from the source?  THAT would be more important than SAS or NVMe, IMHO.   

BTW, I worked in disaster recovery planning, testing for about a decade.  Spend your money and effort where it matters most.
Do your current DR solutions meet the RTO and RPO required?  Those are the first questions.  Do you already meed the uptime requirements for the systems?  A single server cannot be guaranteed to provide more than 96% uptime.  That's a much greater risk than SAS vs SATA.

---

### Post by papriak on 2024-03-08
This is a personal home backup server that already uses ZFS, but I'm paranoid of glitches.  :P

Back to my original question:  Given that the system will be turned off most of the time, is it worth having the advantages of SAS drives, or should I stick with SATA?

---

### Post by TheFu on 2024-03-08
No.  Thought I was pretty clear about that.

---

### Post by papriak on 2024-03-08
You advised using NVME drives, and I'm grateful for that advice. (And I do use one for my server's boot drive.)

However, I'd like the storage pool to be at least 20TB in RAID-Z3.  That would be way out of my budget if I used SSDs.

---

### Post by him610 on 2024-03-08
I was not familiar with "SAS drives" so I looked it up....
> SAS stands for Serial Attached SCSI, which is a technology used to transfer data between hard drives. SAS drives are designed for enterprise-level storage systems that require fast data transfer rates, high I/O (input/output) operations, and continuous operation. SAS drives are faster and more reliable than SATA-based hard drives, but SATA drives have a much larger storage capacity. 

Sounds a lot like the old discussion of IDE vs SCSI drives. IDE drives for everyday people with PCs; SCSI drives for corporations with big iron.
I built a SCSI system about 20+ years ago from mostly castoff parts just to see how SCSI drives worked; the last drive had to be a terminator.

---

### Post by him610 on 2024-03-08
@papriak
Here are three things you might consider....
Develop a risk assessment plan.
Develop a risk mitigation plan
Develop a value-engineering plan.
Objective: Most value for your money - the numbers will tell you.

---

### Post by TheFu on 2024-03-08
> **him610 said:**
> I was not familiar with "SAS drives" so I looked it up....

Sounds a lot like the old discussion of IDE vs SCSI drives. IDE drives for everyday people with PCs; SCSI drives for corporations with big iron.
I built a SCSI system about 20+ years ago from mostly castoff parts just to see how SCSI drives worked; the last drive had to be a terminator.

Yep, but SAS are all "enterprise" by definition.  We can get enterprise HDDs, which are made to handle lots of cycles, vibrations from racks that are opened/closed hard, and some higher heating.

SCSI vs IDE was was clearer, since it was measurable for people actually doing work on their workstations.  I know.  I was a software development lead with 20 people at the time.  One of our workstations was shipped with a SCSI adapter and drive.  From an empty directory system, he could build all our software in 25 minutes whereas everyone else with IDE was taking 50+ minutes.  Ever wondered why software development places had ping-pong tables and other "game" setups?  It was because people were waiting for compiles and links to finish.  Doing just a link was over 15 minutes, assuming everything but 1 file remained the same.  SCSI make 20 developers gain 4+ hrs every day.  My boss believed it and spend $500 per developer workstation for upgrades.

With SAS and backups, that's much less the situation, especially if a smart backup method is being used.  The OP never mentioned 20TB nor how he does backups. He never complained about heat, performance, or anything else that is measurable.   *Seems like he just wants to spend money.* Nothing wrong with that, but don't ask "do I need" questions.  

SAS does matter inside data centers.  If you want SAS-like, buy WD Gold HDDs or some other "enterprise" HDD. Those come in SATA versions.  I have some for my heavy workloads, but I'd never use them for backup storage at home.  They aren't cost effective for that purpose.

RAIDz3?  That's overkill too, IMHO.

Moving on to ECC RAM.  If the motherboard and CPU actually support ECC, not just the sockets fit, but they will truly make use of it, then the cause could be made for that upgrade much more than SATA vs SAS.  ECC RAM is costly compared to non-ECC RAM.   We can all thank Intel for that.  Intel decided not to make all their desktop motherboards ECC capable, so the ECC RAM has always been priced like other server components since it doesn't have 2B people buying it.  Had Intel made ECC RAM support standard, we'd all be better protected for $5 more per stick and $5 more per MB.

Be careful with AMD ECC claims.  It is mostly limited to "PRO" CPUs, which come in pre-built systems.  People upgrading their systems at home can't get those directly 90% of the time..

---

### Post by papriak on 2024-03-08
I suppose I could have been more specific at the beginning, sorry.

You're correct that my current setup "works" without any issues, but I found that I can upgrade it to a DDR4 Supermicro X10SRH-CF board with a Xeon CPU, 32GB ECC RAM, and an integrated SAS controller for about $100.  That seems like a good price for more peace of mind.



My current plan is to flash the SAS controller to IT mode for the 8 drives in RAIDZ3, though I don't know whether actual SAS drives would be much of an upgrade over my current SATA ones.

---

### Post by TheFu on 2024-03-09
And you think a 10+ yr old motherboard and CPU are "upgrades?"

---

### Post by papriak on 2024-03-09
> **TheFu said:**
> And you think a 10+ yr old motherboard and CPU are "upgrades?"

My server's current motherboard is an Asus Z97-A, also released 10 years ago.  :P

---

### Post by TheFu on 2024-03-09
> **papriak said:**
> "Life's too short to use slow computers"  

And yet .... 10 yr old equipment is nothing like a new $90 Ryzen 5600 with nearly 21.5K passmarks.  
[https://www.cpubenchmark.net/cpu.php?cpu=AMD+Ryzen+5+5600&id=4811](https://www.cpubenchmark.net/cpu.php?cpu=AMD+Ryzen+5+5600&id=4811)
Saw that price on Amazon a few days ago for that CPU.

You are going to do what you want to do. Good luck.

---

### Post by MAFoElffen on 2024-03-10
He is using ZFS RAIDZ3 Arrays...

I answered this in your other thread, which aligns with TheFu's discussion on this, at least for the push for digital storage and what SAS once was.

As for ECC memory... I used to use ECC for my servers. Speeds are not as fast, and the gains are not as cost effective as it once was.

For my personal servers, with my experience, you can guess that I think about things before I do something stupid. For my servers, I started shifting from ECC memory to, server boards that supported regular memory, then used "gaming memory" in them. I did this first with a Supermicro H8DG6-F dual AMD Optiron 16-core 6284 SE's, with DDR3 16GB Gaming RAM sticks. With ECC registered memory, it would support 32GB sticks... But not with non-EEC memory (less).

All my tests and benchmarks were great. I upgraded from that after many years. Being a server board, it took forever to boot, because of all the redundant server checks and tests. It only booted as Legacy. Being dual 16-core proc, I had 32-cores, but the processor speed was only 2.7 GHz/3.4 GHz.

Now I go with gaming boards with high end CPU's, and gaming RAM.

---

### Post by papriak on 2024-03-10
I'm not looking for this server to be screaming fast, merely fast enough to store large files reliably over my ~1GB/s network.

Considering that the slowest part of the transfers will probably be that network, I'm guessing the rest of the hardware should be able to keep up.

The motherboard I found supports a 3.5GHz (base speed) Xeon CPU with 8 threads, and 2400Mhz ECC RAM.

---

### Post by MAFoElffen on 2024-03-10
For my old home server farm, for backups, I used a fiber network that was isolated from everything else, so nothing was effected by my backups, and that was not a limiting factor there.

Progress has happened since then. You can now do the same with an isolated 10G-Base-T Ethernet network for your backups.

I see a pattern where most of your priority is in benchmarks of file transfers.... That is what we got into when we were tuning your ZFS RAIDZ Arrays.

In that we tuned the arrays... But ran into your limiting factor as your old motherboard's PCIe Gen Speed, then the 20TB HDD drive r/w speed capabilities. Up'ing the hardware base foundation (CPU, PCIe bus, RAM, and such)... Just upgrading the foundation those drives are on, should up your benchmarks a little bit. Upgrading the drives, and doing RAIDZ. You are going to push those speeds even faster. Somewhere there... Then you are going to start getting/pushing into network throughput factors somewhere in that equation. 

Just an idea on that.

---

