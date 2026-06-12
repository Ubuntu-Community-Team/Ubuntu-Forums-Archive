---
title: "&quot;Extreme&quot; memory usage"
date: 2013-03-22
forum: Hardware
---

### Post by FishGills on 2013-03-22
Hey everyone, I'm trying to find out what's using up all my memory on my ubuntu-server installation (Should not have any X Windows running). 

```

cdavis@ux1:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2013       1700        312          0         96        178
-/+ buffers/cache:       1425        587
Swap:          551          0        551
cdavis@ux1:~$

```

And from top, sorted by memory usage:

```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                        
 1071 mysql     20   0  317m  46m 6032 S    0  2.3   0:39.29 mysqld                                                                                                          
 1555 root      20   0 19212  13m 1572 S    0  0.7   0:05.85 miniserv.pl                                                                                                     
 1401 root      20   0 49000 9884 5460 S    0  0.5   0:03.24 apache2                                                                                                         
 6329 cdavis    20   0 11484 7836 1552 S    0  0.4   0:01.17 bash                                                                                                            
 1515 www-data  20   0 50348 7696 1916 S    0  0.4   0:00.78 apache2                                                                                                         
 1516 www-data  20   0 50348 7696 1916 S    0  0.4   0:00.74 apache2                                                                                                         
 1517 www-data  20   0 50348 7696 1916 S    0  0.4   0:00.91 apache2                                                                                                         
 1518 www-data  20   0 50348 7696 1916 S    0  0.4   0:00.54 apache2                                                                                                         
 1519 www-data  20   0 50348 7696 1916 S    0  0.4   0:00.83 apache2                                                                                                         
 6227 root      20   0 11772 3556 2784 S    0  0.2   0:00.19 sshd                                                                                                            
 4946 root      20   0 30124 3264 2632 S    0  0.2   0:00.71 console-kit-dae                                                                                                 
 5013 root      20   0 24560 2748 2352 S    0  0.1   0:00.18 polkitd                                                                                                         
  916 root      20   0  6684 2272 1844 S    0  0.1   0:01.24 sshd                                                                                                            
 1216 root      20   0 15088 2108  752 S    0  0.1   0:03.73 sendmail-mta                                                                                                    
    1 root      20   0  3668 1992 1280 S    0  0.1   0:08.17 init                                                                                                            
  754 root      20   0  4744 1584 1372 S    0  0.1   0:00.04 bluetoothd                                                                                                      
 6328 cdavis    20   0 11772 1508  736 S    0  0.1   0:00.41 sshd                                                                                                            
  657 syslog    20   0 31064 1436 1028 S    0  0.1   0:07.73 rsyslogd                                                                                                        
  396 root      20   0  3184 1344  752 S    0  0.1   0:03.69 udevd                                                                                                           
 7070 cdavis    20   0  2832 1100  864 R    0  0.1   0:00.30 top                                                                                                             
  694 root      20   0  3000 1060  896 S    0  0.1   0:02.51 plymouth-upstar                                                                                                 
  666 messageb  20   0  3392 1052  704 S    0  0.1   0:00.42 dbus-daemon                                                                                                     
  943 root      20   0  4688  972  732 S    0  0.0   0:00.03 vsftpd                                                                                                          
  257 root      20   0  2716  960  792 S    0  0.0   0:00.65 plymouthd                                                                                                       
 1052 root      20   0  2620  892  708 S    0  0.0   0:00.18 cron                                                                                                            
 1019 root      20   0  4632  856  732 S    0  0.0   0:00.02 getty                                                                                                           
 1014 root      20   0  4632  852  732 S    0  0.0   0:00.02 getty                                                                                                           
 1028 root      20   0  4632  852  732 S    0  0.0   0:00.02 getty                                                                                                           
 1035 root      20   0  4632  852  732 S    0  0.0   0:00.06 getty                                                                                                           
 1567 root      20   0  4632  852  732 S    0  0.0   0:00.02 getty                                                                                                           
 1030 root      20   0  4632  848  732 S    0  0.0   0:00.03 getty                                                                                                           
  535 root      20   0  3052  824  292 S    0  0.0   0:00.17 udevd                                                                                                           
  537 root      20   0  3052  756  228 S    0  0.0   0:00.05 udevd                                                                                                           
 1066 root      20   0  3604  632  488 S    0  0.0   0:07.78 irqbalance                                                                                                      
  387 root      20   0  2836  608  452 S    0  0.0   0:01.13 upstart-udev-br                                                                                                 
  824 root      20   0  2848  360  212 S    0  0.0   0:00.06 upstart-socket-                                                                                                 
 1053 daemon    20   0  2472  348  224 S    0  0.0   0:00.02 atd                                    

```

Nothing seems out of the ordinary to me? Just an Apache/MySQL server...

Anyone able to help?

---

### Post by Doug S on 2013-03-22
I think what you are seeing is normal. The server will gradually use all the memory, but memory will be freed up if needed. Here is one of my servers:```
doug@doug-64:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3001       2924         77          0        140       2459
-/+ buffers/cache:        323       2677
Swap:         3059          0       3059
```And here is another one```
doug@s15:~/temp$ free -m
             total       used       free     shared    buffers     cached
Mem:         15629       2349      13279          0        825        921
-/+ buffers/cache:        601      15027
Swap:         8099          0       8099
```and the same again after I did something that temporarily used a lot of memory:```
doug@s15:~/c$ free -m
             total       used       free     shared    buffers     cached
Mem:         15629      10559       5069          0        825       9113
-/+ buffers/cache:        619      15009
Swap:         8099          0       8099
```What I did was just read an 8 gigabyte file. However, if I read the file again, the read rate is now 8808.602151 Mega Bytes per second. Why? Because it was already entirely cached in memory. However, if something needed some memory in the meantime then the cache would have been deleted.
Notice how the cached number went up by 8192 in my example. Your server was really using 465 megabytes of memory when you took your snap shot
Edit: Opps, that was my first server (Duh). Yours is using quite a lot (1522 mega bytes. hmmm...)
Edit 2: I would only start to get worried if I started to see swap space being used, and even then only depending on what the server was doing.

---

### Post by Doug S on 2013-03-22
I wonder if you have a memory leak or similar. Here is the top, sorted by memory use for one of my servers, very similar to yours when we consider I have more memory, so the percentage numbers are expected to be different for the same bytes used:```
top - 18:23:04 up 3 days,  1:50,  5 users,  load average: 0.00, 0.01, 0.05
Tasks: 109 total,   1 running, 108 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.3%us,  0.0%sy,  0.0%ni, 98.3%id,  1.3%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3073852k total,  2998216k used,    75636k free,   148056k buffers
Swap:  3133436k total,        0k used,  3133436k free,  2516184k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1250 mysql     20   0  480m  36m 1112 S    0  1.2   0:52.02 mysqld
30381 bind      20   0  245m  28m 2684 S    0  1.0   0:16.92 named
31161 doug      20   0 28932 9.9m 1620 S    0  0.3   0:01.56 bash
32616 doug      20   0 26656 7844 1620 S    0  0.3   0:00.59 bash
 1873 doug      20   0 26684 6996  748 S    0  0.2   0:00.47 bash
 2349 doug      20   0 26684 6996  748 S    0  0.2   0:00.43 bash
 2115 doug      20   0 26684 6940  708 S    0  0.2   0:00.42 bash
 2214 root      20   0 22988 6172 5324 S    0  0.2   1:40.91 tcpdump
 1980 root      20   0 22988 6160 5324 S    0  0.2   1:44.18 tcpdump
  403 www-data  20   0  193m 6124 1156 S    0  0.2   0:00.06 apache2
 3209 www-data  20   0  193m 6120 1176 S    0  0.2   0:00.01 apache2
 3490 www-data  20   0  193m 6120 1148 S    0  0.2   0:00.01 apache2
 2403 www-data  20   0  193m 6108 1176 S    0  0.2   0:00.02 apache2
32428 root      20   0  131m 6072 4744 S    0  0.2   0:00.30 sshd
30972 root      20   0  131m 6056 4728 S    0  0.2   0:00.38 sshd
 3814 www-data  20   0  193m 6044 1148 S    0  0.2   0:00.00 apache2
 3810 www-data  20   0  193m 6036 1144 S    0  0.2   0:00.00 apache2
 3875 www-data  20   0  193m 6032 1132 S    0  0.2   0:00.00 apache2
 3819 www-data  20   0  193m 6024 1144 S    0  0.2   0:00.00 apache2
 3955 www-data  20   0  193m 5920 1076 S    0  0.2   0:00.00 apache2
 1559 root      20   0  193m 5816 1020 S    0  0.2   0:04.80 apache2
 4092 www-data  20   0  193m 5224  416 S    0  0.2   0:00.00 apache2
  699 syslog    20   0  244m 4700  808 S    0  0.2   0:41.22 rsyslogd
30923 root      20   0  121m 4468 3304 S    0  0.1   0:00.34 smbd
 1239 dhcpd     20   0 18996 4388  872 S    0  0.1   0:00.39 dhcpd
 4268 postfix   20   0 46868 3984 3024 S    0  0.1   0:00.00 smtpd
 1979 root      20   0  104m 3716 2728 S    0  0.1   0:00.03 sudo
 2213 root      20   0  104m 3716 2728 S    0  0.1   0:00.02 sudo
 1607 root      20   0  119m 3640 2512 S    0  0.1   0:00.65 smbd
 1599 root      20   0  121m 3412 2428 S    0  0.1   0:00.04 login
 1210 root      20   0  121m 3408 2428 S    0  0.1   0:00.03 login
 1209 root      20   0  121m 3404 2428 S    0  0.1   0:00.03 login
30822 postfix   20   0 38132 3108 2180 S    0  0.1   0:00.06 tlsmgr
 1520 root      20   0  101m 2392 1432 S    0  0.1   0:00.19 winbindd
31159 doug      20   0  131m 2372 1032 S    0  0.1   0:04.03 sshd
32615 doug      20   0  131m 2364 1028 S    0  0.1   0:03.72 sshd
 1507 root      20   0  101m 2204 1268 S    0  0.1   0:00.20 winbindd
 1630 root      20   0  101m 2088 1112 S    0  0.1   0:00.00 winbindd
 1402 whoopsie  20   0  183m 2072  876 S    0  0.1   0:00.01 whoopsie
 1092 root      20   0 49956 2044 1440 S    0  0.1   0:00.02 sshd
    1 root      20   0 24468 1908  900 S    0  0.1   0:01.51 init
30453 postfix   20   0 27336 1744 1416 S    0  0.1   0:00.10 qmgr
 1175 root      20   0 91252 1708  908 S    0  0.1   0:01.99 nmbd
 4271 postfix   20   0 27172 1588 1308 S    0  0.1   0:00.00 proxymap
 4277 postfix   20   0 27184 1532 1252 S    0  0.0   0:00.00 trivial-rewrite
 4148 postfix   20   0 27172 1512 1236 S    0  0.0   0:00.00 pickup
 4274 postfix   20   0 27172 1508 1236 S    0  0.0   0:00.00 anvil
 1637 root      20   0  101m 1468  524 S    0  0.0   0:00.00 winbindd
```Total mem is about 8.7% which roughly (1 signficant digit) jives with the free -m number and the use at the begining of top(once I take out the cached number).

---

### Post by sanderj on 2013-03-23
See here: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

So ... in short ... all is well

---

