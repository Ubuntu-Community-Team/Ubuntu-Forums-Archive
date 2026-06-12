---
title: "Ubuntu using A LOT of memory! (literally 90% of it or more)"
date: 2009-01-31
forum: Hardware
---

### Post by bastones on 2009-01-31
I installed Ubuntu yesterday after I finally got it working wirelessly with my ADVENT 5611 and all seems fine but about 15 minutes ago it became slow and so I checked what was happening via Terminal with *free* and its using literally all of my memory... right now its using 973MB of 944MB (1GB total) and its slow...is this normal as I really haven't used Ubuntu properly before so I'm really slowly transitioning from Windows.

Thanks.

---

### Post by linux_tech on 2009-01-31
Try using htop in terminal to decrease priority of process

---

### Post by Tomatz on 2009-01-31
> **bastones said:**
> I installed Ubuntu yesterday after I finally got it working wirelessly with my ADVENT 5611 and all seems fine but about 15 minutes ago it became slow and so I checked what was happening via Terminal with *free* and its using literally all of my memory... right now its using 973MB of 944MB (1GB total) and its slow...is this normal as I really haven't used Ubuntu properly before so I'm really slowly transitioning from Windows.

Thanks.

Open a terminal and run the command:

```
top
```

Then copy and paste the text (output) from the command on the forums (here).

---

### Post by bastones on 2009-01-31
Hi tomatz,
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
 5288 root      20   0  426m  73m 8580 S   10  7.6   2:16.50 Xorg               
 6881 ben       20   0 97.7m  24m  12m R    3  2.5   0:01.78 gnome-terminal     
 6839 ben       20   0  153m  61m  21m S    2  6.4   1:23.56 firefox            
 5734 ben       20   0 21928  13m 5984 S    1  1.4   0:15.30 compiz.real        
 5133 root      20   0  3440 1060  912 S    1  0.1   0:00.26 hald-addon-stor    
 5750 ben       20   0 21080  11m 7216 S    1  1.2   0:08.64 gtk-window-deco    
 5913 ben       20   0 23708  13m 7412 S    1  1.4   0:01.30 notification-da    
 7103 ben       20   0  2416 1156  884 R    1  0.1   0:01.94 top                
    1 root      20   0  3056 1888  564 S    0  0.2   0:01.52 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.24 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.24 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0

---

### Post by Tomatz on 2009-01-31
> **bastones said:**
> Hi tomatz,
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
 5288 root      20   0  426m  73m 8580 S   10  7.6   2:16.50 Xorg               
 6881 ben       20   0 97.7m  24m  12m R    3  2.5   0:01.78 gnome-terminal     
 6839 ben       20   0  153m  61m  21m S    2  6.4   1:23.56 firefox            
 5734 ben       20   0 21928  13m 5984 S    1  1.4   0:15.30 compiz.real        
 5133 root      20   0  3440 1060  912 S    1  0.1   0:00.26 hald-addon-stor    
 5750 ben       20   0 21080  11m 7216 S    1  1.2   0:08.64 gtk-window-deco    
 5913 ben       20   0 23708  13m 7412 S    1  1.4   0:01.30 notification-da    
 7103 ben       20   0  2416 1156  884 R    1  0.1   0:01.94 top                
    1 root      20   0  3056 1888  564 S    0  0.2   0:01.52 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.24 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.24 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0

Well its not due to an application hang or similar. Can you go to ***System, Administration, System Monitor*** and click the **processes tab** then click ***view, all processes***.

Then try to find the offending process and post what it is.

---

### Post by bastones on 2009-01-31
> **Tomatz said:**
> Well its not due to an application hang or similar. Can you go to ***System, Administration, System Monitor*** and click the **processes tab** then click ***view, all processes***.

Then try to find the offending process and post what it is.

there are quite a few processes running but most aren't using more than 3MB and the most is Firefox at 40MB ... but I checked terminal again and its still only got around 33MB free.

---

### Post by bastones on 2009-01-31
oh according to System Monitor its using only 300MB memory in total? Ubuntu does feel slow however.

---

### Post by Tomatz on 2009-01-31
> **bastones said:**
> oh according to System Monitor its using only 300MB memory in total? Ubuntu does feel slow however.

Save (if needed), close all apps and press ***ctrl alt backspace***.

Log back in and see if that made a difference. If it didn't try rebooting ;)

---

### Post by bastones on 2009-01-31
that fixed the problem - thanks :).

---

### Post by OrangeCrate on 2009-01-31
> **bastones said:**
> that fixed the problem - thanks :).

Since you're new to Linux, for future reference, I thought I might point out that Linux utilizes memory differently to what you've been accustomed to on Windows. Here's a good link discussing this:

**Linux Memory Management or 'Why is there no free RAM?'**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by Tomatz on 2009-01-31
> **bastones said:**
> that fixed the problem - thanks :).

Were you watching a flash video or animation (in your web browser) at the time it happned?

---

### Post by bastones on 2009-01-31
> **Tomatz said:**
> Were you watching a flash video or animation (in your web browser) at the time it happned?

nope...was changing resolution settings and I know now that caused the problem...

---

### Post by Tomatz on 2009-01-31
> **bastones said:**
> nope...was changing resolution settings and I know now that caused the problem...

:popcorn:

---

