---
title: "High CPU usage"
date: 2008-11-23
forum: General Help
---

### Post by alexeix on 2008-11-23
Hi,

I'm running Mythbuntu 8.10 (upgraded from Hardy) and I'm experiencing close to 100% CPU usage most of the time.

Can anyone advise how I can troubleshoot this problem?

I've already checked System Monitor and run 'top' from the Terminal, so I can see the high CPU (and high memory usage), but I can't see any processes which are hogging.

The 2 users are my personal log-in and (presumably) my MythTV log-in.

I've tried exiting the Myth front-end, but it makes no difference.  Anyway, even with Myth running and no recordings/playback taking place, why would it run so high?

I'm using an Athlon64 3200+ with 1GB DDR RAM.

Below are the results of 'top'.
Thanks.

```

top - 13:35:04 up 26 min,  2 users,  load average: 0.61, 1.03, 1.02
Tasks: 123 total,   1 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  1.3%sy,  0.0%ni, 96.1%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:   1025116k total,   889744k used,   135372k free,    19732k buffers
Swap:  3012148k total,     2084k used,  3010064k free,   345476k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5678 root      20   0  199m 115m  13m S  2.0 11.5   4:32.70 Xorg                                                                                            
 6614 alex      20   0  298m  32m  13m S  1.3  3.2   0:04.58 gnome-terminal                                                                                  
 5265 mythtv    20   0  495m  23m 8824 S  1.0  2.3   1:29.29 mythbackend                                                                                     
 6139 alex      20   0  193m 4932 3124 S  0.7  0.5   0:04.62 gnome-screensav                                                                                 
 6638 alex      20   0 19096 1340  992 R  0.7  0.1   0:03.02 top                                                                                             
 5059 mysql     20   0  223m  28m 5988 S  0.3  2.8   1:27.30 mysqld                                                                                          
    1 root      20   0  4100  908  616 S  0.0  0.1   0:02.20 init                                                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.24 events/0                                                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                         
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                   
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 kblockd/0                                                                                       
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   49 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
  150 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                          
  154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                         
  200 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
  201 root      20   0     0    0    0 S  0.0  0.0   0:00.08 pdflush                                                                                         
  202 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kswapd0                                                                                         
  248 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1206 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1209 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 1232 root      15  -5     0    0    0 S  0.0  0.0   0:02.00 ata/0                                                                                           
 1234 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
 1242 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                        
 1989 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                     
 1992 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                       
 1995 root      15  -5     0    0    0 S  0.0  0.0   0:04.02 scsi_eh_1                                                                                       
 2051 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                       
 2053 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                       
 2180 root      15  -5     0    0    0 S  0.0  0.0   0:00.26 kjournald                                                                                       
 2355 root      16  -4 17528 1576  384 S  0.0  0.2   0:00.78 udevd                                                                                           
 4395 root      20   0  3940  600  504 S  0.0  0.1   0:00.00 getty                                                                                           
 4396 root      20   0  3940  600  504 S  0.0  0.1   0:00.00 getty                                                                                           
 4405 root      20   0  3940  596  504 S  0.0  0.1   0:00.00 getty                                                                                           
 4407 root      20   0  3940  596  504 S  0.0  0.1   0:00.00 getty                                                                                           
 4409 root      20   0  3940  600  504 S  0.0  0.1   0:00.00 getty                                                                                           
 4570 root      20   0  4864 1640  548 S  0.0  0.2   0:00.00 acpid                                                                                           
 4614 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 kondemand/0                                                                                     
 4682 syslog    20   0 12364  740  572 S  0.0  0.1   0:00.04 syslogd                                                                                         
 4732 root      20   0  8204  616  496 S  0.0  0.1   0:00.06 dd                                                                                              
 4734 klog      20   0  7700 4324  460 S  0.0  0.4   0:00.16 klogd                                                                                           
 4757 messageb  20   0 21764 1488  720 S  0.0  0.1   0:00.18 dbus-daemon

```

---

### Post by NESFreak on 2008-11-23
try sudo top and you'll see klogd is going mad. no idea why, found this post while searching for the answer.

---

### Post by NESFreak on 2008-11-23
> **zeus77 said:**
> this is a known bug, and a kernel update (which appears to fix this) has been released to intrepid-proposed.  i imagine this should make it into the regular updates in a short while.  for those who need the fix immediately, you can enable intrepid-proposed repositories and install the proposed 2.6.28 kernel update.  for help enabling the proposed repositories, go [here]("https://wiki.ubuntu.com/Testing/EnableProposed").  note that the linux-backports-modules package still has a buggy version of the driver in it, so you'll need to uninstall that (if installed).

for more details on all this, go [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285").

did this help?

---

### Post by alexeix on 2008-11-23
Problem seems to have gone away for now, so I'll check for 'klogd' next time.

I probably won't install that fix though; I'll wait for it to be pushed out, unless the problem gets very bad.

Thanks.

---

