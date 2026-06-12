---
title: "Out of memory; total freeze"
date: 2011-01-12
forum: Hardware
---

### Post by RivalMarco4421 on 2011-01-12
Hello,

Today i was running 2 VM's:

- VMWare Player, Windows 7, 2GB RAM
- VirtualBox, Debian, 1GB RAM

They were both busy uploading stuff and installing things

Now these 2 machines made my laptop crash, the whole x server just freezes, and i can't do anything except giving my laptop a hard reboot..

I've looked in the log file, and i found this:

```
Jan 12 10:15:01 meh kernel: [ 5370.683042] Mem-Info:
Jan 12 10:15:01 meh kernel: [ 5370.683044] DMA per-cpu:
Jan 12 10:15:01 meh kernel: [ 5370.683046] CPU    0: hi:    0, btch:   1 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683049] CPU    1: hi:    0, btch:   1 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683052] CPU    2: hi:    0, btch:   1 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683054] CPU    3: hi:    0, btch:   1 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683057] CPU    4: hi:    0, btch:   1 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683060] CPU    5: hi:    0, btch:   1 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683062] CPU    6: hi:    0, btch:   1 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683065] CPU    7: hi:    0, btch:   1 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683067] Normal per-cpu:
Jan 12 10:15:01 meh kernel: [ 5370.683070] CPU    0: hi:  186, btch:  31 usd: 183
Jan 12 10:15:01 meh kernel: [ 5370.683073] CPU    1: hi:  186, btch:  31 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683075] CPU    2: hi:  186, btch:  31 usd:  28
Jan 12 10:15:01 meh kernel: [ 5370.683078] CPU    3: hi:  186, btch:  31 usd: 127
Jan 12 10:15:01 meh kernel: [ 5370.683080] CPU    4: hi:  186, btch:  31 usd:  20
Jan 12 10:15:01 meh kernel: [ 5370.683083] CPU    5: hi:  186, btch:  31 usd:  30
Jan 12 10:15:01 meh kernel: [ 5370.683086] CPU    6: hi:  186, btch:  31 usd:  60
Jan 12 10:15:01 meh kernel: [ 5370.683089] CPU    7: hi:  186, btch:  31 usd:  30
Jan 12 10:15:01 meh kernel: [ 5370.683091] HighMem per-cpu:
Jan 12 10:15:01 meh kernel: [ 5370.683094] CPU    0: hi:  186, btch:  31 usd: 144
Jan 12 10:15:01 meh kernel: [ 5370.683097] CPU    1: hi:  186, btch:  31 usd:   2
Jan 12 10:15:01 meh kernel: [ 5370.683100] CPU    2: hi:  186, btch:  31 usd:  55
Jan 12 10:15:01 meh kernel: [ 5370.683102] CPU    3: hi:  186, btch:  31 usd:  85
Jan 12 10:15:01 meh kernel: [ 5370.683105] CPU    4: hi:  186, btch:  31 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683108] CPU    5: hi:  186, btch:  31 usd:  28
Jan 12 10:15:01 meh kernel: [ 5370.683111] CPU    6: hi:  186, btch:  31 usd:  18
Jan 12 10:15:01 meh kernel: [ 5370.683113] CPU    7: hi:  186, btch:  31 usd:   0
Jan 12 10:15:01 meh kernel: [ 5370.683119] active_anon:170367 inactive_anon:40477 isolated_anon:0
Jan 12 10:15:01 meh kernel: [ 5370.683121]  active_file:313857 inactive_file:314362 isolated_file:64
Jan 12 10:15:01 meh kernel: [ 5370.683122]  unevictable:4 dirty:0 writeback:0 unstable:0
Jan 12 10:15:01 meh kernel: [ 5370.683123]  free:27069 slab_reclaimable:8837 slab_unreclaimable:7470
Jan 12 10:15:01 meh kernel: [ 5370.683125]  mapped:130958 shmem:5964 pagetables:4354 bounce:0
Jan 12 10:15:01 meh kernel: [ 5370.683133] DMA free:7344kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15788kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:16kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Jan 12 10:15:01 meh kernel: [ 5370.683140] lowmem_reserve[]: 0 869 3965 3965
Jan 12 10:15:01 meh kernel: [ 5370.683152] Normal free:100308kB min:3736kB low:4668kB high:5604kB active_anon:27800kB inactive_anon:30676kB active_file:243888kB inactive_file:244720kB unevictable:0kB isolated(anon):0kB isolated(file):128kB present:890008kB mlocked:0kB dirty:0kB writeback:0kB mapped:80076kB shmem:3180kB slab_reclaimable:35348kB slab_unreclaimable:29864kB kernel_stack:4864kB pagetables:1276kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:858592 all_unreclaimable? no
Jan 12 10:15:01 meh kernel: [ 5370.683160] lowmem_reserve[]: 0 0 24767 24767
Jan 12 10:15:01 meh kernel: [ 5370.683171] HighMem free:624kB min:512kB low:3840kB high:7168kB active_anon:653668kB inactive_anon:131232kB active_file:1011540kB inactive_file:1012728kB unevictable:16kB isolated(anon):0kB isolated(file):128kB present:3170196kB mlocked:16kB dirty:0kB writeback:0kB mapped:443756kB shmem:20676kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:16140kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:3605248 all_unreclaimable? yes
Jan 12 10:15:01 meh kernel: [ 5370.683179] lowmem_reserve[]: 0 0 0 0
Jan 12 10:15:01 meh kernel: [ 5370.683184] DMA: 2*4kB 5*8kB 2*16kB 5*32kB 3*64kB 4*128kB 3*256kB 3*512kB 2*1024kB 1*2048kB 0*4096kB = 7344kB
Jan 12 10:15:01 meh kernel: [ 5370.683197] Normal: 2978*4kB 3448*8kB 955*16kB 407*32kB 174*64kB 81*128kB 18*256kB 0*512kB 0*1024kB 1*2048kB 1*4096kB = 100056kB
Jan 12 10:15:01 meh kernel: [ 5370.683210] HighMem: 100*4kB 26*8kB 1*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 624kB
Jan 12 10:15:01 meh kernel: [ 5370.683222] 634235 total pagecache pages
Jan 12 10:15:01 meh kernel: [ 5370.683225] 0 pages in swap cache
Jan 12 10:15:01 meh kernel: [ 5370.683227] Swap cache stats: add 0, delete 0, find 0/0
Jan 12 10:15:01 meh kernel: [ 5370.683229] Free swap  = 0kB
Jan 12 10:15:01 meh kernel: [ 5370.683231] Total swap = 0kB
Jan 12 10:15:01 meh kernel: [ 5370.701620] 1310704 pages RAM
Jan 12 10:15:01 meh kernel: [ 5370.701623] 1082370 pages HighMem
Jan 12 10:15:01 meh kernel: [ 5370.701625] 406918 pages reserved
Jan 12 10:15:01 meh kernel: [ 5370.701627] 878949 pages shared
Jan 12 10:15:01 meh kernel: [ 5370.701629] 291794 pages non-shared
Jan 12 10:15:07 meh kernel: [ 5376.940700] xsensors invoked oom-killer: gfp_mask=0x280da, order=0, oom_adj=0
Jan 12 10:15:07 meh kernel: [ 5376.940706] xsensors cpuset=/ mems_allowed=0
Jan 12 10:15:07 meh kernel: [ 5376.940710] Pid: 3647, comm: xsensors Tainted: P            2.6.35-24-generic-pae #42-Ubuntu
Jan 12 10:15:07 meh kernel: [ 5376.940713] Call Trace:
Jan 12 10:15:07 meh kernel: [ 5376.940722]  [<c01e4bca>] dump_header+0x7a/0xb0
Jan 12 10:15:07 meh kernel: [ 5376.940728]  [<c01e4c5c>] oom_kill_process+0x5c/0x160
Jan 12 10:15:07 meh kernel: [ 5376.940733]  [<c01e51c9>] ? select_bad_process+0xa9/0xe0
Jan 12 10:15:07 meh kernel: [ 5376.940738]  [<c01e5251>] __out_of_memory+0x51/0xb0
Jan 12 10:15:07 meh kernel: [ 5376.940742]  [<c01e5308>] out_of_memory+0x58/0xd0
Jan 12 10:15:07 meh kernel: [ 5376.940746]  [<c01e81d6>] __alloc_pages_slowpath+0x496/0x4b0
Jan 12 10:15:07 meh kernel: [ 5376.940751]  [<c01e835f>] __alloc_pages_nodemask+0x16f/0x1c0
Jan 12 10:15:07 meh kernel: [ 5376.940757]  [<c01f9147>] do_anonymous_page+0x197/0x3c0
Jan 12 10:15:07 meh kernel: [ 5376.940762]  [<c013a8e4>] ? kmap_atomic_prot+0xe4/0x110
Jan 12 10:15:07 meh kernel: [ 5376.940766]  [<c013a934>] ? kmap_atomic+0x24/0x30
Jan 12 10:15:07 meh kernel: [ 5376.940770]  [<c01fdd27>] handle_mm_fault+0x417/0x510
Jan 12 10:15:07 meh kernel: [ 5376.940776]  [<c013360a>] ? __ticket_spin_is_locked+0x1a/0x20
Jan 12 10:15:07 meh kernel: [ 5376.940783]  [<c05f07bf>] ? _raw_spin_lock_irqsave+0x2f/0x50
Jan 12 10:15:07 meh kernel: [ 5376.940787]  [<c05f40d6>] do_page_fault+0x146/0x440
Jan 12 10:15:07 meh kernel: [ 5376.940793]  [<c03bc39b>] ? acpi_evaluate_object+0x1b8/0x1c5
Jan 12 10:15:07 meh kernel: [ 5376.940799]  [<c03631ca>] ? vsnprintf+0x2da/0x430
Jan 12 10:15:07 meh kernel: [ 5376.940803]  [<c05f3f90>] ? do_page_fault+0x0/0x440
Jan 12 10:15:07 meh kernel: [ 5376.940808]  [<c05f13c7>] error_code+0x73/0x78
Jan 12 10:15:07 meh kernel: [ 5376.940816]  [<c04c00d8>] ? atkbd_show_set+0x8/0x30
Jan 12 10:15:07 meh kernel: [ 5376.940821]  [<c0364d1e>] ? copy_to_user+0x11e/0x130
Jan 12 10:15:07 meh kernel: [ 5376.940826]  [<c023f865>] simple_read_from_buffer+0x95/0xc0
Jan 12 10:15:07 meh kernel: [ 5376.940831]  [<c027a4a4>] sysfs_read_file+0x54/0x90
Jan 12 10:15:07 meh kernel: [ 5376.940837]  [<c02231bf>] vfs_read+0x9f/0x190
Jan 12 10:15:07 meh kernel: [ 5376.940841]  [<c027a450>] ? sysfs_read_file+0x0/0x90
Jan 12 10:15:07 meh kernel: [ 5376.940845]  [<c02232f2>] sys_read+0x42/0x70
Jan 12 10:15:07 meh kernel: [ 5376.940851]  [<c010939f>] sysenter_do_call+0x12/0x28
```

Looking to this in specific, i think my machine is out of memory?

```

Jan 12 10:15:01 meh kernel: [ 5370.683229] Free swap  = 0kB
Jan 12 10:15:01 meh kernel: [ 5370.683231] Total swap = 0kB

Jan 12 10:15:07 meh kernel: [ 5376.940738]  [<c01e5251>] __out_of_memory+0x51/0xb0
Jan 12 10:15:07 meh kernel: [ 5376.940742]  [<c01e5308>] out_of_memory+0x58/0xd0

```

In total, the VM's could maximum be using 3GB RAM, however they are only using just over 1GB in System Monitor.

It's an Intel I7 740 /w 4GB RAM, and 90GB SSD /w 8GB Cache partition.

This happened already 4 times today, what could have caused this?

---

### Post by aschurger on 2011-10-18
Hi, I do not know the answer to your question, but I can add that I have had what seems to be the same sort of problem. When I have a few processes running at once in the background (doing some memory-intensive computations) and one or more of the processes runs out of memory, then *all* of the processes die, other programs become unresponsive, and the whole system becomes unstable requiring a reboot. This has been happening consistently over the past couple of weeks, so I don't think it was a fluke. I hope that someone might have some insight into this. We just switched from Mandriva to Ubuntu at our research center, and frankly I am starting to regret it. Mandriva was not very good, but at least it was stable.

---

### Post by trozamon on 2011-10-18
aschurger, what exactly are you doing and what are the specs of the computers you're running the stuff on (cpu, memory, swap, etc.)?

---

### Post by yragnos on 2012-10-03
Looks like your swap file size is 0 - maybe your swap is not set up. Sero swap space combined with running multiple pages in browser and no  more hard drive space leads to not a happy place.......

In linux leave more disk space so that you can make the most of its efficient file system. It makes it faster not cheaper in terms of storage!

---

### Post by overdrank on 2012-10-03
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

