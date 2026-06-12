---
title: "Help understanding memory usage in Ubuntu."
date: 2005-11-29
forum: General Help
---

### Post by a212359 on 2005-11-29
Hello, I am running breezy on an asus m6n laptop, with 1GB ram. After leaving it on for a week or so, I noticed I had ~100k free memory while doing nothing.  Xorg was using most of the memory. 

I am pretty new at linux so and would like a bit of help understanding how the memory is being used, what is reasonable and what isn't, etc.

So I have rebooted and started fvwm via gdm. The fvwm is without a config file - so its just a blank screen. I am typing this in vi in a mrxvt terminal, and there are two xterms open, and thats it.

Here is the output of free:
```

             total       used       free     shared    buffers     cached
Mem:       1035772     223792     811980          0      35436     131328
-/+ buffers/cache:      57028     978744
Swap:      1124508          0    1124508

```
Here is the output from top:
```

top - 23:50:51 up 12 min,  1 user,  load average: 0.00, 0.04, 0.03
Tasks:  62 total,   1 running,  61 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7% us,  1.0% sy,  0.0% ni, 98.3% id,  0.0% wa,  0.0% hi,  0.0%
Mem:   1035772k total,   225536k used,   810236k free,    36416k buffers
Swap:  1124508k total,        0k used,  1124508k free,   131356k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    7 root      11  -5     0    0    0 S  0.3  0.0   0:00.56 kacpid
 8122 hal       16   0  5136 3828 1604 S  0.3  0.4   0:00.59 hald
 8243 root      15   0 80416  12m 2716 S  0.3  1.2   0:01.54 Xorg
 8683 user      15   0  8404 4112 2192 S  0.3  0.4   0:00.57 xterm
 8803 user      16   0  2132 1072  844 R  0.3  0.1   0:00.13 top
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.10 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 events/0
    4 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
  110 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0
  134 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  135 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  137 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0  
  722 root      15   0     0    0    0 S  0.0  0.0   0:00.03 kseriod
 2241 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 3452 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 reiserfs/0
 3642 root      15  -4  1660  568  484 S  0.0  0.1   0:00.04 udevd
 4860 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 5785 root      25   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 6392 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 6402 root      23   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 6489 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 6551 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 ipw2200/0
 7515 dhcp      16   0  2460 1132  824 S  0.0  0.1   0:00.00 dhclient3
 8062 root      18   0  1956 1116  560 S  0.0  0.1   0:00.00 acpid
 8077 syslog    16   0  1884  756  636 S  0.0  0.1   0:00.01 syslogd
 8094 root      16   0  1564  400  328 S  0.0  0.0   0:00.00 dd
 8096 klog      16   0  2568 1544  468 S  0.0  0.1   0:00.07 klogd
 8109 messageb  16   0  2148 1036  908 S  0.0  0.1   0:00.00 dbus-daemon
 8127 hal       15   0  1864  700  608 S  0.0  0.1   0:00.00 hald-addon-acp
 8143 hal       16   0  1872  632  544 S  0.0  0.1   0:00.07 hald-addon-sto
 8182 root      16   0 10448 2576 2056 S  0.0  0.2   0:00.00 gdm
 8187 root      16   0 10776 3004 2436 S  0.0  0.3   0:00.00 gdm
 8246 cupsys    16   0  6272 3196 1168 S  0.0  0.3   0:00.16 cupsd
 8274 hplip     16   0 12740 1284 1064 S  0.0  0.1   0:00.00 hpiod
 8287 hplip     16   0  8952 5852 2360 S  0.0  0.6   0:00.00 python
 8381 root      18   0  1708  736  544 S  0.0  0.1   0:00.00 cardmgr
 8479 root      21   5  1552  528  460 S  0.0  0.1   0:00.00 powernowd
 8494 root      24   0  1924  816  712 S  0.0  0.1   0:00.00 hcid
 8500 root      24   0  1612  556  480 S  0.0  0.1   0:00.00 sdpd
 8510 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 8542 daemon    25   0  1876  652  564 S  0.0  0.1   0:00.00 atd
 8555 root      16   0  1940  856  712 S  0.0  0.1   0:00.00 cron
 8598 root      16   0  1560  496  424 S  0.0  0.0   0:00.00 getty
 8599 root      16   0  1560  496  424 S  0.0  0.0   0:00.00 getty
 8600 root      16   0  1556  488  424 S  0.0  0.0   0:00.00 getty
 8601 root      16   0  1556  492  424 S  0.0  0.0   0:00.00 getty
 8602 root      16   0  1556  492  424 S  0.0  0.0   0:00.00 getty
 8603 root      16   0  1556  492  424 S  0.0  0.0   0:00.00 getty
 8624 user      15   0  6128 2604 2036 S  0.0  0.3   0:00.65 fvwm2
 8667 user      16   0  3124 1004  808 S  0.0  0.1   0:00.00 ssh-agent
 8670 user      22   0  2576  744  620 S  0.0  0.1   0:00.00 dbus-launch
 8671 user      22   0  2036  744  644 S  0.0  0.1   0:00.00 dbus-daemon 
 8672 user      16   0  8440 3388 2200 S  0.0  0.3   0:00.26 xterm
 8673 user      15   0  4520 2064 1292 S  0.0  0.2   0:00.02 bash
 8684 user      15   0  4516 2056 1292 S  0.0  0.2   0:00.02 bash
 8703 user      16   0  6464 3012 1820 S  0.0  0.3   0:00.29 mrxvt
 8704 user      16   0  4524 2064 1292 S  0.0  0.2   0:00.01 bash
 8715 user      16   0  5040 2604 1544 S  0.0  0.3   0:00.41 vi
 8819 user      16   0  5048 2524 1500 S  0.0  0.2   0:00.08 vi

```


The amount of memory being used now (225k) still seems like a lot considering I'm basically doing nothing...I am not sure what a lot of the things in the top output are, or why gdm seems to have two entries, for example. I'm guessing a lot of it is normal system stuff, but I am wondering if some of it is unecessary, and how this memory usage compares to what it should be...thanks!

---

### Post by RAOF on 2005-11-29
You could check [here]("http://www.ubuntuforums.org/showthread.php?t=87734&highlight=memory").  There's some stuff about how linux manages/reports/uses memory.  Basically, the objective is to use 100% of the RAM, 100% of the time.

---

### Post by a212359 on 2005-11-30
Thanks for the link - that makes some sense. 

Here is a quick follow-up question: My computer has been on since I rebooted (see 1st post), so thats around 16 hours now. If I repeat the conditions in the first post (two xterm and one mrxvt), the memory being used has increased by 150k, so its now at ~380k. The only thing that has changed is that I had firefox open for a while, browsed, and shut it down.  So my quesiton is how does one explain why more memory is being used now?

(In my naive picture, the "base" amount of memory being used when I am doing nothing should not change, no matter how long my computer has been on, or what programs I use in between...)

Thanks again.

---

### Post by Casey on 2005-11-30
More memory is being used now because your computer is caching files from the hard disk (where access is slow) in memory (where access is quick) as you use them.  As long as that memory is otherwise not being used, this costs you nothing but gives you the benefit of faster access.

The more programs you open and close, the more memory you will use (to a point... at a point linux starts unloading old programs from memory when necessary to insure that you have enough memory to open and use other programs).

---

### Post by a212359 on 2005-11-30
[QUOTE=Casey]The more programs you open and close, the more memory you will use (to a point... at a point linux starts unloading old programs from memory when necessary to insure that you have enough memory to open and use other programs).[/QUOTE]

ok, thanks for the info - I think I am starting to get the idea. I think I will need to find some more reading on this subject, its sort of interesting...thanks for all the help though.

---

### Post by infoseeker on 2005-11-30
Just found a bug in Kubuntu : 
Step 1 : right click desktop 
Step 2 : select 'create new' --> 'text file' 
Step 3 : enter filename eg. 'memory' and select 'ok' (saves as text file) Step 4 : double click file newly created text file (opens with Kate) 
Step 5 : enter letters 'top' on line 1 
Step 6 : press enter 
Step 7 : enter 'free' on line 2 and press enter 
>  top
free
 
 Step 8 : save the file

 THE TEXT FILE IS THEN SAVED BUT IT IS SAVED AS A QUICKTIME VIDEO :) DO NOT ATTEMPT TO OPEN THE FILE...NOATUN GOES CRAZY ! :) I don't know if this will happen in Ubuntu.....don't have it installed .

---

