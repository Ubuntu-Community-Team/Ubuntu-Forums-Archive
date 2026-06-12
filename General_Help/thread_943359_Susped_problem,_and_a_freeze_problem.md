---
title: "Susped problem, and a freeze problem"
date: 2008-10-10
forum: General Help
---

### Post by The-herod on 2008-10-10
Hello,

I can't suspend my computer. I found this in /var/log/messages:
```
Oct 10 05:01:23 gal gnome-power-manager: (gal) Suspending computer. Reason: System idle.
Oct 10 05:01:26 gal gnome-power-manager: (gal) cannot suspend as not allowed from policy
Oct 10 05:15:12 gal -- MARK --
Oct 10 05:29:58 gal gnome-power-manager: (gal) Resuming computer
Oct 10 05:50:12 gal kernel: [20350.653316] ACPI: PCI interrupt for device 0000:00:0a.0 disabled
Oct 10 05:51:53 gal kernel: [20445.596131] ACPI: PCI interrupt for device 0000:01:07.0 disabled
Oct 10 06:00:09 gal kernel: [20920.972432] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
Oct 10 06:00:09 gal kernel: [20920.972438] swsusp: Basic memory bitmaps created
Oct 10 06:00:24 gal kernel: [20920.972440] Syncing filesystems ... done.
Oct 10 06:00:29 gal kernel: [20924.943375] Freezing user space processes ... (elapsed 3.33 seconds) done.
Oct 10 06:00:37 gal kernel: [20928.278033] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Oct 10 06:00:39 gal kernel: [20928.278074] Shrinking memory...  ^H-<7>PM: Image restored successfully.
Oct 10 06:00:40 gal kernel: [20934.527806] Restarting tasks ... done.
Oct 10 06:00:40 gal kernel: [20934.529605] swsusp: Basic memory bitmaps freed
```

Maybe someone know what does it mean, "not allowed from policy"? Also, perhaps the lower part has something to do with the freezing problem ("Freezing remaining freezable tasks"...)

At morning, the computer still worked, the Caps Lock led was lighting, but the screen got no signal, and the computer didn't respond to anything, so I had to reboot.

this is the last messages before the reboot:```

Oct 10 08:58:40 gal kernel: [31500.188132] Mem-info:
Oct 10 08:58:40 gal kernel: [31500.188133] Node 0 DMA per-cpu:
Oct 10 08:58:40 gal kernel: [31500.188136] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Oct 10 08:58:40 gal kernel: [31500.188138] Node 0 DMA32 per-cpu:
Oct 10 08:58:40 gal kernel: [31500.188141] CPU    0: Hot: hi:  186, btch:  31 usd:  80   Cold: hi:   62, btch:  15 usd:  56
Oct 10 08:58:40 gal kernel: [31500.188144] Active:192487 inactive:27829 dirty:0 writeback:0 unstable:0
Oct 10 08:58:40 gal kernel: [31500.188145]  free:2051 slab:10733 mapped:2250 pagetables:6345 bounce:0
Oct 10 08:58:40 gal kernel: [31500.188147] Node 0 DMA free:4008kB min:40kB low:48kB high:60kB active:3224kB inactive:3228kB present:10896kB pages_scanned:10620 all_unreclaimable? yes
Oct 10 08:58:40 gal kernel: [31500.188151] lowmem_reserve[]: 0 994 994 994
Oct 10 08:58:40 gal kernel: [31500.188153] Node 0 DMA32 free:4196kB min:4012kB low:5012kB high:6016kB active:766724kB inactive:108088kB present:1018020kB pages_scanned:1798241 all_unreclaimable? yes
Oct 10 08:58:40 gal kernel: [31500.188158] lowmem_reserve[]: 0 0 0 0
Oct 10 08:58:40 gal kernel: [31500.188159] Node 0 DMA: 0*4kB 1*8kB 0*16kB 1*32kB 0*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4008kB
Oct 10 08:58:40 gal kernel: [31500.188166] Node 0 DMA32: 99*4kB 3*8kB 2*16kB 1*32kB 2*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4196kB
Oct 10 08:58:40 gal kernel: [31500.188173] Swap cache: add 576276, delete 576276, find 82558/119899, race 0+159
Oct 10 08:58:40 gal kernel: [31500.188174] Free swap  = 0kB
Oct 10 08:58:40 gal kernel: [31500.188175] Total swap = 995988kB
Oct 10 08:58:40 gal kernel: [31500.188176] Free swap:            0kB
Oct 10 08:58:40 gal kernel: [31500.196548] 262128 pages of RAM
Oct 10 08:58:40 gal kernel: [31500.196550] 13589 reserved pages
Oct 10 08:58:40 gal kernel: [31500.196551] 1543 pages shared
Oct 10 08:58:40 gal kernel: [31500.196552] 0 pages swap cached
```

Any idea...?

Thanks!

---

### Post by milasch on 2008-10-10
Well, at least you seem to get to suspend or something similar to it...

If I try to suspend, my computer closes gnome, blinks the 3 lights from the keyboard, turns of the HD, but doesn't go to suspend mode, stays on... So I have to reset in order to use it again.

I've tried to suspend with a number of distros but I believe the kernel doesn't support it on my hardware.

---

### Post by Glucklich on 2008-10-10
Are you using any Hardware controller for your graphics card? If so, try to uninstall it and reboot. If it doesn't happen again that's the problem, if it happens again that's not the problem. I was experiencing freezes and monitor image distortions, banged my head in the wall for weeks about it but after uninstalling that they were gone. It's a nVidia driver thing known since 2006 but still isn't fixed.

---

### Post by The-herod on 2008-10-12
Thanks! (sorry for the late response, there has been a holiday here)

When I try to hibernate with the package ("hibernate") I installed, I get the same thing as you. No image, no HD, but the computer is on and the three LEDs are blinking.

I'm using an ATI graphics controller (fglrx), can it be the source of the problem of freeze? (I understand the problem is with nVidia...)
By the way, for a long time (a few months) the computer was fine (couldn't hibernate... but it didn't freeze). Only last week the problems started. Perhaps it has something to do with an upgrade of something...

One more problem I noticed. If I log in to the desktop, and while it's loading, I move to tty1 (Ctrl+Alt+F1), and after it returns the the graphical desktop (Ctrl+Alt+F7), everything get stuck and I have to reset. Should I open a bug thread somewhere?

Thanks!

---

