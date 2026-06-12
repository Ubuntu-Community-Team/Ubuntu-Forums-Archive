---
title: "frequent, random (?) hard lockups on my new system"
date: 2008-07-14
forum: Hardware
---

### Post by greenmoss on 2008-07-14
Hello all,

I recently built a new box to host my home server and myth needs. It does what I need, except for one **serious** problem. Every few days, the system will hard lock (somtimes it happens within a few hours, sometimes it waits for 4 or 5 days). The system drops all ssh connections, X11 freezes, and even the caps lock key fails to light up the "caps lock" light on the keyboard.

I'm not sure what's wrong. The machine doesn't appear to be doing anything particularly interesting when it locks. It did go into an "infinite repeat" once while playing a video, but the other lockups have happened while nobody was using the machine for anything: no videos, games, or cpu-intensive activity. Perhaps something was running from cron, but it's hard to know for certain.



I tried various diagnostics to track down the problem:
- memtest86 to test the memory (and cpu): 8 full passes, with 0 problems reported
- repeatedly recompile the kernel with flag -j3 to test for cpu/processing problems on both my cores: probably compiled 10 to 20 times, no problems
- run "cpuburn" on both cores: didn't really max the cpu, but I let it run for several hours: no problems
- install lmsensors to check for temperature problems: all temperatures remain within normal ranges, even while cpuburn was running

I'm also trying a "tail" on dmesg, syslog, cron.log, and kern.log. Nothing yet.




There is one message which appears frequently in the kern.log and syslog: 

"atl1 0000:01:00.0: hw csum wrong, pkt_flag:1600, err_flag:80"

I looked around on the internet and couldn't find anything showing this being a problem, or causing lockups.




My system:
- ASUS P5K-V G33 775
- INTEL Core 2 Duo E7200 2.53GHz (on-board video, audio, ethernet)
- 2 GB Memory
- Hauppauge PVR-150 capture card
- PCHDTV 5500 capture card
- 1 x 500 GB PATA disk for /, using ext3
- 4 x 500 GB SATA disks for myth recordings, using ZFS via FUZE
- Ubuntu Hardy with latest updates, running amd64
- Various services, eg netatalk, ssh, postfix, spamassassin, etc
- Not overclocked (yet ;)




So, can anyone suggest something to help me pin down what is causing this problem? If it's the hardware, I still have a week or so to return/exchange it. But I'd need to be certain which piece of hardware was causing the problem before I shipped it back.




Help me, great gurus, you're my only hope!

---

### Post by greenmoss on 2008-07-15
*bump*

anyone?

---

### Post by jimv on 2008-07-15
I, and a lot of other people, have been having this issue with 8.04.  Some people had posted that using the RealTime kernel fixed the issue, so I tried it.  Haven't had any lockups since.

Installing the RT kernel is pretty simple.  Just open a terminal and type "sudo apt-get install linux-rt".

Oh, except you're using the 64 version...which I'm thinking that you can't change to the rt kernel from that.

---

### Post by greenmoss on 2008-07-21
I tried the RT kernel and still had a lockup. I'm thinking maybe it has something to do with the pchdtv 5500. I've disabled it for now to see if the lockups go away.

---

### Post by jcliburn on 2008-08-06
> **greenmoss said:**
> 
There is one message which appears frequently in the kern.log and syslog: 

"atl1 0000:01:00.0: hw csum wrong, pkt_flag:1600, err_flag:80"

This message is from your wired ethernet device, the Attansic L1 NIC.  The device contains a hardware bug that incorrectly flags an IP fragment as having an erroneous TCP or UDP checksum, when in fact, the packet and its checksum are fine.  A patch was recently submitted to the kernel to work around the hardware bug.

In the meantime, you can avoid the condition altogether by adjusting your MTU size to eliminate IP fragmentation.  Google "change MTU size" to find out how to determine exactly what your MTU size should be; it varies depending upon the type of equipment that connects you to the internet.  I'm connected to the outside world by a DSL router, and I have to set my MTU to 1472 instead of the default 1500 to avoid fragmentation.  Anything higher than 1472 and packets get fragmented.

See if that helps.

---

### Post by MirageIndigo on 2008-08-17
I'm been having the same problem on my system for a while.  I'm runnign the 32 bit 8.04.  Syslog, messages, user.log, mythtv logs, all nothing.  This system justlocks.  For me it happens every 18 hours or so.  I thought it was thermal, but the system seems quite cool.  Memtest nothing.

I also have a pcHD5500.  Actually a pair.  I think this card is just cursed.  Whatever I'm hitting you seem to be hitting the same thing.  I will try the RT kernel and see if it helps. 

Note I was having an earlier problem (which pops up less frequently now) with myth frontend crashing X.  This happens when switching between video modes with myth front end playback.  The most recent intel drivers seem to help a lot, though.

---

