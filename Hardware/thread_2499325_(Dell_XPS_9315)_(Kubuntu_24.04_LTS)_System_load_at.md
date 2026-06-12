---
title: "(Dell XPS 9315) (Kubuntu 24.04 LTS) System load at idle is 2.00, not 0.00"
date: 2024-07-23
forum: Hardware
---

### Post by budsnow1 on 2024-07-23
I've just replaced my Windows 11 installation that comes with the laptop with Ubuntu 24.04 LTS then installed KDE Plasma to replace the default desktop. Now I just realized that the system load at idle is 2.00, not 0.00. `top` doesn't show any particular process having high CPU at all. Is this normal?

---

### Post by currentshaft on 2024-07-23
How many cores do you have? Use "htop" for better monitoring results.

---

### Post by budsnow1 on 2024-07-23
> **currentshaft said:**
> How many cores do you have? Use "htop" for better monitoring results.

The CPU is 12th gen Intel Core i7-1250U (10 cores, 12 threads). htop shows me 12 bars from 0-11 which all show no activity. But I wonder why the load number is always >= 2.00.

(As a comparison, my older Dell XPS 9360 laptop, Core i5-7200U, 2 cores / 4 threads, Ubuntu 20.04.6 LTS, "normally" shows load number of 0.0 when idle).

---

### Post by currentshaft on 2024-07-23
> **budsnow1 said:**
> The CPU is 12th gen Intel Core i7-1250U (10 cores, 12 threads). htop shows me 12 bars from 0-11 which all show no activity. But I wonder why the load number is always >= 2.00.

(As a comparison, my older Dell XPS 9360 laptop, Core i5-7200U, 2 cores / 4 threads, Ubuntu 20.04.6 LTS, "normally" shows load number of 0.0 when idle).

There you have it, you have 12 threads, so a system at 100% load would be 12.00 not 2.00.

---

### Post by budsnow1 on 2024-07-24
> **currentshaft said:**
> There you have it, you have 12 threads, so a system at 100% load would be 12.00 not 2.00.

Sorry, I still don't get it. I understand that at exactly 100% load the number would be 12 because that's the number of threads. At higher loads this number can even go higher. But when system is idle (0% load), what does load number of 2.00 mean? From a Google search I got: "Linux load average is a number equal to the number of the running  processes plus a number of processes ready to run and waiting for  available CPU plus the number of processes in uninterruptible state  (usually blocked on disk I/O)." So how do I find this 2 processes that are always running or or ready to run or in uninterruptible state?

I also found [https://serverfault.com/questions/251299/high-load-average-over-2-0-on-an-idle-machine](https://serverfault.com/questions/251299/high-load-average-over-2-0-on-an-idle-machine)

I guess I'll try trying out different kernels then.

---

### Post by currentshaft on 2024-07-24
A load of 2 on a system with 12 threads means it's 1/6th under load.

If you're asking why the load is not zero, it's because you're running a graphical desktop OS which is resource hungry.

You can sort htop by CPU time to find the exact processes.

---

### Post by budsnow1 on 2024-07-26
> **currentshaft said:**
> A load of 2 on a system with 12 threads means it's 1/6th under load.

If you're asking why the load is not zero, it's because you're running a graphical desktop OS which is resource hungry.

You can sort htop by CPU time to find the exact processes.

I've never seen an idle Linux graphical desktop environment, on all my PC's and laptops I've ever had, has a minimum load of 2.00. And htop does not show any particular processes showing on the top of the list, after sorting by CPU time, though it shows period spikes of thread 0, 1, 2 mostly.

I booted to safe mode so there's no graphial environment running at all. The load is even higher, around 3.

So I booted Debian 12 live and the there the load number when idle is less than 1 (0.15, which still seems high because my older laptop can get to 0.0x fine).

Confirming kernel problem.

---

### Post by currentshaft on 2024-07-26
> **budsnow1 said:**
> I've never seen an idle Linux graphical desktop environment, on all my PC's and laptops I've ever had, has a minimum load of 2.00. And htop does not show any particular processes showing on the top of the list, after sorting by CPU time, though it shows period spikes of thread 0, 1, 2 mostly.

I booted to safe mode so there's no graphial environment running at all. The load is even higher, around 3.

So I booted Debian 12 live and the there the load number when idle is less than 1 (0.15, which still seems high because my older laptop can get to 0.0x fine).

Confirming kernel problem.

It's not a kernel problem. There is not even any problem from what I can tell, just an odd fascination with a number.

---

### Post by Yellow Pasque on 2024-07-27
In htop, click the 'S' column to find processes by state

```
STATE (S)
            The state of the process:
               S for sleeping
               I for idle (longer inactivity than sleeping on platforms that distinguish)
               R for running
               D for disk sleep (uninterruptible)
               Z for zombie (waiting for parent to read its exit status)
               T for traced or suspended (e.g by SIGTSTP)
               W for paging
```

EDIT: If your load number is always about 2.0 or a bit over when idle, I'm going to guess you you have 2 processes that are uninterruptible. And being Kubuntu, I wouldn't be surprised if at least one of them was related to the Baloo file indexer.

---

### Post by Doug S on 2024-07-27
I would say that a load average of 2 on an idle system seems a little high.

Disclaimer: I am a server person, and only know that "idle" on a server (no GUI) is not the same as "idle" on a desktop.

Load average doesn't include CPU frequency, so a higher load average might just indicate the CPU frequency is staying low, and could actually be a good thing in terms of power consumption. Note that load average is a sampled calculation, so it is possible to have aliasing effects contribute to false numbers, although I haven't seen such for a few years now.

Anyway, show us your actual data, maybe we can see something. Example from my server, which is doing something right now:

```
top - 08:25:56 up 14:37,  3 users,  load average: 2.04, 2.04, 2.01
Tasks: 242 total,   1 running, 241 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.7 us,  2.7 sy,  0.0 ni, 85.3 id, 11.2 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  31924.4 total,    398.6 free,    896.3 used,  31100.5 buff/cache
MiB Swap:   8192.0 total,   8191.7 free,      0.2 used.  31028.1 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   3609 doug      20   0   13904   2260   1168 S  18.9   0.0  10:38.96 rsync
   3607 doug      20   0   13932   7272   6248 D  15.6   0.0   8:47.35 rsync
    116 root      20   0       0      0      0 S   3.9   0.0   4:31.65 kswapd0
   3662 root      20   0       0      0      0 D   2.0   0.0   0:37.28 kworker/u48:2+flush-8:16
   3797 root      20   0       0      0      0 I   1.2   0.0   0:00.70 kworker/u48:5-ext4-rsv-conversion
     79 root      rt   0       0      0      0 S   0.1   0.0   0:00.29 migration/10
      1 root      20   0   22396  13084   9244 S   0.0   0.0   0:01.56 systemd
```

I have 12 CPUs, so my wait of 11.2% means 134% of load average. Plus the other actual loads of ~42%, is ~176 or a load average of 1.8. So, close.

I do have a 24.04 desktop VM, with 4 VCPUs, and it shows a load average of 0.01 when idle. Note: wait at least 10 minutes after boot, as there always seems to be some post boot stuff that increases the load average:
```
doug@desk-nn:~$ uptime
 08:35:16 up 27 min,  2 users,  load average: 0.01, 0.04, 0.03
```
and
```
top - 08:38:37 up 30 min,  2 users,  load average: 0.00, 0.01, 0.01
Tasks: 215 total,   1 running, 214 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni, 99.9 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   7941.3 total,   5595.8 free,   1108.5 used,   1519.8 buff/cache
MiB Swap:   4096.0 total,   4096.0 free,      0.0 used.   6832.8 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   4406 doug      20   0   14652   5888   3712 R   0.2   0.1   0:00.03 top
      1 root      20   0   23172  13720   9112 S   0.0   0.2   0:02.79 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_g
```

---

