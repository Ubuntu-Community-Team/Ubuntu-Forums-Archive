---
title: "Something eating all memory"
date: 2008-11-05
forum: General Help
---

### Post by Colin@oxford on 2008-11-05
A couple of times in the last week I have been doing nothing much at the computer when Firefox suddenly disappears, then Thunderbird, then Gnome and all I can do is press ctrl-alt-F1 and do a reboot.  Things that have changed:

1) Automatic update to linux-image-2.6.24-21-rt.  Don't know why I have this kernel since before I only had the generic one

2) Using virtualbox - max 500MB in guest OS - total 2GB real memory

This is a complete section of kern.log where a process is zapped:
[INDENT]
```

[FONT="Courier New"]Nov  4 16:54:42 Asus kernel: [ 2704.418768] printk: 612 messages suppressed.
Nov  4 16:54:42 Asus kernel: [ 2704.418773] authatieventsd. invoked oom-killer: gfp_mask=0xd0, order=1, oomkilladj=0
Nov  4 16:54:42 Asus kernel: [ 2704.418777] Pid: 26209, comm: authatieventsd. Not tainted 2.6.24-21-rt #1
Nov  4 16:54:42 Asus kernel: [ 2704.418791]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Nov  4 16:54:42 Asus kernel: [ 2704.418805]  [out_of_memory+0x16c/0x1b0] out_of_memory+0x16c/0x1b0
Nov  4 16:54:42 Asus kernel: [ 2704.418816]  [nfs:__alloc_pages+0x34c/0x380] __alloc_pages+0x34c/0x380
Nov  4 16:54:42 Asus kernel: [ 2704.418832]  [nfs:__get_free_pages+0x37/0x820] __get_free_pages+0x37/0x50
Nov  4 16:54:42 Asus kernel: [ 2704.418835]  [copy_process+0xa6/0x1300] copy_process+0xa6/0x1300
Nov  4 16:54:42 Asus kernel: [ 2704.418843]  [handle_mm_fault+0x138/0x770] handle_mm_fault+0x138/0x770
Nov  4 16:54:42 Asus kernel: [ 2704.418852]  [powernow_k8:kmem_cache_alloc+0x63/0x610] kmem_cache_alloc+0x63/0xc0
Nov  4 16:54:42 Asus kernel: [ 2704.418861]  [do_fork+0x40/0x260] do_fork+0x40/0x260
Nov  4 16:54:42 Asus kernel: [ 2704.418867]  [get_empty_filp+0xda/0x190] get_empty_filp+0xda/0x190
Nov  4 16:54:42 Asus kernel: [ 2704.418872]  [fd_install+0x21/0x50] fd_install+0x21/0x50
Nov  4 16:54:42 Asus kernel: [ 2704.418878]  [do_pipe+0x7c/0xf0] do_pipe+0x7c/0xf0
Nov  4 16:54:42 Asus kernel: [ 2704.418886]  [sys_clone+0x36/0x40] sys_clone+0x36/0x40
Nov  4 16:54:42 Asus kernel: [ 2704.418891]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Nov  4 16:54:42 Asus kernel: [ 2704.418907]  =======================
Nov  4 16:54:42 Asus kernel: [ 2704.418908] Mem-info:
Nov  4 16:54:42 Asus kernel: [ 2704.418910] DMA per-cpu:
Nov  4 16:54:42 Asus kernel: [ 2704.418911] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov  4 16:54:42 Asus kernel: [ 2704.418914] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov  4 16:54:42 Asus kernel: [ 2704.418915] Normal per-cpu:
Nov  4 16:54:42 Asus kernel: [ 2704.418917] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Nov  4 16:54:42 Asus kernel: [ 2704.418919] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Nov  4 16:54:42 Asus kernel: [ 2704.418921] HighMem per-cpu:
Nov  4 16:54:42 Asus kernel: [ 2704.418923] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Nov  4 16:54:42 Asus kernel: [ 2704.418925] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Nov  4 16:54:42 Asus kernel: [ 2704.418928] Active:127624 inactive:14736 dirty:0 writeback:0 unstable:0
Nov  4 16:54:42 Asus kernel: [ 2704.418929]  free:119625 slab:32478 mapped:35427 pagetables:663 bounce:0
Nov  4 16:54:42 Asus kernel: [ 2704.418931] DMA free:3532kB min:64kB low:80kB high:96kB active:0kB inactive:0kB present:16160kB pages_scanned:0 all_unreclaimable? no
Nov  4 16:54:42 Asus kernel: [ 2704.418933] lowmem_reserve[]: 0 867 1877 1877
Nov  4 16:54:42 Asus kernel: [ 2704.418937] Normal free:5072kB min:3736kB low:4668kB high:5604kB active:100kB inactive:0kB present:888800kB pages_scanned:0 all_unreclaimable? no
Nov  4 16:54:42 Asus kernel: [ 2704.418939] lowmem_reserve[]: 0 0 8077 8077
Nov  4 16:54:42 Asus kernel: [ 2704.418942] HighMem free:469896kB min:512kB low:1596kB high:2684kB active:510396kB inactive:58944kB present:1033928kB pages_scanned:0 all_unreclaimable? no
Nov  4 16:54:42 Asus kernel: [ 2704.418944] lowmem_reserve[]: 0 0 0 0
Nov  4 16:54:42 Asus kernel: [ 2704.418946] DMA: 1*4kB 1*8kB 0*16kB 0*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3532kB
Nov  4 16:54:42 Asus kernel: [ 2704.418953] Normal: 277*4kB 25*8kB 2*16kB 2*32kB 2*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 5116kB
Nov  4 16:54:42 Asus kernel: [ 2704.418958] HighMem: 7237*4kB 8367*8kB 3904*16kB 1853*32kB 672*64kB 227*128kB 90*256kB 53*512kB 35*1024kB 22*2048kB 12*4096kB = 469932kB
Nov  4 16:54:42 Asus kernel: [ 2704.418965] Swap cache: add 15631, delete 13315, find 1539/1895, race 0+0
Nov  4 16:54:42 Asus kernel: [ 2704.418967] Free swap  = 2044684kB
Nov  4 16:54:42 Asus kernel: [ 2704.418968] Total swap = 2096472kB
Nov  4 16:54:42 Asus kernel: [ 2704.418969] Free swap:       2044684kB
Nov  4 16:54:42 Asus kernel: [ 2704.428889] 491440 pages of RAM
Nov  4 16:54:42 Asus kernel: [ 2704.428956] 262064 pages of HIGHMEM
Nov  4 16:54:42 Asus kernel: [ 2704.429009] 8031 reserved pages
Nov  4 16:54:42 Asus kernel: [ 2704.429057] 99566 pages shared
Nov  4 16:54:42 Asus kernel: [ 2704.429104] 2316 pages swap cached
Nov  4 16:54:42 Asus kernel: [ 2704.429157] 0 pages dirty
Nov  4 16:54:42 Asus kernel: [ 2704.429198] 0 pages writeback
Nov  4 16:54:42 Asus kernel: [ 2704.429243] 35427 pages mapped
Nov  4 16:54:42 Asus kernel: [ 2704.429289] 32478 pages slab
Nov  4 16:54:42 Asus kernel: [ 2704.429339] 663 pages pagetables
Nov  4 16:54:42 Asus kernel: [ 2704.429389] Out of memory: kill process 9631 (run-mozilla.sh) score 78749 or a child
Nov  4 16:54:42 Asus kernel: [ 2704.429516] Killed process 9635 (thunderbird-bin)[/FONT]

```[/INDENT]

---

### Post by taurus on 2008-11-05
You can run top from a terminal to see which process(es) eats up all the memory.  

```
top
```

---

### Post by Colin@oxford on 2008-11-05
yes - but by the time I have spotted the problem, even "top" won't run.

---

