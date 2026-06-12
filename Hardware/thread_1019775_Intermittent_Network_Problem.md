---
title: "Intermittent Network Problem"
date: 2008-12-23
forum: Hardware
---

### Post by victorbrca on 2008-12-23
Hi all,


  Installing a new PC with two network cards and am having network connection problem. I loose connection from the server for a few minutes (5) and then it comes back. This happens even when only one NIC is enabled (the second is not even in use right now). 

  I'm guessing it might be an IRQ problem. Any ideas?


**/var/log/messages**
```
Dec 22 21:52:07 enterprise kernel: [ 8325.021304] ------------[ cut here ]------------
Dec 22 21:52:07 enterprise kernel: [ 8325.021311] WARNING: at /build/buildd/linux-2.6.27/net/sched/sch_generic.c:219 dev_watchdog+0x272/0x280()
Dec 22 21:52:07 enterprise kernel: [ 8325.021314] NETDEV WATCHDOG: eth0 (r8169): transmit timed out
Dec 22 21:52:07 enterprise kernel: [ 8325.021316] Modules linked in: vmnet vmci vmmon ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp bridge stp kvm ppdev ipv6 iptable_filter ip_tables x_tables ac lp loop evdev snd_hda_intel pcspkr snd_pcm snd_timer snd parport_pc soundcore parport iTCO_wdt iTCO_vendor_support snd_page_alloc intel_agp shpchp pci_hotplug button ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif ata_generic sg 8139cp pata_jmicron ata_piix 8139too pata_cmd64x pata_acpi mii libata r8169 scsi_mod dock ehci_hcd uhci_hcd usbcore raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod dm_mirror dm_log dm_snapshot dm_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse [last unloaded: kvm_intel]
Dec 22 21:52:07 enterprise kernel: [ 8325.021387] Pid: 0, comm: swapper Not tainted 2.6.27-7-server #1
Dec 22 21:52:07 enterprise kernel: [ 8325.021389] 
Dec 22 21:52:07 enterprise kernel: [ 8325.021389] Call Trace:
Dec 22 21:52:07 enterprise kernel: [ 8325.021391]  <IRQ>  [<ffffffff8024e91c>] warn_slowpath+0xbc/0xf0
Dec 22 21:52:07 enterprise kernel: [ 8325.021400]  [<ffffffff802473ee>] ? try_to_wake_up+0x11e/0x2e0
Dec 22 21:52:07 enterprise kernel: [ 8325.021404]  [<ffffffff803198d2>] ? bio_free+0x52/0x60
Dec 22 21:52:07 enterprise kernel: [ 8325.021408]  [<ffffffff802475bd>] ? default_wake_function+0xd/0x10
Dec 22 21:52:07 enterprise kernel: [ 8325.021412]  [<ffffffff802e1de0>] ? __slab_free+0x10/0x120
Dec 22 21:52:07 enterprise kernel: [ 8325.021428]  [<ffffffffa0137fe1>] ? scsi_pool_free_command+0x51/0x60 [scsi_mod]
Dec 22 21:52:07 enterprise kernel: [ 8325.021433]  [<ffffffff8039b8f9>] ? deadline_queue_empty+0x9/0x40
Dec 22 21:52:07 enterprise kernel: [ 8325.021437]  [<ffffffff8038e37a>] ? elv_queue_empty+0x3a/0x50
Dec 22 21:52:07 enterprise kernel: [ 8325.021440]  [<ffffffff80392c5f>] ? blk_run_queue+0x3f/0x50
Dec 22 21:52:07 enterprise kernel: [ 8325.021444]  [<ffffffff80219d26>] ? read_tsc+0x16/0x40
Dec 22 21:52:07 enterprise kernel: [ 8325.021448]  [<ffffffff80273f44>] ? timer_stats_update_stats+0x24/0x370
Dec 22 21:52:07 enterprise kernel: [ 8325.021457]  [<ffffffff8026e491>] ? getnstimeofday+0x51/0xd0
Dec 22 21:52:07 enterprise kernel: [ 8325.021460]  [<ffffffff803a85fa>] ? strlcpy+0x4a/0x60
Dec 22 21:52:07 enterprise kernel: [ 8325.021462]  [<ffffffff80253e69>] ? set_normalized_timespec+0x9/0x90
Dec 22 21:52:07 enterprise kernel: [ 8325.021464]  [<ffffffff8047b452>] dev_watchdog+0x272/0x280
Dec 22 21:52:07 enterprise kernel: [ 8325.021466]  [<ffffffff8026ce9c>] ? sched_clock_cpu+0xcc/0x160
Dec 22 21:52:07 enterprise kernel: [ 8325.021468]  [<ffffffff80219d26>] ? read_tsc+0x16/0x40
Dec 22 21:52:07 enterprise kernel: [ 8325.021470]  [<ffffffff8047b1e0>] ? dev_watchdog+0x0/0x280
Dec 22 21:52:07 enterprise kernel: [ 8325.021472]  [<ffffffff80259f79>] run_timer_softirq+0x179/0x260
Dec 22 21:52:07 enterprise kernel: [ 8325.021476]  [<ffffffff80271704>] ? clockevents_program_event+0x54/0xa0
Dec 22 21:52:07 enterprise kernel: [ 8325.021478]  [<ffffffff80254d1c>] __do_softirq+0x8c/0x100
Dec 22 21:52:07 enterprise kernel: [ 8325.021481]  [<ffffffff8021417c>] call_softirq+0x1c/0x30
Dec 22 21:52:07 enterprise kernel: [ 8325.021483]  [<ffffffff80215875>] do_softirq+0x65/0xa0
Dec 22 21:52:07 enterprise kernel: [ 8325.021485]  [<ffffffff80254a85>] irq_exit+0x95/0xa0
Dec 22 21:52:07 enterprise kernel: [ 8325.021488]  [<ffffffff80226909>] smp_apic_timer_interrupt+0x89/0xc0
Dec 22 21:52:07 enterprise kernel: [ 8325.021490]  [<ffffffff80213983>] apic_timer_interrupt+0x83/0x90
Dec 22 21:52:07 enterprise kernel: [ 8325.021491]  <EOI>  [<ffffffff8021ab82>] ? mwait_idle+0x52/0x60
Dec 22 21:52:07 enterprise kernel: [ 8325.021495]  [<ffffffff8021ab39>] ? mwait_idle+0x9/0x60
Dec 22 21:52:07 enterprise kernel: [ 8325.021498]  [<ffffffff80210e95>] ? cpu_idle+0x75/0x110
Dec 22 21:52:07 enterprise kernel: [ 8325.021500]  [<ffffffff804fd205>] ? start_secondary+0x97/0xc2
Dec 22 21:52:07 enterprise kernel: [ 8325.021502] 
Dec 22 21:52:07 enterprise kernel: [ 8325.021503] ---[ end trace 32564b7b4519213d ]---
Dec 22 21:52:07 enterprise kernel: [ 8325.050641] r8169: eth0: link up
```


**syslog**
```
$ tail -n 1000 syslog | grep eth0
Dec 20 13:17:14 enterprise kernel: [ 2888.207096] device eth0 entered promiscuous mode
Dec 20 13:17:14 enterprise kernel: [ 2888.207101] bridge-eth0: enabled promiscuous mode
Dec 20 14:10:31 enterprise kernel: [ 6085.803169] device eth0 left promiscuous mode
Dec 20 14:10:31 enterprise kernel: [ 6085.803184] bridge-eth0: disabled promiscuous mode
Dec 20 14:10:32 enterprise kernel: [ 6086.201079] device eth0 entered promiscuous mode
Dec 20 14:10:32 enterprise kernel: [ 6086.201083] bridge-eth0: enabled promiscuous mode
Dec 20 14:11:02 enterprise kernel: [ 6115.913185] device eth0 left promiscuous mode
Dec 20 14:11:02 enterprise kernel: [ 6115.913201] bridge-eth0: disabled promiscuous mode
Dec 20 14:11:02 enterprise kernel: [ 6116.244791] device eth0 entered promiscuous mode
Dec 20 14:11:02 enterprise kernel: [ 6116.244796] bridge-eth0: enabled promiscuous mode
Dec 20 14:39:04 enterprise kernel: [ 7798.011292] NETDEV WATCHDOG: eth0 (r8169): transmit timed out
Dec 20 14:39:04 enterprise kernel: [ 7798.051931] r8169: eth0: link up
Dec 20 16:47:46 enterprise kernel: [15520.051918] r8169: eth0: link up
Dec 20 16:52:56 enterprise kernel: [15830.440176] device eth0 left promiscuous mode
Dec 20 16:52:56 enterprise kernel: [15830.440185] bridge-eth0: disabled promiscuous mode
Dec 20 17:38:53 enterprise kernel: [18587.591336] bridge-eth0: disabling the bridge
Dec 20 17:38:53 enterprise vmnetBridge: Stopped bridge eth0 to virtual network 0. 
Dec 20 17:38:53 enterprise kernel: [18587.622527] bridge-eth0: down
Dec 20 17:38:53 enterprise kernel: [18587.622539] bridge-eth0: detached
Dec 20 17:39:01 enterprise avahi-daemon[4565]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.13.15.8.
Dec 22 19:33:40 enterprise kernel: [    4.411383] eth0: RTL8168b/8111b at 0xffffc20000638000, 00:1f:d0:5d:12:6a, XID 38000000 IRQ 2300
Dec 22 19:33:40 enterprise kernel: [   14.608659] r8169: eth0: link up
Dec 22 19:33:40 enterprise kernel: [   14.608668] r8169: eth0: link up
Dec 22 19:33:40 enterprise avahi-daemon[4576]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.13.15.8.
Dec 22 19:33:40 enterprise avahi-daemon[4576]: New relevant interface eth0.IPv4 for mDNS.
Dec 22 19:33:40 enterprise avahi-daemon[4576]: Registering new address record for fe80::21f:d0ff:fe5d:126a on eth0.*.
Dec 22 19:33:40 enterprise avahi-daemon[4576]: Registering new address record for 10.13.15.8 on eth0.IPv4.
Dec 22 19:33:46 enterprise vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00011043 
Dec 22 19:33:46 enterprise kernel: [   24.405737] bridge-eth0: up
Dec 22 19:33:46 enterprise kernel: [   24.405742] bridge-eth0: attached
Dec 22 19:33:46 enterprise vmnetBridge: Started bridge eth0 to virtual network 0. 
Dec 22 19:33:47 enterprise kernel: [   25.382526] eth0: no IPv6 routers present
Dec 22 19:56:40 enterprise kernel: [ 1398.054744] device eth0 entered promiscuous mode
Dec 22 19:56:40 enterprise kernel: [ 1398.054749] bridge-eth0: enabled promiscuous mode
Dec 22 21:52:07 enterprise kernel: [ 8325.021314] NETDEV WATCHDOG: eth0 (r8169): transmit timed out
Dec 22 21:52:07 enterprise kernel: [ 8325.050641] r8169: eth0: link up
```


**/proc/interrupts**
```
$ cat /proc/interrupts 
           CPU0       CPU1       CPU2       CPU3       
  0:         51          8          4         12   IO-APIC-edge      timer
  1:         52         47         49         48   IO-APIC-edge      i8042
  4:          1          4          3          0   IO-APIC-edge    
  7:          0          0          0          0   IO-APIC-edge      parport0
  8:      37117      37211      37183      37105   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 14:      21638      21683      21852      21798   IO-APIC-edge      ata_piix
 15:      21924      21811      21662      21787   IO-APIC-edge      ata_piix
 16:          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb1
 18:          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb3, ehci_hcd:usb4, uhci_hcd:usb7
 19:      29862      29906      29859      29708   IO-APIC-fasteoi   uhci_hcd:usb6, pata_cmd64x, ata_piix, pata_jmicron
 21:          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 22:         31         29         30         31   IO-APIC-fasteoi   HDA Intel
 23:          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb8
2300:     105549     105482     105539     105692   PCI-MSI-edge      eth0
NMI:          0          0          0          0   Non-maskable interrupts
LOC:     561380     498363     618124     569180   Local timer interrupts
RES:       6299       7235       5826       5985   Rescheduling interrupts
CAL:      49923      36023      35410      48095   function call interrupts
TLB:      15980      13455      11969      13923   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
SPU:          0          0          0          0   Spurious interrupts
```


Thanks!

Vic.

---

### Post by victorbrca on 2009-01-26
Problem has been solved. Apparently module r8169 has been having problems with my nic (see bellow) since Gutsy. I installed r8168 from Realtek's site and removed r8169 module about two days ago. Haven't had any problem since.

> Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


Vic.

---

