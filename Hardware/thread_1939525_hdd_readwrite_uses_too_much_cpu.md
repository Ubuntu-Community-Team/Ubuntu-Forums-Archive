---
title: "hdd read/write uses too much cpu"
date: 2012-03-11
forum: Hardware
---

### Post by kosme15 on 2012-03-11
I was copying a large directory tree (about 8GB in about 15000 files of various sizes) from one hdd to another (two separate devices, not two partitions on the same device).  I noticed an exuberant cpu load of about 80-90% while the copying was taking place.  I don't think this is normal.  I'm wandering if there is some sort of a kernel module that should offload the hdd operations to the motherboard that isn't loaded properly and so the cpu ends up doing all the work.  Any help with this would be greatly appreciated.

PS: to copy I issued in a terminal:
$ rsync -auvhi /source_path/  /destination_path 

and in a separate terminal I had this running:
$ dstat -cdf

---

### Post by papibe on 2012-03-11
Are both of the drive internal?
Are both ext4 filesystems?

Regards.

---

### Post by kosme15 on 2012-03-11
Yes and yes.

---

### Post by ahallubuntu on 2012-03-11
SATA is controlled by the CPU (to some extent) so it is normal for the CPU to get a load during a copy. That is, there is no dedicated controller for SATA the way there was for SCSI back in the old days.  The main reason: it's cheaper to manufacture a motherboard where the CPU does the work, not some extra component that raises the cost of the board.

The question is, what process(es) show the CPU load?  If the rsync process is taking most of the CPU, that's probably fine and in fact good because it means it is being pretty efficient and probably copying at a decent speed.

Also, what are the CPU specs on the machine you are using?  My guess would be older not newer?

Copying between NTFS partitions can load up the CPU (especially on writes) but that's just overhead because the rsync (in that case) wouldn't be utilizing the CPU.

---

### Post by kosme15 on 2012-03-11
I'll check which process(es) use most cpu and I'll post it tomorrow (I'm using a different pc now).  

The machine is indeed old -- Athlon64 X2 4400+ on MSI K8N Diamond Plus.  I remember back in the old days it made a big difference in the hdd performance in Windows XP whether I installed the NVidia drivers for the nforce4 chipset or not.  Of course there were never any drivers to install in Ubuntu, but this has lead me to believe that a part of i/o is done by the motherboard and the linux kernel knows how to make the chipset do the work, while windows needs a driver to do the same.  So I thought that this part of linux kernel has somehow become mis-configured in my case.

Anyhow, thanks a lot for your interest in my question, I appreciate it.  I'll do some testing tomorrow when I get back to my pc and I'll post the results.

---

### Post by ahallubuntu on 2012-03-11
> **kosme15 said:**
> The machine is indeed old -- Athlon64 X2 4400+ on MSI K8N Diamond Plus.  I remember back in the old days it made a big difference in the hdd performance in Windows XP whether I installed the NVidia drivers for the nforce4 chipset or not.  Of course there were never any drivers to install in Ubuntu, but this has lead me to believe that a part of i/o is done by the motherboard and the linux kernel knows how to make the chipset do the work, while windows needs a driver to do the same.  So I thought that this part of linux kernel has somehow become mis-configured in my case.

You had the right idea.  What was probably happening in XP is that the NVidia drivers allowed XP to use more advanced modes in the hard drive controller and/or the drive itself (DMA modes and such) that would allow it to transfer data more quickly.  XP's built-in driver may have been old and generic and did not know  how to utilize the controller most efficiently.   But that doesn't mean "the motherboard took over" - it just meant the CPU could transfer the data more efficiently with a lot less work.

Today's Linux kernel probably has great drivers for this old hardware (just a guess).  Whether or not this is true should be  judged not by how much CPU is used but by the transfer rates you are getting.  For example, try using Nautilus (the Ubuntu file browser) to drap-and-drop a big amount of data as a test from a folder on one drive to another folder on the other drive and see what kind of transfer rate is reported after about a minute of transfer.

You can also drop into a terminal and try this command to test the read access speed of each drive:

sudo hdparm -t /dev/sda

(repeat for /dev/sdb if you want to check both of your drives).

and see what kind of read speed you get on each drive.  For example, I have a decently fast Hitachi 500GB SATA laptop drive, and I get a read speed of 78.86MB/sec, which I consider quite good for a 3-year old laptop and a 5400RPM drive.  You will probably get a slower rate, maybe closer to 40-50MB/sec on an older drive.  This can depend on the drive too, though.

On the other hand, if you're really getting something awful like 10MB/sec then maybe there is some sort of driver issue.

---

### Post by Helen McCall on 2012-03-17
Worth checking your syslog and dmesg to see if there are any I/O failures.

I experienced a massively over burdened cpu when I had a disk controller failure on my last computer.

---

### Post by kosme15 on 2012-03-17
OKay,  I finally had some time to poke around my old pc.  I did a lot of tests of different things, but for the sake of brevity I will only post the result of the most informative test.

I figured out that rsync, being a remote sync tool, runs two instances, one that sends the files and another to receive them.  Which makes sense since these are meant to run on different machines and communicate with each other over a network.  However, if the source and destination are on the same machine, then rsync still runs two preocesses on then same machine.  This is why I was seeing high cpu usage.  

For comparison I did the same copy using rsync and cp.  Here are the very instructive results: 

```

$ time cp -pr /media/4564eb84-bb0c-4a95-bf2f-7129617b7c3d/home/boyan/code /tmp/ 

real    4m8.129s
user    0m0.944s
sys    0m48.647s

$ time rsync -a /media/4564eb84-bb0c-4a95-bf2f-7129617b7c3d/home/boyan/code /tmp/

real    3m52.900s
user    2m4.600s
sys    2m23.065s

$ du -hs /tmp/code
7.6G    /tmp/code

```

Both cp and rsync take about the same time, as measured on my watch, but they use it very differently.  
Most of the time taken by cp was neither user code (only 0.9s), nor system code (under 50s), which means that around three of the four minutes were just sitting and waiting for the hdd's.  Which also means that three minutes of cpu cycles were available for someone else to use.  
rsync on the onter hand spent over two minutes in user code and just under two and a half minutes in kernel code.  It's interesting that the user+sys is more than real.  How is this possible?  My theory is that the user and sys times are the totals for the two rsync processes, and if they were running on different cores, the time available for someone else would be real-(user+sys)/2 = 1.651125m = 1m39.0675s. (about half of what cp left us)

So, lesson learned: rsync is a great tool for synchronizing two copies of the same directory, but for plain copying cp (or scp if remote) is more efficient.  For some time I have been using 'rsync -a' for all my copying for convenience, because with rsync I don't have to worry if the destination already exists.  I now realize that my convenience was actually costing me quite a lot, so this stops today.

Thanks to everyone for your interest and for your useful suggestions.

---

