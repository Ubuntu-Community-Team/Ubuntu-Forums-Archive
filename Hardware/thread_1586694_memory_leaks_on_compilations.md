---
title: "memory leaks on compilations"
date: 2010-10-02
forum: Hardware
---

### Post by teresaejunior on 2010-10-02
Hi, there! I really hope one will take his time to help me!

Recently, I tried recompiling Icecat (Firefox) from its PPA. Everything seems to be OK until memory (2GB) fills and swap begins to fill too. Now, when it just BEGINS to swap, the machine hangs with high disk activity, the display freezes... I left it working for more than 40 minutes to see if it would finish, but the disk LED generally blinks when in high disk activity. This time it wouldn't even blink, but stay shining... BTW, Firefox is a big package to compile.

Today I tried recompiling the kernel, other big package, but when just beginning to compile I faced the same problem. This time I had added 10GB of swap, believe me or not, but as I stated before, it becomes such slow right when beginning to swap.

In this link: [http://forums.gentoo.org/viewtopic-t-541460-start-0.html](http://forums.gentoo.org/viewtopic-t-541460-start-0.html), I see that in Gentoo they change some mounts before compilations, but I don't know if it's the case with debuild. And in this thread [https://forums.gentoo.org/viewtopic-t-808336-start-0.html](https://forums.gentoo.org/viewtopic-t-808336-start-0.html), also in Gentoo, they talk about a similar problem, but reducing -j2 to -j1 didn't solve my problem, it just reduces to one CPU core and takes longer to compile.

I don't face this problem in small packages.

Your help will be very appreciated!
Teresa e Junior

---

### Post by lovinglinux on 2010-10-02
Try my tutorial for Firefox compilation - [http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html](http://firefox-tutorials.blogspot.com/2010/07/compiling-firefox.html)

Firefox takes a long time to compile. I have a Core2 Duo and it takes 40 min to 1 hour. Nevertheless, I also have 2Gb and don't experience such memory issues.

---

### Post by teresaejunior on 2010-10-03
Hello, thanks for your reply! I had a look at your tutorial, but yesterday at night I found my memory seems not to be well configured.

Though I have only entries for "net.ipv6.bindv6only" and "kernel.domainname" in my /etc/sysctl.conf and /etc/sysctl.d/, I noticed I have "vm.swappiness = 0" set, which was not supposed to be the default. I also noticed the following: "vm.panic_on_oom = 0" and "vm.oom_kill_allocating_task = 0", which means the kernel won't worry if there is some memory leak.

Now, I tried setting vm.swappiness, vm.overcommit_memory and vm.overcommit_ratio, but the problem occurred again. What makes me upset is that, every time I have to kill the machine, I'm in the risk of damaging my HD.

In order to help me, would you post the output of this command, so I can compare my settings?

```
sudo sysctl -a | grep ^vm | sort
```

Many people are afraid of malicious commands, so here it goes:
sudo: run command as superuser.
sysctl: configure kernel parameters at runtime.
-a: Display all values currently available.
grep ^vm: extract only values which refer to virtual memory.
sort: in alphabetical order.

---

### Post by IcarusR on 2010-10-03
Read this thread yesterday & compiled icecat myself without issue on my core2 duo 2Gb ram laptop.

Output of your command...

```
vm.block_dump = 0
vm.dirty_background_bytes = 0
vm.dirty_background_ratio = 10
vm.dirty_bytes = 0
vm.dirty_expire_centisecs = 3000
vm.dirty_ratio = 20
vm.dirty_writeback_centisecs = 1500
vm.drop_caches = 0
vm.highmem_is_dirtyable = 0
vm.hugepages_treat_as_movable = 0
vm.hugetlb_shm_group = 0
vm.laptop_mode = 0
vm.legacy_va_layout = 0
vm.lowmem_reserve_ratio = 256    32    32
vm.max_map_count = 65530
vm.memory_failure_early_kill = 0
vm.memory_failure_recovery = 1
vm.min_free_kbytes = 3798
vm.mmap_min_addr = 0
vm.nr_hugepages = 0
vm.nr_overcommit_hugepages = 0
vm.nr_pdflush_threads = 0
vm.oom_dump_tasks = 0
vm.oom_kill_allocating_task = 0
vm.overcommit_memory = 0
vm.overcommit_ratio = 50
vm.page-cluster = 3
vm.panic_on_oom = 0
vm.percpu_pagelist_fraction = 0
vm.scan_unevictable_pages = 0
vm.stat_interval = 1
vm.swappiness = 60
vm.vdso_enabled = 1
vm.vfs_cache_pressure = 100
```

Hope this helps.

---

### Post by teresaejunior on 2010-10-04
Thank you! I compared the values and tried some adjustments, but still no luck. :confused:

Left Icecat compiling for almost 5 hours before killing it...

---

### Post by IcarusR on 2010-10-04
You are aware that there is a ppa repository containing binaries for Ubuntu ?? 

So not necessary to compile.

[https://launchpad.net/~gnuzilla-team/+archive/ppa]("https://launchpad.net/~gnuzilla-team/+archive/ppa")

---

### Post by teresaejunior on 2010-10-04
Thanks for your reply! I'm compiling from the source of their PPA, actually. I needed to make a few changes, and the kernel I actually need to compile, so I can't give up on this.

Here is the output of a few commands:

      ```
# sysctl -a | grep vm. | sort
[CENTER][LEFT][LEFT] error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
vm.block_dump = 0
vm.dirty_background_bytes = 0
vm.dirty_background_ratio = 10
vm.dirty_bytes = 0
vm.dirty_expire_centisecs = 3000
vm.dirty_ratio = 20
vm.dirty_writeback_centisecs = 500
vm.drop_caches = 0
vm.highmem_is_dirtyable = 0
vm.hugepages_treat_as_movable = 0
vm.hugetlb_shm_group = 0
vm.laptop_mode = 0
vm.legacy_va_layout = 0
vm.lowmem_reserve_ratio = 256    32    32
vm.max_map_count = 65530
vm.memory_failure_early_kill = 0
vm.memory_failure_recovery = 1
vm.min_free_kbytes = 3789
vm.mmap_min_addr = 65536
vm.nr_hugepages = 0
vm.nr_overcommit_hugepages = 0
vm.nr_pdflush_threads = 0
vm.oom_dump_tasks = 0
vm.oom_kill_allocating_task = 0
vm.overcommit_memory = 0
vm.overcommit_ratio = 50
vm.page-cluster = 3
vm.panic_on_oom = 0
vm.percpu_pagelist_fraction = 0
vm.scan_unevictable_pages = 0
vm.stat_interval = 1
vm.swappiness = 60
vm.vdso_enabled = 1
vm.vfs_cache_pressure = 100
[/LEFT]
[/LEFT]
[/CENTER]

```[CENTER][LEFT][LEFT]
 
```

$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
``````

$ free -m
             total       used       free     shared    buffers cached
Mem:          1987        437       1549          0    51         192
-/+ buffers/cache:        193       1793
Swap:        10240          0      10240
``````
# swapon -s
Filename                Type        Size    Used    Priority
/dev/sda1                               partition    10486776    0    -1
```[/LEFT]
[/LEFT]
[/CENTER]

---

### Post by teresaejunior on 2010-10-05
Solved, I didn't set -j to 1, I just left it unset...

Thanks!

---

