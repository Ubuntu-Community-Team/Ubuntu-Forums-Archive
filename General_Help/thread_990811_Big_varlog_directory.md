---
title: "Big var/log directory"
date: 2008-11-23
forum: General Help
---

### Post by mjetek on 2008-11-23
Hi, I installed ubuntu 8.10 two days ago and now my /var/log/ directory has 11.3GB. Propably I won't need these files, so can I delete these directory?

---

### Post by dexter on 2008-11-23
That is extremely big. Which files are taking up al that space?

My /var/log is only 6.9MiB.

---

### Post by Elfy on 2008-11-23
What hardware do you have - can you look in your logs - System Logs in System>admin menu - while it might not make much sense to you are there a lot of lines relating to memory or hdd/swap - can't remember exactly - but you might be affected by a reported bug.

The fix if that is the case is to use the proposed updates to get the next kernel.

I'll try and find the bug.

Edit -  this one = [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285)

Run this from a terminal

```
dmesg |grep swapper
```
see if it gives an output

---

### Post by mjetek on 2008-11-23
in this directory i have two extremaly big files: kern.log.0 has 5.7GB and messages.0 has 5.3GB. I have 64bit edition ubuntu with kernel 2.6.27-7-generic. I use this on my laptop ASMobile S96S, with processor intel core 2 duo t7500, graphics GeeForce 8600GS. Command ```
dmesg |grep swapper
``` doesn't give any output.

---

### Post by Elfy on 2008-11-23
Well it was a bit of a guess tbh - did you look at the bug report, you need to - I know that it's been seen on a laptop - whether he had similar I don't know.

What can you see in the error logs - you'll be looking for something that repeats itself and I would think probably quite easy to see.

You can run dmesg and get it to show the last few entries - defaults to 10 

```
dmesg |tail
``` would default to 10 adding -20 would give 20 lines
```
dmesg |tail -20
```

You could also look in there for errors - but it might not report as an error

```
dmesg |grep error
```

---

### Post by mjetek on 2008-11-23
on begin of file kern.log.0 is a lot of repeats of something similar to

```

Nov 21 10:56:42 mjetek-laptop kernel: [ 4560.092103] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov 21 10:56:42 mjetek-laptop kernel: [ 4560.092122] ata1.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 16392 in
Nov 21 10:56:42 mjetek-laptop kernel: [ 4560.092124]          cdb 4a 01 00 00 10 00 00 00  08 00 00 00 00 00 00 00
Nov 21 10:56:42 mjetek-laptop kernel: [ 4560.092126]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Nov 21 10:56:42 mjetek-laptop kernel: [ 4560.092131] ata1.01: status: { DRDY }
Nov 21 10:56:47 mjetek-laptop kernel: [ 4565.136085] ata1: link is slow to respond, please be patient (ready=0)
Nov 21 10:56:51 mjetek-laptop kernel: [ 4569.937076] iwlagn: index 255 not used in uCode key table.
Nov 21 10:56:52 mjetek-laptop kernel: [ 4570.120082] ata1: device not ready (errno=-16), forcing hardreset
Nov 21 10:56:52 mjetek-laptop kernel: [ 4570.120099] ata1: soft resetting link
Nov 21 10:56:52 mjetek-laptop kernel: [ 4570.336341] ata1.01: configured for UDMA/33
Nov 21 10:56:52 mjetek-laptop kernel: [ 4570.336364] ata1: EH complete
Nov 21 10:57:53 mjetek-laptop kernel: [ 4631.937089] iwlagn: index 255 not used in uCode key table.

```
but at end of this file i have repeated these lines:
```

Nov 21 18:21:18 mjetek-laptop kernel: [20967.659115] bad: scheduling from the idle thread!
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659117] Pid: 0, comm: swapper Not tainted 2.6.27-7-generic #1
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659119] 
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659120] Call Trace:
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659123]  [<ffffffff8023e06d>] dequeue_task_idle+0x2d/0x40
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659126]  [<ffffffff8023c436>] dequeue_task+0x96/0xe0
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659129]  [<ffffffff8023c4d3>] deactivate_task+0x23/0x30
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659132]  [<ffffffff80500685>] thread_return+0x108/0x3c3
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659135]  [<ffffffff8026d12e>] ? sched_clock_idle_wakeup_event+0xe/0x10
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659138]  [<ffffffff80210ecd>] cpu_idle+0xad/0x110
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659141]  [<ffffffff804fd735>] start_secondary+0x97/0xc2
Nov 21 18:21:18 mjetek-laptop kernel: [20967.659143] 

```
Command ```
dmesg |tail -20
``` give these output:
```

[  701.164206] ata1: device not ready (errno=-16), forcing hardreset
[  701.164222] ata1: soft resetting link
[  701.384488] ata1.01: configured for UDMA/33
[  701.384510] ata1: EH complete
[  756.144123] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  756.144138] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[  756.144140]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  756.144142]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  756.144147] ata1.01: status: { DRDY }
[  761.200204] ata1: link is slow to respond, please be patient (ready=0)
[  766.184183] ata1: device not ready (errno=-16), forcing hardreset
[  766.184198] ata1: soft resetting link
[  766.396486] ata1.01: configured for UDMA/33
[  766.396509] ata1: EH complete
[ 1369.144229] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 1369.144246] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 1369.144248]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1369.144249]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 1369.144254] ata1.01: status: { DRDY }
[ 1374.184212] ata1: link is slow to respond, please be patient (ready=0)

```
And command ```
dmesg |grep error
```give this 
```
[   12.528173] usb 5-2: device not accepting address 2, error -71 
```

---

### Post by -Zeus- on 2008-11-23
try running this:

```
du -ah /var/log/
```

---

### Post by Elfy on 2008-11-23
> swapper Not tainted 2.6.27-7-genericThis I think is the problem - the fix is in the newer kernel it appears, it's only been released to proposed afaik.

Open Software Sources in System Admin menu - updates tab - enable proposed. Close and let it reload the sources, run the update manager.

Similar here - [http://ubuntuforums.org/showthread.php?p=6189105](http://ubuntuforums.org/showthread.php?p=6189105)

Take note of what proposed is offering to update - might be worth just updating the kernel and checking the other updates for possible problems.

---

### Post by mjetek on 2008-11-23
Ok i installed new kernel and removed the biggest files from /var/log directory. Now i think that everything is ok. Thanks

---

