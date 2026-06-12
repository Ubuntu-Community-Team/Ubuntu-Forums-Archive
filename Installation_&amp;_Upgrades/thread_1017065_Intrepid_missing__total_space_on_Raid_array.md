---
title: "Intrepid missing  total space on Raid array"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by crows4hire on 2008-12-20
I have a new machine running a Gigabyte M61PME-S2 with two 750 Gb hard drives running fakeRaid, mirrored. I have set the partitions simply as 100 Gb for root, 10 Gb for swap and the remainder as home. When the install is complete, I wind up missing about 50 Gb of total space between the partitions. 

df returns the following:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/nvidia_cffciiih1
                      96124904   2270096  88971856   3% /
tmpfs                  1783408         0   1783408   0% /lib/init/rw
varrun                 1783408       100   1783308   1% /var/run
varlock                1783408         0   1783408   0% /var/lock
udev                   1783408      2776   1780632   1% /dev
tmpfs                  1783408       188   1783220   1% /dev/shm
lrm                    1783408      2000   1781408   1% /lib/modules/2.6.27-7-generic/volatile
/dev/mapper/nvidia_cffciiih6
                     1202762284    224924 1141440564   1% /home

In addition, my swap file does not load. Finally, I have 4 Gb of ram installed and System Manager only shows 3.4 Gb. 

I have been re-installing Intrepid in every configuration I can think of for days now and I am at my wits end. HELP!!! ... please!

---

### Post by lemming465 on 2008-12-28
Um,  I'm not sure you are actually missing any space.  More likely you are a victim of the rather confused ways disk space gets measured.  The disk drive vendors sell it units of 10^9 bytes (decimal gigabytes).  Linux tends to show multiples of binary 2^10 = 1024 = 1 kibibyte. 1500000 base 10 kilobytes is roughly 1464883 base 2 kibibytes.  It will look even worse if you use **df -m** and get it measuring in mebibytes (2^20) or gibibytes (2^30).

Swap partitions aren't mounted as filesystems, and df won't show them.  Try **cat /proc/swaps** to see what is actually being used.  You can also find stuff about swap partitions being activated in the output of **dmesg**, which is archived in /var/log/messages.

---

