---
title: "Enable ncq"
date: 2006-03-15
forum: Hardware &amp; Laptops
---

### Post by Jimmy_r on 2006-03-15
I just remembered that my harddrive has NCQ, so i checked to see if it is enabled.
After some googling i found this:

[http://www.ussg.iu.edu/hypermail/linux/kernel/0505.3/1379.html]("http://www.ussg.iu.edu/hypermail/linux/kernel/0505.3/1379.html")

> If NCQ is enabled for your drive, it will be printed in dmesg after the lba48 flag, such as:

ata1: dev 0 ATA, max UDMA/133, 488281250 sectors lba48 ncq

If you don't see NCQ there, your drive/controller doesn't support it.
Likewise you will have a queueing depth of > 1 if NCQ is enabled, check
/sys/block/sdX/device/queue_depth to see what the configured queueing
depth is for that device.

the line in my dmesg:
[   15.775687] ata3: dev 0 ATA-6, max UDMA/133, 312581808 sectors: LBA48

no "ncq" there, and  /sys/block/sda/device/queue_depth shows "1".


So, apparently ncq is not enabled. I have a dim memory of enabling and disabling it at will under winXP, so there should not be a hardware problem.

Any advice on how i can get it working?

My motherboard is an Asus A8N-E nForce4 Ultra
The harddrive is a Seagate Barracuda 7200.7 SATA NCQ

Also i am using the 64 bit Dapper Drake

---

### Post by mips on 2006-03-15
Sorry cannot answer your question but what is NCQ ?

---

### Post by Jimmy_r on 2006-03-15
[www.seagate.com/docs/pdf/whitepaper/D2c_tech_paper_intc-stx_sata_ncq.pdf](www.seagate.com/docs/pdf/whitepaper/D2c_tech_paper_intc-stx_sata_ncq.pdf)

> Native Command Queuing (NCQ) is among the advanced and most anticipated features
introduced in the Serial ATA II: Extensions to Serial ATA 1.0 Specification, download available at
[www.serialata.org](www.serialata.org). NCQ is a powerful interface/disc technology designed to increase
performance and endurance by allowing the drive to internally optimize the execution order of
workloads. Intelligent reordering of commands within the drive&#8217;s internal command queue helps
improve performance of queued workloads by minimizing mechanical positioning latencies on the
drive. 

Or in English: It is supposed to go faster :)
Even though in WinXP the opposite was true :(
Disabling it there halved my boot time, i think. I was just curous to test if it worked better under linux.

---

### Post by mips on 2006-03-15
Thx for the explanation, now i know what ncq is ;)

All I can suggest is to keep on searching for a solution unfortunately...

[http://linux-ata.org/software-status.html](http://linux-ata.org/software-status.html)

---

### Post by Jimmy_r on 2006-03-16
Hmm, seems as i would need to patch the kernel with experimental code...
I will probably just wait until Linus is kind enough to get it into his kernel tree :)

---

### Post by Ux64 on 2008-02-23
This thread is now two years old? And no solution yet? I tried to activate NCQ. System show's it's available but it's not being used.

Any new hints?

---

### Post by Yellow Pasque on 2008-02-23
> **Ux64 said:**
> This thread is now two years old? And no solution yet? I tried to activate NCQ. System show's it's available but it's not being used.

Any new hints?
Native Command Queueing works best with server workloads. I have yet to see a test that shows it makes a significant difference for desktop users, except maybe trimming boot times a bit (but there are plenty of other ways to do that). Basically, I only recommend worryiing about NCQ after you've done a lot of other optimization. Only then would it be worth the effort.

---

### Post by Ux64 on 2008-02-29
> **Temüjin said:**
> Native Command Queueing works best with server workloads. I have yet to see a test that shows it makes a significant difference for desktop users, except maybe trimming boot times a bit (but there are plenty of other ways to do that). Basically, I only recommend worryiing about NCQ after you've done a lot of other optimization. Only then would it be worth the effort.

Yep. But NCQ should work out of the box. It's standard feature. And when disk I/O is maxed out, it should help especially if it's maxed out due "random" reads & writes.

I often hear that something is not needed. But if it improves performance, why it's not needed is bit unclear. When you ad 500 x 1% improvement, it's a lot. Even if it's only that 1% that gets improved.

Core optimizations should be done for you. So you don't need to do those by your self.

Just my IMHO.

So getting NCQ working, shouldn't require ANY work. It just should work, that's it. Most of hardware supports NCQ today.

Slowest part of my system is currently disk i/o, so any help to it is appreciated.  And even in single user environment in that case I think that NCQ should provide help. I'm using browser, when using torrent and while extarcting huge rar archive. In that case I see that NCQ should help. And disk i/o is worst bottle neck on my system anyway. (And it has been on other systems earlier) plenty of memory and cpu power, but disk i/o is slow.

---

### Post by Yellow Pasque on 2008-02-29
> So getting NCQ working, shouldn't require ANY work. It just should work, that's it. Most of hardware supports NCQ today.
Well, that's the idealistic take on it. If you want practical advice, read the post above yours. :P

---

### Post by Ux64 on 2008-03-10
> **Temüjin said:**
> Well, that's the idealistic take on it. If you want practical advice, read the post above yours. :P

If it's working on your system. How did you enable it, where's the switch?

And if it does, did you run any benchmarks? Very simple test operation.

First disable ncq.

Copy three files in parallel.

Then enable ncq.

and repeat test.

There you have it. If there is any improvement like 10%. Then it' clearly helps. 

- Thanks!

I hate when people claim something without any facts. I think Linux community should follow scientific and academic standards. ;) I didn't see any proper research about topic why defrag isn't needed. Just claims without any real facts.

This thread: [http://ubuntuforums.org/showthread.php?t=383100](http://ubuntuforums.org/showthread.php?t=383100)

Unfortunately because proper defrag program isn't available,  I could do tests my self. Anyway, it would be too small sample for any proof. But it could give some clue anyway. Just like the simple test described above.

---

### Post by Ux64 on 2008-03-25
How much NCQ can help...

Read this: [http://www.storagereview.com/500.sr?page=0%2C6](http://www.storagereview.com/500.sr?page=0%2C6)

- Thank you!

---

### Post by Yellow Pasque on 2008-03-25
> **Ux64 said:**
> How much NCQ can help...

Read this: [http://www.storagereview.com/500.sr?page=0%2C6](http://www.storagereview.com/500.sr?page=0%2C6)

- Thank you!

:confused: Are you trying to make a case for NCQ on the desktop? If so, I suggest working on reading comprehension. The only place where it showed noticeable improvement was with file server workloads. The NCQ actually showed negligible gain and more often decreased I/O's per second (esp. with the WD drive) in all of the other tests. Also note that the drives being tested are **Enterprise** drives

---

