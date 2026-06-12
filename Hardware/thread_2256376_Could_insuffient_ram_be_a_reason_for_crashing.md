---
title: "Could insuffient ram be a reason for crashing?"
date: 2014-12-11
forum: Hardware
---

### Post by kccv42 on 2014-12-11
I have 2gb of ram running on my laptop. Does it need more to stop crashing as frequently?

---

### Post by papibe on 2014-12-11
Hi kccv42.

It could, but you also would have to:
[LIST]
[*]have a very small, or not all, swap partition, and
[*]run enough programs simultaneously so that the system reject new programs being launch, or halt all together.
[/LIST]
In order to diagnose the reason, I'd start checking the following logs:
[LIST]
[*]/var/log/dmesg
[*]/var/log/kern.log
[*]/var/log/syslog
[/LIST]
Hope it helps. Let us know if you need more help finding out why your system crashes.
Regards.

---

### Post by sammiev on 2014-12-11
You leave no specs of your computer or what version and flavor of Ubuntu you are running.

---

### Post by Reha_Andrew on 2014-12-12
Yes it could be because sometimes router becomes slow. I suppose you have not used heavy p2p application.

---

### Post by Yellow Pasque on 2014-12-12
Give output of free command:
```
free -m
```

Memtest is your friend. If I suspected corrupt RAM, I think I'd run that before digging into OS logs.

---

### Post by mörgæs on 2014-12-12
Limited RAM could make a system run slow or (in extreme cases) freeze, but not crash.

Agree, **memtest** is worth trying. Also please post the output from ```
sudo lshw -short -C memory
``` in CODE tags.

---

### Post by kccv42 on 2014-12-12
Here is the information you all requested. To papibe, all the commands you gave me said permission denied.

```
computer4@computer4:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1744       1640        104         16         44        668
-/+ buffers/cache:        927        817
Swap:         1784          0       1784
```

-------------------------------------------------------------------------------------------
PCI (sysfs)  

```
H/W path        Device      Class       Description
===================================================
/0/0                        memory      1MiB BIOS
/0/b/c                      memory      128KiB L1 cache
/0/b/d                      memory      512KiB L2 cache
/0/e                        memory      2GiB System Memory
/0/e/0                      memory      1GiB SODIMM DDR3 Synchronous 1066 MHz (0
/0/e/1                      memory      1GiB SODIMM DDR3 Synchronous 1066 MHz (0
```

---

### Post by sammiev on 2014-12-12
What OS are you running? You do have a memory problem.
Lubuntu may serve you better.
What programs are you running and how many open windows do you have at one time?
I would love to see the output of "top".

---

### Post by Yellow Pasque on 2014-12-12
> **sammiev said:**
> You do have a memory problem.

Be more specific. It's a laptop, so it's probably reserving 256MB of RAM for integrated graphics (so it reports about ~1.75GB total as expected). In the "free" output the OP gave, about half the RAM is still available and there is a ~2GB swap partition available that hasn't even been used yet. There is no problem with that output AFAICT.

> To papibe, all the commands you gave me said permission denied.
They're files, not commands. You view them in a text editor, for example:
```
gksu gedit /var/log/kern.log
```

---

### Post by kccv42 on 2014-12-12
I am running ubuntu 14.04 LTS.

---

### Post by buzzingrobot on 2014-12-12
> **kccv42 said:**
> I have 2gb of ram running on my laptop. Does it need more to stop crashing as frequently?

What do you mean by "crash"?  What, specifically, is happening?  Is the same thing happening at every "crash"? Is it triggered by a specific action?  Can you deliberately create a "crash"?

While two gigs of RAM is a small allotment, you have a swap partition, which will substitute physical disk space for RAM when something makes a request for memory that cannot be filled from RAM. To simplify, if 100 megs of RAM are free and a process requests 150 megs of memory, enough information will be swapped out from RAM to the swap partition on the drive so the memory request can be allocated. Then, when the 150 megs on the drive are needed, they'll be read back into RAM, with some other bits swapped out if more room is needed. 

It is possible, in certain circumstances, to overload the swap partition to the extent that the system spends all of its time managing the swap process. That might appear as a "crash" because the machine can't seem to get anything else done.

What's the typical application mix you launch?  Do you load a number of very large files?

---

