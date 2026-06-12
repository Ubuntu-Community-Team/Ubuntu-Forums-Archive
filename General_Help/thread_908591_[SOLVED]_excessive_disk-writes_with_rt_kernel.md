---
title: "[SOLVED] excessive disk-writes with rt kernel ?"
date: 2008-09-02
forum: General Help
---

### Post by robert shearer on 2008-09-02
I am using the eAR-OS remaster of Hardy.Viewing System Monitor shows the hard-drive writing to disk every 5 seconds when the system is idle.
Viewing 'top' gives the following..

 5335 root      20   0  308m  28m  11m R 16.9  2.8   1:01.93 Xorg               
 5836 earmusic  20   0 19216  11m 7068 S  2.8  1.2   0:03.70 metacity           
24567 earmusic  20   0  101m  19m  10m S  2.8  1.9   0:00.49 gnome-terminal     
24678 earmusic  20   0  2308 1124  852 R  2.8  0.1   0:00.08 top                
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.20 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 posix_cpu_timer    
    5 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-high/0     
    6 root     -51  -5     0    0    0 S  0.0  0.0   0:08.73 softirq-timer/0    
    7 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-net-tx/    
    8 root     -51  -5     0    0    0 S  0.0  0.0   0:00.28 softirq-net-rx/    
    9 root     -51  -5     0    0    0 S  0.0  0.0   0:00.77 softirq-block/0    
   10 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-tasklet    
   11 root     -51  -5     0    0    0 S  0.0  0.0   0:00.28 softirq-sched/0    
   12 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-hrtimer    
   13 root     -51  -5     0    0    0 S  0.0  0.0   0:00.81 softirq-rcu/0      
   14 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
   15 root      10 -10     0    0    0 S  0.0  0.0   0:00.10 desched/0          
   16 root      -2  -5     0    0    0 S  0.0  0.0   0:00.10 events/0           
   17 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper   

and comparing this with my standard Hardy install there seem to be a lot of 'soft-irq' entries here.

What is happening here? Should I be concerned?
 What info can I check?. Can I do anything to stop the disc-writes or is this normal?.

Using amd64. But the soft-irq stuff shows up when I use top whilst running from the eAR-OS live cd on an amd Duron/ a Pentium 3/ and a Celeron so I think this is not hardware related?
Is it something to do with the rt-kernel?


Update.. found the culprit =  atieventsd  
by doing   killall  atieventsd   the regular writes have stopped.
So far there have been no other side effects from this so what use is  atieventsd  ?? (I am using a desktop machine and I think that it is for laptops.)

Can I disable it permanently? and how.


Removed ATI frglx driver with Envy and this has fixed it.

---

### Post by robert shearer on 2008-09-04
bump

---

