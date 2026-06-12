---
title: "Ubuntu 10.4 - Amilo D series eth0 problem"
date: 2010-07-10
forum: Hardware
---

### Post by strozzino on 2010-07-10
Hi all,
I've got some problem with my Amilo D series.
I cannot use the network connection. Here you can find the dmesg output ...
I never seen this before this kind of problem. What can be?

Thank you,
Lorenzo


```
[   33.720010] eth0: no IPv6 routers present
[   66.816014] ------------[ cut here ]------------
[   66.816031] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x1fe/0x210()
[   66.816035] Hardware name: Amilo D Series
[   66.816038] NETDEV WATCHDOG: eth0 (sis900): transmit queue 0 timed out
[   66.816041] Modules linked in: binfmt_misc joydev fbcon tileblit font bitblit softcursor snd_intel8x0 snd_ac97_codec ac97_bus vga16fb vgastate snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy pcmcia snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device radeon ttm p54pci snd p54common drm_kms_helper ppdev led_class mac80211 yenta_socket rsrc_nonstatic drm soundcore i2c_algo_bit sis_agp irda crc_ccitt video output parport_pc lp cfg80211 psmouse serio_raw snd_page_alloc pcmcia_core i2c_sis96x shpchp agpgart parport usbhid ohci1394 hid sis900 mii ieee1394
[   66.816109] Pid: 0, comm: swapper Not tainted 2.6.32-23-generic #37-Ubuntu
[   66.816112] Call Trace:
[   66.816122]  [<c014c492>] warn_slowpath_common+0x72/0xa0
[   66.816126]  [<c04d8dce>] ? dev_watchdog+0x1fe/0x210
[   66.816130]  [<c04d8dce>] ? dev_watchdog+0x1fe/0x210
[   66.816134]  [<c014c50b>] warn_slowpath_fmt+0x2b/0x30
[   66.816138]  [<c04d8dce>] dev_watchdog+0x1fe/0x210
[   66.816145]  [<c0163a40>] ? insert_work+0x60/0xb0
[   66.816151]  [<c012a498>] ? default_spin_lock_flags+0x8/0x10
[   66.816156]  [<c058c22f>] ? _spin_lock_irqsave+0x2f/0x50
[   66.816161]  [<c0163d06>] ? __queue_work+0x36/0x50
[   66.816165]  [<c015b6fe>] run_timer_softirq+0x13e/0x2c0
[   66.816171]  [<c01768d4>] ? tick_dev_program_event+0x74/0xd0
[   66.816176]  [<c04d8bd0>] ? dev_watchdog+0x0/0x210
[   66.816180]  [<c0153128>] __do_softirq+0x98/0x1b0
[   66.816184]  [<c0153285>] do_softirq+0x45/0x50
[   66.816188]  [<c01533d5>] irq_exit+0x65/0x70
[   66.816192]  [<c059076c>] smp_apic_timer_interrupt+0x5c/0x8b
[   66.816196]  [<c058a19c>] ? schedule+0x44c/0x840
[   66.816201]  [<c0103df1>] apic_timer_interrupt+0x31/0x40
[   66.816206]  [<c010aaa5>] ? mwait_idle+0x55/0xa0
[   66.816209]  [<c01021d4>] cpu_idle+0x94/0xd0
[   66.816215]  [<c0579c78>] rest_init+0x58/0x60
[   66.816222]  [<c07a38ec>] start_kernel+0x351/0x357
[   66.816226]  [<c07a33c7>] ? unknown_bootoption+0x0/0x19e
[   66.816231]  [<c07a30aa>] i386_start_kernel+0xaa/0xb1
[   66.816234] ---[ end trace 42cca1fed61d8d89 ]---
[   66.816239] eth0: Transmit timeout, status 00000004 00000241 
[   74.816031] eth0: Transmit timeout, status 00000004 00000241 
[   82.816016] eth0: Transmit timeout, status 00000004 00000241 
[   90.816017] eth0: Transmit timeout, status 00000004 00000249 
[   98.816036] eth0: Transmit timeout, status 00000004 00000249 
[  106.816023] eth0: Transmit timeout, status 00000004 00000249 
[  114.816029] eth0: Transmit timeout, status 00000004 00000241 
[  122.816025] eth0: Transmit timeout, status 00000004 00000241 
[  130.816037] eth0: Transmit timeout, status 00000004 00000241 
[  138.816035] eth0: Transmit timeout, status 00000004 00000241 
[  146.816023] eth0: Transmit timeout, status 00000004 00000241 
[  154.816026] eth0: Transmit timeout, status 00000004 00000249 
[  162.816025] eth0: Transmit timeout, status 00000000 00000259 
[  170.816022] eth0: Transmit timeout, status 00000000 00000240 
[  178.816028] eth0: Transmit timeout, status 00000000 00000240 
[  186.816029] eth0: Transmit timeout, status 00000000 00000240 
[  194.816030] eth0: Transmit timeout, status 00000000 00000240 
[  202.816027] eth0: Transmit timeout, status 00000000 00000240 
[  210.816026] eth0: Transmit timeout, status 00000000 00000240 
[  218.816031] eth0: Transmit timeout, status 00000000 00000240 
[  226.816025] eth0: Transmit timeout, status 00000000 00000240 
[  234.816031] eth0: Transmit timeout, status 00000000 00000240 
[  242.816030] eth0: Transmit timeout, status 00000000 00000240 
[  250.816023] eth0: Transmit timeout, status 00000000 00000240 
[  258.816029] eth0: Transmit timeout, status 00000000 00000240 
[  266.816017] eth0: Transmit timeout, status 00000000 00000240 
[  274.816027] eth0: Transmit timeout, status 00000000 00000240 
[  282.816027] eth0: Transmit timeout, status 00000000 00000240 
[  290.816026] eth0: Transmit timeout, status 00000000 00000260 
[  298.816032] eth0: Transmit timeout, status 00000000 00000260 
[  302.820042] eth0: Transmit timeout, status 00000000 00000260 
[  307.000026] eth0: Transmit timeout, status 00000000 00000260 
[  315.000024] eth0: Transmit timeout, status 00000000 00000260 
[  323.000023] eth0: Transmit timeout, status 00000000 00000260 
[  331.000024] eth0: Transmit timeout, status 00000000 00000260 
[  339.000026] eth0: Transmit timeout, status 00000000 00000260 
[  347.000025] eth0: Transmit timeout, status 00000000 00000260 
[  355.000022] eth0: Transmit timeout, status 00000000 00000260 
[  363.000023] eth0: Transmit timeout, status 00000000 00000260 
[  371.000023] eth0: Transmit timeout, status 00000000 00000260 
[  379.000033] eth0: Transmit timeout, status 00000000 00000260
```

---

### Post by strozzino on 2010-07-10
The problem was solved disabling apic on boot....

---

