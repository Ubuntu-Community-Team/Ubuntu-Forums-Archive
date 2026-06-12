---
title: "Determining the cause of this Hardware Error kernel panic"
date: 2013-09-12
forum: Hardware
---

### Post by martini3 on 2013-09-12
Ubuntu 12.04LTS server
I have had a number of kernel panics recently.  Here is the error I get on the console.  How do I determine what hardware is causing the error?

    [Hardware Error]: CPU:2   MC0_STATUS[-|UE|-|-|AddrV|UECC]: 0xb400200055000145
    [Hardware Error]: MC0_ADDR: 0x0000000164fe77b0
    [Hardware Error]: Data Cache Error: Data/Tag DWR error.
    [Hardware Error]: cache level: L1, tx: DATA, mem-tx: DWR
    [Hardware Error]: CPU:3 MC0_STATUS[-|UE|-|PCC|AddrV|CECC]: 0xb66b400000000135
    [Hardware Error]: MC0_ADDR: 0x0000000164fe77b0
    [Hardware Error]: Data Cache Error: Data/Tag DWD error.
    [Hardware Error]: cache level: L1, tx: DATA, mem-tx: DRD
    [Hardware Error]: CPU 3: Machine Check Exception: 4 Bank 0: b66b400000000135
    [Hardware Error]: TSC bc02bd350de4 ADDR 164fe7bb0
    [Hardware Error]: PROCESSOR 2:100f42 TIME 1378965147 SOCKET 0 APIC 3 microcode 10000c6
    [Hardware Error]: CPU:3 MC0_STATUS[-|UE|-|PCC|AddrV|CECC]: 0xb66b400000000135
    [Hardware Error]: MC0_ADDR: 0x0000000164fe77b0
    [Hardware Error]: Data Cache Error: Data/Tag DWD error.
    [Hardware Error]: cache level: L1, tx: DATA, mem-tx: DRD
    [Hardware Error]: Machine Check: Invalid
    Kernel panic - not syncing: Fatal machine check on current CPU
    Shutting down cpus with NMI

    kernel: [58495.948100] ------------[ cut here ]------------
    kernel: [58495.948108] WARNING: at /build/buildd/linux-lts-quantal-3.5.0/net/sched/sch_generic.c:255 dev_watchdog+0x272/0x280()
    kernel: [58495.948109] Hardware name: MS-7576
    kernel: [58495.948110] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
    kernel: [58495.948111] Modules linked in: nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc xfs vesafb radeon ttm drm_kms_helper snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel drm snd_hda_codec wmi i2c_algo_bit snd_hwdep snd_pcm snd_timer snd soundcore snd_page_alloc lp shpchp r8169 sp5100_tco i2c_piix4 firewire_ohci parport firewire_core kvm_amd edac_core k10temp edac_mce_amd serio_raw kvm mac_hid microcode crc_itu_t raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid1 raid0 multipath linear pata_atiixp
    kernel: [58495.948136] Pid: 0, comm: swapper/3 Tainted: G   M         3.5.0-23-generic #35~precise1-Ubuntu
    kernel: [58495.948137] Call Trace:
    kernel: [58495.948138]  <IRQ>  [<ffffffff81052c9f>] warn_slowpath_common+0x7f/0xc0
    kernel: [58495.948144]  [<ffffffff81052d96>] warn_slowpath_fmt+0x46/0x50
    kernel: [58495.948146]  [<ffffffff815a05b2>] dev_watchdog+0x272/0x280
    kernel: [58495.948149]  [<ffffffff8101be03>] ? native_sched_clock+0x13/0x80
    kernel: [58495.948151]  [<ffffffff810702d0>] ? __queue_work+0x330/0x330
    kernel: [58495.948153]  [<ffffffff815a0340>] ? pfifo_fast_dequeue+0xe0/0xe0
    kernel: [58495.948154]  [<ffffffff815a0340>] ? pfifo_fast_dequeue+0xe0/0xe0
    kernel: [58495.948156]  [<ffffffff81062ce6>] call_timer_fn+0x46/0x160
    kernel: [58495.948158]  [<ffffffff815a0340>] ? pfifo_fast_dequeue+0xe0/0xe0
    kernel: [58495.948159]  [<ffffffff81064632>] run_timer_softirq+0x132/0x2a0
    kernel: [58495.948162]  [<ffffffff810a4105>] ? ktime_get+0x65/0xe0
    kernel: [58495.948164]  [<ffffffff8105ba88>] __do_softirq+0xa8/0x210
    kernel: [58495.948166]  [<ffffffff810ab264>] ? tick_program_event+0x24/0x30
    kernel: [58495.948168]  [<ffffffff816a841c>] call_softirq+0x1c/0x30
    kernel: [58495.948170]  [<ffffffff81016245>] do_softirq+0x65/0xa0
    kernel: [58495.948172]  [<ffffffff8105be6e>] irq_exit+0x8e/0xb0
    kernel: [58495.948174]  [<ffffffff816a8d5e>] smp_apic_timer_interrupt+0x6e/0x99
    kernel: [58495.948176]  [<ffffffff816a7aca>] apic_timer_interrupt+0x6a/0x70
    kernel: [58495.948177]  <EOI>  [<ffffffff8103ff56>] ? native_safe_halt+0x6/0x10
    kernel: [58495.948180]  [<ffffffff8101c993>] default_idle+0x53/0x1f0
    kernel: [58495.948182]  [<ffffffff8101d8a9>] cpu_idle+0xd9/0x120
    kernel: [58495.948184]  [<ffffffff8167b237>] start_secondary+0xc3/0xc5
    kernel: [58495.948185] ---[ end trace ef52dc6dad6ceea1 ]---

---

### Post by tgalati4 on 2013-09-12
NMI's are non-maskable interrupts.  These are errors that are not listed, nor handled well by the CPU/BIOS, resulting in a halt instruction.  With a CPU3 error, I assume you have a quad core processor (CPU0,1,2,3).  I also assume that the onboard cache is two-way associative, which means that the CPU's share the cache from a common pool.  It looks like you have some L1 cache communication issues between the CPU's.

Has this server been running for a while?  If so, pull it apart, clean it thoroughly with compressed air and reseat the CPU's, new heat paste, and reseat the RAM.  Unfortunately, this looks like a failed CPU, since the L1 cache is normally on the die that is shared with all 4 CPU's.  There is no way to repair this.  There may be an instruction or utility to turn off cache to isolate it, but that won't fix it.

Can you run memtest?

---

### Post by martini3 on 2013-09-12
My RAID array is rebuilding (after the crash) and I don't want to interrupt it.  Once it completes I will run the memtest.
Thanks for the info.

---

### Post by martini3 on 2013-09-16
The memtest86+ results said that the memory had no errors. 

Due to the critical nature of this server, I replaced the CPU (and motherboard).

So I never really resolved this.

---

### Post by tgalati4 on 2013-09-16
Build another machine with scrap parts and test it.  I bet you will find some hardware issues.  Thankfully, you were able to rebuild your RAID.

---

