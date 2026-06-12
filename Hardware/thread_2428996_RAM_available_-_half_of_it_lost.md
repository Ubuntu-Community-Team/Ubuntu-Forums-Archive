---
title: "RAM available - half of it lost?"
date: 2019-10-12
forum: Hardware
---

### Post by drechsel on 2019-10-12
Hello everybody,

at my machine, there is 12 GB of physical RAM installed. 
```
sudo dmidecode -t17

```
displays the 4 bars - 2x2, and 2x4GB.

Now, when I do a ```
$ free -m
```, look into ```
top
``` or into gnome-control-center, I find that only 5,8GB of RAM are available. Which info is correct? - Do I actually loose half of my RAM?

Cheers,
Wolf

---

### Post by sudodus on 2019-10-12
Please tell us which version of Ubuntu you are running (for example 18.04.x LTS) and which architecture (32-bit alias i386 or 64-bit alias amd64).

If 32-bit, there are issues to manage big RAM. In that case please consider installing a 64-bit version of Ubuntu.

Otherwise there could be other problems, for example related to hardware. Does the UEFI/BIOS system see all memory? Have you tested the memory with memtest?

---

### Post by oldfred on 2019-10-12
Linux uses RAM as a cache to reload some app you recently used.

Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Difference between Details screen on RAM and free command
[http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649](http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649) &
[https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221](https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221)

---

### Post by TheFu on 2019-10-12
And actually showing the output from the commands would be nice.  Or do we need our secret-squirrel crypto-authentication rings first?

Besides buffers, integrated GPUs will grab some amount of RAM.
```
$ head /proc/meminfo 
MemTotal:        **8048236** kB
MemFree:          604768 kB
MemAvailable:    3913008 kB

```
```

$ inxi -b
....
Info:      Processes: 343 Uptime: 5 days Memory: 3462.9/**7859.6MB**
```

```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           **7.7G**        2.9G        682M        523M        4.1G        3.8G
Swap:          4.5G         17M        4.4G
....
```

```
$ top -b
top - 12:33:40 up 5 days, 17:35,  3 users,  load average: 0.36, 0.42, 0.52
Tasks: 343 total,   1 running, 246 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.6 us,  3.0 sy,  0.0 ni, 87.2 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem :  **8048236** total,   686920 free,  3046452 used,  4314864 buff/cache
KiB Swap:  4673532 total,  4655392 free,    18140 used.  3994300 avail Mem 

```

```
$ sudo lshw -class memory
  *-memory                
       description: System memory
       physical id: 0
       size: **7859MiB**

```

So, what happened to my RAM?  The iGPU ... ?
```
$ lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 1d30
        Flags: bus master, fast devsel, latency 0, IRQ 126
        Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, **prefetchable**) [size=**256M**]
        I/O ports at f000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

```

7859 + 256 = 8115 MB  Hummmm.
1024 x 8 = 8192  MB
Close enough for me.

YMMV.

---

