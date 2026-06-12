---
title: "WINTEL PRO W8 PRO based on z8300. r8152 NETDEV WATCHDOG"
date: 2016-11-07
forum: Hardware
---

### Post by porlockos on 2016-11-07
Hi I’m fighting with this more than a week and i lose any hope
I have WINTEL PRO W8 PRO based on z8300.
And I have a problem with Ethernet card, it dies in some strange circumstances, I always happened when I view a movie on TV over DLNA,  first I think that happened when network load is hudge but I testes with a ftp transfer and I do not died, maybe this 

was only a coincidence.  I already try a kernel   4.8 (16.10), 4.4 (16.04.1)  and 4.4. linuxium (on 4.8 linuxium it do not want to boot at all)

I tested on kernel drivers and on module (ver 2.07.0) from Realtek site, I try to run interface in halfduplex mode, and add a pcie_aspm=off and  usbcore.autosuspend=-1 to kernel bot parameters.

No luck,  Ethernet card dies and in demesg I see something like this 


Nov 05 03:14:23 wintel systemd[1]: Started dnf makecache.
Nov 05 03:14:23 wintel audit[1]: SERVICE_START pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=dnf-makecache comm="systemd" exe="/usr/lib/systemd/systemd" hostname=? addr=? terminal=? r
Nov 05 03:14:23 wintel audit[1]: SERVICE_STOP pid=1 uid=0 auid=4294967295 ses=4294967295 msg='unit=dnf-makecache comm="systemd" exe="/usr/lib/systemd/systemd" hostname=? addr=? terminal=? re
Nov 05 03:14:49 wintel kernel: r8152 1-3:1.0 enp0s20u3: Tx status -71
Nov 05 03:16:07 wintel kernel: ------------[ cut here ]------------
Nov 05 03:16:07 wintel kernel: WARNING: CPU: 0 PID: 0 at net/sched/sch_generic.c:306 dev_watchdog+0x22e/0x240()
Nov 05 03:16:07 wintel kernel: NETDEV WATCHDOG: enp0s20u3 (r8152): transmit queue 0 timed out
Nov 05 03:16:07 wintel kernel: Modules linked in: cpufreq_stats fuse ip_set nfnetlink bridge stp llc intel_rapl vfat coretemp fat kvm_intel kvm iTCO_wdt iTCO_vendor_support irqbypass crct10d
Nov 05 03:16:07 wintel kernel:  soundcore int340x_thermal_zone tpm_tis tpm acpi_pad intel_soc_dts_iosf spi_pxa2xx_platform lpc_ich xfs libcrc32c i915 i2c_algo_bit drm_kms_helper mmc_block dr
Nov 05 03:16:07 wintel kernel: CPU: 0 PID: 0 Comm: swapper/0 Tainted: G        W       4.5.5-300.fc24.x86_64 #1
Nov 05 03:16:07 wintel kernel: Hardware name: N/A CherryTrail/Type2 - Board Product Name, BIOS YT8.2x64.001 01/06/2016
Nov 05 03:16:07 wintel kernel:  0000000000000286 63f3762ca967b860 ffff880079e03da0 ffffffff813d35af
Nov 05 03:16:07 wintel kernel:  ffff880079e03de8 ffffffff81b074f0 ffff880079e03dd8 ffffffff810a5f12
Nov 05 03:16:07 wintel kernel:  0000000000000000 ffff880077786000 0000000000000000 0000000000000001
Nov 05 03:16:07 wintel kernel: Call Trace:
Nov 05 03:16:07 wintel kernel:  <IRQ>  [<ffffffff813d35af>] dump_stack+0x63/0x84
Nov 05 03:16:07 wintel kernel:  [<ffffffff810a5f12>] warn_slowpath_common+0x82/0xc0
Nov 05 03:16:07 wintel kernel:  [<ffffffff810a5fac>] warn_slowpath_fmt+0x5c/0x80
Nov 05 03:16:07 wintel kernel:  [<ffffffff816da43e>] dev_watchdog+0x22e/0x240
Nov 05 03:16:07 wintel kernel:  [<ffffffff816da210>] ? qdisc_rcu_free+0x40/0x40
Nov 05 03:16:07 wintel kernel:  [<ffffffff8110fee5>] call_timer_fn+0x35/0x120
Nov 05 03:16:07 wintel kernel:  [<ffffffff816da210>] ? qdisc_rcu_free+0x40/0x40
Nov 05 03:16:07 wintel kernel:  [<ffffffff8111052e>] run_timer_softirq+0x21e/0x2d0
Nov 05 03:16:07 wintel kernel:  [<ffffffff810aa8e2>] __do_softirq+0x112/0x2f0
Nov 05 03:16:07 wintel kernel:  [<ffffffff810aacc5>] irq_exit+0x105/0x110
Nov 05 03:16:07 wintel kernel:  [<ffffffff817d19b2>] smp_apic_timer_interrupt+0x42/0x50
Nov 05 03:16:07 wintel kernel:  [<ffffffff817cfadc>] apic_timer_interrupt+0x8c/0xa0
Nov 05 03:16:07 wintel kernel:  <EOI>  [<ffffffff81665313>] ? cpuidle_enter_state+0x113/0x2b0
Nov 05 03:16:07 wintel kernel:  [<ffffffff816654e7>] cpuidle_enter+0x17/0x20
Nov 05 03:16:07 wintel kernel:  [<ffffffff810e8b3a>] call_cpuidle+0x2a/0x40
Nov 05 03:16:07 wintel kernel:  [<ffffffff810e8f12>] cpu_startup_entry+0x2a2/0x360
Nov 05 03:16:07 wintel kernel:  [<ffffffff817c1ccc>] rest_init+0x7c/0x80
Nov 05 03:16:07 wintel kernel:  [<ffffffff81d6903f>] start_kernel+0x496/0x4b7
Nov 05 03:16:07 wintel kernel:  [<ffffffff81d68120>] ? early_idt_handler_array+0x120/0x120
Nov 05 03:16:07 wintel kernel:  [<ffffffff81d68332>] x86_64_start_reservations+0x2a/0x2c
Nov 05 03:16:07 wintel kernel:  [<ffffffff81d68480>] x86_64_start_kernel+0x14c/0x16f
Nov 05 03:16:07 wintel kernel: ---[ end trace 1e97147847271855 ]---
Nov 05 03:16:07 wintel kernel: r8152 1-3:1.0 enp0s20u3: Tx timeout
Nov 05 03:16:07 wintel kernel: r8152 1-3:1.0 enp0s20u3: Tx status -2
Nov 05 03:16:07 wintel kernel: r8152 1-3:1.0 enp0s20u3: Tx status -2
Nov 05 03:16:07 wintel kernel: r8152 1-3:1.0 enp0s20u3: Tx status -2
Nov 05 03:16:07 wintel kernel: r8152 1-3:1.0 enp0s20u3: Tx status -2
Nov 05 03:16:10 wintel kernel: usb 1-3: reset high-speed USB device number 3 using xhci_hcd
 
Im realy, relay desperate, today I go to sleep at 5 AM because of that **** ..  pls help L

---

