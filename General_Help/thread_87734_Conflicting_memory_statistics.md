---
title: "Conflicting memory statistics"
date: 2005-11-08
forum: General Help
---

### Post by joris.brus on 2005-11-08
System monitor tells me about 50% memory usage (1Gb total)
when I add up resident memory however I get to about 340 Mb, Which I think is still very steep for what i'm running. 
On top of that 'pardon the pun' when I use top, it tells me 900 Mb is being used with a 100 Mb free and no swap being used. (so does /proc/meminfo)
So.. which one is right?

I know this has been asked before but.. Does my weather app (if find it very usefull), clock, evolution notifier and exchange each need to use 12 mb? It seems terribly inefficient. Retreive weather info, display a number and small picture of clouds, should not use 12 mb. 

One more thing I noticed, I made a script that basically does a whole bunch of grep commands. My cpu is an athlon64 3000, I used the same script at work running redhat enterprise on a pentium 3 700 laptop. The script is about 2.5 times faster on my home pc. This seems very weak.

Any suggestions, comments welcome

---

### Post by Manny C on 2005-11-08
I believe that the GUI interfaces do not count data that is cached on RAM as being used. 

Top does. Top is therefore more accurate.

---

### Post by joris.brus on 2005-11-08
That's terribly inefficient then.. 900mb for a browser, email and messenger. 

I think I'm going to have to try windows for a while, see how it performs.

---

### Post by Manny C on 2005-11-08
It is not inefficient to use RAM rather than swap.

Windows gives the illusion that it doesn't use much RAM, but it actually ships most of the activity to swap. This slows the system down and **is** inefficient.

Do you want to post your top output here?

---

### Post by RAOF on 2005-11-08
Top's memory statistics will include all of the RAM used as buffers.  As will the gnome monitor applet thingy.

The most efficient use of ram is to use **all** of it, all of the time.  There's no point in having 500 mb of ram spare, if you could possibly be using it as a disc cache.  As programs start to use up memory, the disc cache will shrink to accomidate them.

My 1gb of ram tends to be fully used, split ~50% buffers, 50% programs.

Finally, your grep script will almost certainly be IO bound, rather than CPU bound.  The relative speeds of the processors will be a small fraction of the difference in times.  The difference in disc transfer rate and access speed will overwhelm any other difference between the two systems.  Having a 2.5 times faster hard-drive transfer rate sounds about right.  (Actually, if you run the same script twice, you should find the second time it goes dramatically faster - it will be hitting the disc cache rather than the hard-drive.  Even so, this will still be IO bound (this time it will be as fast as your ram-transfer rate))

---

### Post by Manny C on 2005-11-08
Great analysis RAOF.

---

### Post by joris.brus on 2005-11-08
Yeah I never looked at it that way.. that makes sense though, about using 100% RAM. 
I would think that because the files the script uses however are under a 100kb it would cache them right away.. I don't notice a real perfomance gain the second run. 
Is there a good linux cpu benchmarking tool btw?

Here's my top info
almost using all RAM.. now it's a good thing though:D 

Thanks for the solid replies

top - 20:54:54 up  3:13,  3 users,  load average: 1.23, 0.42, 0.25
Tasks:  94 total,   1 running,  93 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.2% us,  1.0% sy,  0.0% ni, 89.8% id,  0.7% wa,  0.0% hi,  0.2% si
Mem:   1022260k total,  1008676k used,    13584k free,    43492k buffers
Swap:  2996080k total,        0k used,  2996080k free,   422032k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
10605 joris     15   0  148m  60m 9612 S  2.0  6.1   0:31.96 btdownloadgui
    1 root      16   0  2628  560  476 S  0.0  0.1   0:00.56 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.14 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   96 root      10  -5     0    0    0 S  0.0  0.0   0:00.25 kblockd/0
   99 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
  130 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  131 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush
  133 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  132 root      15   0     0    0    0 S  0.0  0.0   0:00.05 kswapd0
  718 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1925 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1928 root      25   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1929 root      25   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 3314 root      15   0     0    0    0 S  0.0  0.0   0:00.28 kjournald
 3440 root      13  -4  4776  596  492 S  0.0  0.1   0:00.06 udevd
 5367 root      25   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event

---

### Post by Manny C on 2005-11-09
Looks like bittorrent is taking a large chunk of your RAM. Do you have it running all the time?

---

