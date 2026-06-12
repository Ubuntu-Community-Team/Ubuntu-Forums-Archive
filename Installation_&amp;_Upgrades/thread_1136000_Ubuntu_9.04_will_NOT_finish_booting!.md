---
title: "Ubuntu 9.04 will NOT finish booting!"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by swiftstealth on 2009-04-24
Hey all,
I tried to load Ubuntu on my Hp Pavilion a1100n computer, and it refused to load the live CD. It kept getting stuck about a third of the way into the loading bar. XP - with it's text based installer - loaded fine, so I assumed it must have had something to do with the GUI. I downloaded the text based installer version of 9.04, and it ran perfectly. I assumed, that, like windows, after it was installed it would have no issues with running a GUI.

Mistake.

Ubuntu will NOT get past the 1/3 point in the loading bar, whether I'm booting into recovery mode or not. It stops, the Caps Lock and Scroll Lock LED's blink at me (and continue to do so until the computer is rebooted) and then it presents me with a page of text. I'll recreate it here

> 
[10.760636] [<c0193f99>] ? __alloc_pagees>internal+0xb9/0x490
[10.760636] [<c01a78a9>] ? anon_vma_prepare+0x19/0xc0
[10.760636] [<c019fa07>] ? do_anonymous_page+0x47/0x1d0
[10.760636] [<c0127453>] ? kmap_atomic_prot+0x43/0xe0
[10.760636] [<c01a1faf>] ? handle_mm_fault+0x2af/0x380
[10.760636] [<c01d4258>] ? mnt_drop_write+0x58/0x150
[10.760636] [<c050521d>] ? do_page_fault+0x1fd/0x790
[10.760636] [<c01c4b7d>] ? pipe_read+0x20d/0x3e0
[10.760636] [<c013b43f>] ? wait_noreap_copyout+0x9f/0xd0
[10.760636] [<c013cc28>] ? wait_task_zombie+0x518/0x530
[10.760636] [<c014ef78>] ? remove_wait_queue+0x38/0x50
[10.760636] [<c013cf96>] ? do_wait+0x1f6/0x320
[10.760636] [<c0133d00>] ? default_wake_function+0x0/0x10
[10.760636] [<c013d222>] ? sys_waitid+0x72/0xa0
[10.760636] [<c0505020>] ? do_page_fault+0x0/0x790
[10.760636] [<c0503082>] ? error_code+0x72/0x80
[10.760636] [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[10.760636] d3 65 f0 8b 45 f0 85 c0 7e 3b 89 d6 31 db 90 8d 74 26 00 ba 03 00 00 00 89 f0 e8 9c 3a f9 ff b9 00 04 00 00 89 45 e0 89 c7 31 c0 <f3> ab 8b 45 e0 ba 03 00 00 00 83 c3 01 83 c6 20 e8 fb 38 f9 ff
[10.760636] EIP: [<c0193160>] prep_new_page+0xb0/0x140 SS:ESP 0068:ee6bdce4
[10.760636] ---[ end trace a9113c5a35f193b7 ]---
[10.760636] note: init[1[ exited with preempt_count 1
[10.760636] Kernel panic - not syncing: Attempted to kill init!


At this point I have no choice but to restart the computer.
Help.
What is this? How can I fix it?

---

### Post by swiftstealth on 2009-04-24
Please note, this problem does not seem to be confined to Jaunty - I had the same issue (that of the status bar freezing and the GUI not loading) with my live CD's of Linux Mint (Felicia) and Ubuntu 7.04 (Feisty) - both of which run perfectly on other machines.

Another help forum mentioned that this points to a hardware defect, so I removed a stick of RAM that I suspected has issues. The Scroll Lock and Caps Lock LED's no longer blink, but it still refuses to progress beyond the loading screen.

---

### Post by Tashi on 2009-04-28
I have the same problem. I installed Ubuntu Studio 9.04 64Bit on my AMD PC. Help would be very appreciated.

---

