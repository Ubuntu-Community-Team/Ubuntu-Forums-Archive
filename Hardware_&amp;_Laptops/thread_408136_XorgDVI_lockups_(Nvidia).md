---
title: "Xorg/DVI lockups (Nvidia)"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by kidders on 2007-04-12
Hi guys,

I'm having a nasty problem that I don't really understand, so I'm not sure how to start solving it.

Basically, whenever I try to use a DVI cable to connect my graphics card to my monitor, X's CPU usage jumps up to 100% and stays there. Sometimes, I can't even persuade the process to terminate.

**Hardware details:** AMD64X2 4600+, Nvidia 8800.

I'd been happily using Nvidia's x64 1.0-9755 driver (from the website) with a VGA cable for a few weeks, but when I switched to a DVI one, the fun began. I tried simplifying xorg.conf in stages, reducing the colour depth & screen resolution, removing extensions, switching to less ambitious drivers... and then simply typing 'X', to see what would happen. Unfortunately the results are inconsistent and hard to reproduce.

[LIST]
[*]Sometimes X starts & then segfaults after a second or two after the ugly grey trellis pattern appeared.
[*]Other times, X fails to start...
[/LIST]```
(EE) NVIDIA(GPU-0): EVO Push buffer channel allocation failed
(EE)  *** Aborting ***
(EE) NVIDIA(GPU-0): Failed to allocate EVO DMA push buffer
(EE)  *** Aborting ***
(EE) NVIDIA(GPU-0): Failed to initialize EVO

Fatal server error:
AddScreen/ScreenInit failed for driver 0
```
[LIST]
[*]Most often, X just locks up. I would do the following in sequence ... sometimes the process dies ... other times I have to reset by box:
[LIST]
[*]Hit CTRL+C.
[*]Switch to another terminal and try **kill [pid]**.
[*]Get a bit more desperate and try **kill -9 [pid]** or **kill -11 [pid]**.
[*]Try renicing X (a lot) in an attempt to lower its priority.
[*]Bash my head off the desk & try a few more vain **kill**s
[/LIST]
[/LIST]
Sometimes, this happens (dmesg)...
```
[  410.819166] BUG: soft lockup detected on CPU#1!
[  410.819171] 
[  410.819172] Call Trace:
[  410.819175]  <IRQ>  [<ffffffff802bc36a>] softlockup_tick+0xfa/0x120
[  410.819203]  [<ffffffff80211c9f>] __do_softirq+0x5f/0xd0
[  410.819211]  [<ffffffff80299297>] update_process_times+0x57/0x90
[  410.819218]  [<ffffffff8027a664>] smp_local_timer_interrupt+0x34/0x60
[  410.819222]  [<ffffffff8027ade9>] smp_apic_timer_interrupt+0x59/0x80
[  410.819229]  [<ffffffff80261ce6>] apic_timer_interrupt+0x66/0x70
[  410.819232]  <EOI>  [<ffffffff803c38d0>] pci_conf1_read+0x0/0x100
[  410.819412]  [<ffffffff88450014>] :nvidia:_nv007276rm+0x43c/0x456
[  410.819518]  [<ffffffff8853ac4a>] :nvidia:_nv001523rm+0x34/0x182
[  410.819641]  [<ffffffff8845283f>] :nvidia:_nv007371rm+0xb9/0x13e
[  410.819756]  [<ffffffff883b5649>] :nvidia:_nv009588rm+0x16f/0x1a2
[  410.819876]  [<ffffffff883b985f>] :nvidia:_nv009351rm+0x1bb/0x2e4
[  410.819996]  [<ffffffff883b7d74>] :nvidia:_nv009579rm+0x96/0x470
[  410.820065]  [<ffffffff8823cf61>] :nvidia:_nv012097rm+0x65/0x100
[  410.820140]  [<ffffffff8824bc25>] :nvidia:_nv002599rm+0x215/0x29c
[  410.820218]  [<ffffffff8824bf15>] :nvidia:_nv002598rm+0x269/0x290
[  410.820298]  [<ffffffff8824b25c>] :nvidia:_nv002596rm+0xa4/0x1a2
[  410.820376]  [<ffffffff8824af60>] :nvidia:_nv002602rm+0xcc/0x2d2
[  410.820456]  [<ffffffff8824adad>] :nvidia:_nv002605rm+0xef/0x1d6
[  410.820529]  [<ffffffff8824aa86>] :nvidia:_nv002608rm+0x42/0x27a
[  410.820646]  [<ffffffff884503da>] :nvidia:_nv006972rm+0xc8/0xd8
[  410.820727]  [<ffffffff88270b23>] :nvidia:rm_set_interrupts+0x11f/0x136
[  410.820808]  [<ffffffff8826f8e8>] :nvidia:_nv002583rm+0x4a/0x7e
[  410.820887]  [<ffffffff882710b8>] :nvidia:rm_free_unused_clients+0x6e/0x9a
[  410.820983]  [<ffffffff88573659>] :nvidia:nv_kern_ctl_close+0x80/0xb6
[  410.821077]  [<ffffffff885750a2>] :nvidia:nv_kern_close+0x48/0x2e4
[  410.821089]  [<ffffffff80212345>] __fput+0xc5/0x1d0
[  410.821097]  [<ffffffff80224d21>] filp_close+0x71/0x90
[  410.821104]  [<ffffffff8023a6e7>] put_files_struct+0x87/0x110
[  410.821112]  [<ffffffff8021522a>] do_exit+0x27a/0x880
[  410.821125]  [<ffffffff8024b022>] do_group_exit+0x82/0x90
[  410.821131]  [<ffffffff8022c758>] get_signal_to_deliver+0x418/0x450
[  410.821139]  [<ffffffff8025e49a>] do_notify_resume+0xca/0x7a0
[  410.821148]  [<ffffffff802731c3>] init_fpu+0x73/0xa0
[  410.821160]  [<ffffffff8027fae8>] do_gettimeoffset_pm+0x8/0x30
[  410.821167]  [<ffffffff80270a54>] do_gettimeofday+0x44/0x90
[  410.821174]  [<ffffffff8025dda0>] getnstimeofday+0x10/0x30
[  410.821183]  [<ffffffff802611a7>] sysret_signal+0x1c/0x27
[  410.821187]  [<ffffffff80261437>] ptregscall_common+0x67/0xb0
```

Anyhow, I'm lost. :-( What's the first step?

---

