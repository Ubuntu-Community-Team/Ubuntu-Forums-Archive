---
title: "Very slow speeds (185MB/s) when copying from one internal NVME to another"
date: 2024-11-18
forum: Hardware
---

### Post by shorthaul on 2024-11-18
[COLOR=#000000][FONT=Arial]I am seeing incredibly slow speeds when copying from one internal NVME to another internal NVME. I am getting ~185 MB/s instead of an expected 1,000 to 3,500 MB/s, a very significant difference.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]_**[COLOR=#000000][FONT=Arial]System specs:[/FONT][/COLOR]**_[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Ubuntu 24.04.1[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]MB: Asus Proart X670E-Creator (PCIe Gen5) - latest available BIOS[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]CPU: Ryzen 7700X[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Memory: 32GB[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]I have a video card in the x16  slot, no other PCIE slots used[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]NVME 1: Crucial P3 4TB Gen3 (~3,500 MB/s read speeds) - firmware updated[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]NVME 2: WD Black 8TB SN850X Gen4 (~6,600 MB/s write speeds) - firmware updated[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Both NVME drives are formatted with EXT4 and SMART looks normal for both. I am trying to copy a large _**3.5TB**_ file from NVME 1 to NVME 2 by dragging and dropping the file in Nautilus. Speeds start out at 330 MB/s (instead of an expected ~3,500 MB/s) for a couple of minutes, then it drops to about 185 MB/s and continues at that speed. After the cache on the drive fills it should be able to maintain a solid 1,000 MB/s, about 5 times faster than what I am getting. [/FONT][/COLOR][COLOR=#000000][FONT=Arial]A review of this drive from Toms Hardware shows that after the cache fills the drive should be able to maintain write speeds of ~1,000 MB/s:



[/FONT][/COLOR][IMG]https://cdn.mos.cms.futurecdn.net/Ud2kjRNas99TNbW5Uez4wK-970-80.png.webp[/IMG]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]




The board has 2 NVME slots off of the CPU and 2 from the chipset. The Crucial NVME is in one of the slots from the CPU. I&#8217;ve tried putting the WD NVME in the other slots but it didn&#8217;t make a difference in the speeds.[/FONT][/COLOR][COLOR=#000000][FONT=Arial] Any thoughts as why the copy speed is so slow?
[/FONT][/COLOR]

---

### Post by him610 on 2024-11-18
> Any thoughts as why the copy speed is so slow?
IMOH, the buffers fill up.
A user in real world will never see speeds as fast as controlled lab-type tests.

---

### Post by TheFu on 2024-11-18
I'd look at the motherboard architecture and settings.  Sometimes where a GPU is placed or how other HDD SATA/port settings are set can take away from other parts of a shared bus.  In Asus MB manuals, I've seen have 2 tables which spell out the complexities of the bus setups.

---

### Post by 1fallen on 2024-11-18
> **him610 said:**
> 
A user in real world will never see speeds as fast as controlled lab-type tests.
Very true.

@shorthaul, is there a reason you choose ext4?

If speed is a big factor, maybe read about BTRFS or better yet ZFS.

Also Drag and Drop, isn't in my habits, I mean nothing wrong with it but there are better ways.
1.The old "cp" average so so.
2. "rsync" is one part of my go to's

And Hardware is Key.

---

### Post by TheFu on 2024-11-18
> **1fallen said:**
>  
Also Drag and Drop, isn't in my habits, I mean nothing wrong with it but there are better ways.
1.The old "cp" average so so.
2. "rsync" is one part of my go to's

The more GUI stuff there is in the middle, the more likely things seem to slow down.  

Definitely run tests using **cp** with the **time** and known file size so that MBps can be calculated over the entire transfer.  **rsync** can do this too - just add *--stats* to the options (I think that's the option).

I'm not a fan of BTRFS and ZFS has some overhead, but I haven't tested performance with them.  COW file systems should be faster for reads, but I can't see how writes would be any different.  I'd be more likely to switch to XFS for data, not booting!!!!, than use BTRFS.  ZFS for huge amounts of data can make sense too, but I'd need 6 HDDs before I considered it and a good way to backup all that data.

If 1fallen has some real-world data, that could be helpful.  Whenever phoronix.com does performance comparisons between file systems, ext4 is respectable and for large disks, xfs has a slight lead.  The reasons to use btrfs and zfs are not for performance. It is for the other things those volume managers+file systems provide.  As always, specific workloads matter. [https://www.phoronix.com/review/ubuntu1910-ext4-zfs](https://www.phoronix.com/review/ubuntu1910-ext4-zfs)
And BTRFS lags according to this: [https://www.phoronix.com/review/linux-611-filesystems](https://www.phoronix.com/review/linux-611-filesystems)

---

### Post by shorthaul on 2024-11-18
> **him610 said:**
> IMOH, the buffers fill up.
A user in real world will never see speeds as fast as controlled lab-type tests.

Before the cache on the drive filled up I was seeing 300 MB/s, about 10 times slower than it should. There may be some difference b/w 'lab' and 'real world', but not 10 times difference. Something else has to be going on. 


> **TheFu said:**
> I'd look at the motherboard architecture and settings.  Sometimes where a GPU is placed or how other HDD SATA/port settings are set can take away from other parts of a shared bus.  In Asus MB manuals, I've seen have 2 tables which spell out the complexities of the bus setups.

There is only one of the four NVME slots that share bandwidth with one of the PCIe slots, and that's only if there is a device in the PCIe slot. I am not using that slot and don't have a device in that PCIe slot either, so it isn't that.

> **1fallen said:**
> Very true.

@shorthaul, is there a reason you choose ext4?


Not really, it's how the drive I'm reading from is formatted and was the default, so just went with that. Would ext4 cause a 10x drop in expected performance? 

Once the current file copy finishes I will try using dd and bypass the file system cache and see if that makes a difference.

---

### Post by shorthaul on 2024-11-18
I tested using dd to bypass the file system cache but I'm still getting very slow speeds, even from the very start of the copy process when the cache isn't full. I used this command and it still was around 185 MB/s transfer speeds.

dd if=/path/to/source of=/path/to/destination bs=128M count=4000 oflag=direct status=progress

---

### Post by brcisna-u on 2024-11-18
@shorthaul

Is the second drive like a storage tank for your setup,or are the two drives  Ubuntu used ?
If second drive is a  storage tank what happens if you take that drive out,, then do a benchmark on your system drive?
I always just use the gnome-disks utility and do a benchmark from there,just because it is convenient and you are comparing apples to apples each time you run it. 
If your performance goes up to about 2Gbps with system drive only,, swap that drive to the opposite slot and repeat.

---

### Post by 1fallen on 2024-11-19
I'll start this with just basics, I'll copy a file un-compressed and the size is "6.1 GiB (6,506,741,844)1,105 files, 136 sub-folders"
That took:
```
 0:03:28 [21.7MiB/s] [==============================================================>] 100%            
```
Now I'll compress that same folder and now:
```
[FONT=monospace][COLOR=#000000] pv '/home/me/Downloads/1.All-DL'\''s.tar.gz'  > /media/me/WD-Blue-1TB/Downloads [/COLOR]
 643MiB 0:00:13 [47.1MiB/s] [==============================================================>] 100%      
[/FONT] 
```

The destination drive is ext4, the source drive is BTRFS with /home compressed ie:
```
less /etc/fstab|grep /home
UUID=3213b2e0-07ed-4f08-b6a6-d1f0fdc83db4 /home          btrfs   subvol=/@home,defaults,compress-force=zstd:3 0 2

```

On my Tank Drive with ZFS is way faster:
```
[FONT=monospace][COLOR=#000000]# pv '/home/me/Downloads/1.All-DL'\''s.tar.gz'  > /tank/speedtest [/COLOR]
 643MiB 0:00:00 [1.86GiB/s] [==============================================================>] 100%  

``` 
[/FONT]```
[FONT=monospace][COLOR=#000000]# df -T /tank [/COLOR]
Filesystem     Type 1K-blocks     Used Available Use% Mounted on 
tank           zfs  939123328 71617536 867505792   8% /tank



```[/FONT]
That should help, I think anyway. :)

---

### Post by TheFu on 2024-11-19
Exact commands would be useful, I bet.
Mixing so many different types of storage muddies the waters massively too.

Best to keep it simple.
1. Simplify the environment.
2. Isolate the different parts with separate tests.
3. Determine the slowest part, then .... 
4. Repeat.

```
dd if=/path/to/source of=/path/to/destination bs=128M count=4000 oflag=direct status=progress
```
That blocksize is huge.  Try either 4K or 4M.  Larger block sizes can keep other tasks out.  Larger isn't always better. Especially for I/O tasks.  Too small is bad too.

---

### Post by ubfan1 on 2024-11-22
The "slow copy" or "decrease of transfer rate when copying large amount of data" are known problems, with many askubuntu questions and launchpad bugs filed.  Previous postings have covered most of the things to check, but to reiterate: 1) Your MB has two PCIE5 M.2 slots and two PCIE4 M.2 slots, use a fast one for your target.
2)Ensure your partitions/filesystems are aligned properly -- 1MB or even 4MB.
3)System buffers fill up when writes are slower than reads, the usual case. Things slow down when buffers fill.  Using the nocache command on a terminal copy will at least prevent the input stream from being buffered.  
4)The "time" command is usless for determining write speeds, the copying process finishes minutes before the system buffers get flushed. Force the flush with a sync or watch the blinking lights for disk activity to determine the actual finish of the copy.
5)Some copy commands allow you to specify a buffer size --  this may help in limiting memory fragmentation, speeding things up a bit.
6)There are tweaks that may help for specific cases -- different scheduler, altering dirty write bits or rations, but the filling of system buffers will eventually drag things to a crawl.   Slowing the reads down to the write speeds is the goal of such alterations.  Most of the suggestions for tweaks were for hard disks, SSDs are likely to have completely different optimizations.

Follow the previous suggestions for seeing what helps your situation the most.  Understand, this is an unresolved problem that prevents some people from using Linux for their work -- they simply cannot back up their data sets in a timely manner.  Good luck, and interested in seeing what you find helps you the most.

---

### Post by Doug S on 2024-11-23
Just out of interest and because I just so happen to have two nvme drives installed in my main test server at the moment, I tried to see what I get.

Motherboard: ASUS PRIME Z490-A
Memory: 32G
Processor: Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz (turbo to 4.8 GHz)
OS: Ubuntu 24.04.1 (Server, no GUI)
Kernel: 6.12.0-rc7
Format: EXT4 (both NVME drives)
NVME 1: WD_BLACK_SN850X_2000GB
NVME 2: WD_BLACK_SN850X_1000GB
CPU Frequency scaling driver and governor: intel_pstate / performance. HWP disabled.
Force CPU 5 only, to avoid CPU migration delays.

File: 536,870,912,000 random bytes.

Copy from NVME 1 to NVME 2: 1,416,545,942 bytes per second.
Copy from NVME 2 to NVME 1: 1,269,198,374 bytes per second.

Example of Script used:
```
doug@s19:/media/nvme/home/doug/tmp/tmp/tmp/tmp$ cat copy-big-pull
#!/bin/bash
date
taskset -c 5 cp ~/tmp/tmp/tmp/tmp/big ./
date
sync
date
```

EDIT: it doesn't seem to make a difference if the CPU frequency scaling governor is powersave and no forcing of CPU affinity.
Read only rate from:
NVME 1: 2791.103 Mega Bytes per second.
NVME 2: 1611.177 Mega Bytes per second.

---

