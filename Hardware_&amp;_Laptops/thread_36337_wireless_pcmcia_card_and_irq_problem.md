---
title: "wireless pcmcia card and irq problem?"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by Jeezis on 2005-05-22
i have been using ubuntu for about 6 months now and love it to death. currently i am running kubuntu hoary on an hp pavilion ze4420us. i've tried numerous times to get a variety of wireless cards to work on this machine and my new sager 9860-s. but, the problem:

i am using a belkin f5d6020 ver. 2
my router is completely open, no encryption or anything involved
apparently it should be supported naturally, but this hasn't been the case.
i sucessfully installed the atmel driver for it and immediately it was recognized but here is where it gets confusing.

kwifimanager shows the card has 100% signal strength
the accesspoint is unknown
the ap mac address is of course FF:00:00:00:00:00
the ip address of the card is unavailable
scans never turn up with available networks

iwconfig is as follows:
atml0     ATMEL REVE  ESSID:""
          Mode:Managed  Frequency=2.427 GHz  Access Point: FF:00:00:00:00:00
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:40  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
the control center shows that the card isnt enabled. the only way i have found to enable it is statically assigning it an ip address, but, still no connection.

this is a snip from dmesg that seems to be ultimately the problem. this only occurs when i boot with the card plugged it:
irq 3: nobody cared (try booting with the "irqpoll" option.
 [<c012e363>] __report_bad_irq+0x31/0x77
 [<c012e436>] note_interrupt+0x75/0x9b
 [<c012de1a>] __do_IRQ+0xd3/0x111
 [<c0104cc5>] do_IRQ+0x19/0x24
 [<c0103966>] common_interrupt+0x1a/0x20
 [<c0119dfc>] __do_softirq+0x2c/0x79
 [<c0119e6b>] do_softirq+0x22/0x26
 [<c012dcf0>] irq_exit+0x29/0x34
 [<c0104cca>] do_IRQ+0x1e/0x24
 [<c0103966>] common_interrupt+0x1a/0x20
 [<dcab0341>] yenta_set_socket+0xc7/0x180 [yenta_socket]
 [<dcac1b6f>] pcmcia_request_configuration+0x12c/0x357 [pcmcia_core]
 [<dcb65d5a>] vnet_config+0x412/0x4b5 [pcmf502re]
 [<c01f260f>] freed_request+0x25/0x9b
 [<c01f3d1e>] end_that_request_last+0x6d/0x81
 [<dc884903>] __ide_end_request+0xdd/0xef [ide_core]
 [<c0113217>] scheduler_tick+0x3d7/0x3df
 [<c0113217>] scheduler_tick+0x3d7/0x3df
 [<c0123af9>] rcu_process_callbacks+0x28/0x2c
 [<dcab0687>] yenta_set_mem_map+0x18d/0x1bf [yenta_socket]
 [<dcab0687>] yenta_set_mem_map+0x18d/0x1bf [yenta_socket]
 [<dcab0687>] yenta_set_mem_map+0x18d/0x1bf [yenta_socket]
 [<dcac25c2>] set_cis_map+0x7b/0xb0 [pcmcia_core]
 [<dcac26f9>] read_cis_mem+0x102/0x14c [pcmcia_core]
 [<dcac296c>] read_cis_cache+0x102/0x157 [pcmcia_core]
 [<dcac2eed>] pccard_get_next_tuple+0x82/0x1ec [pcmcia_core]
 [<dcac2ce6>] pccard_get_first_tuple+0xf7/0x104 [pcmcia_core]
 [<dcb66150>] vnet_event+0x76/0x1d1 [pcmf502re]
 [<dcac1762>] pcmcia_register_client+0x19e/0x1d0 [pcmcia_core]
 [<c01362c9>] cache_alloc_refill+0x156/0x187
 [<dcb66016>] vnet_attach+0x18e/0x1b6 [pcmf502re]
 [<dcb660da>] vnet_event+0x0/0x1d1 [pcmf502re]
 [<dcafc04f>] pcmcia_bind_device+0x4f/0x73 [pcmcia]
 [<dcafc632>] bind_request+0x172/0x1cd [pcmcia]
 [<c0112900>] recalc_task_prio+0x8a/0x133
 [<dcafd02a>] ds_ioctl+0x4b5/0x57e [pcmcia]
 [<c0210b8e>] sock_def_readable+0x2b/0x65
 [<dc85b9a0>] unix_dgram_sendmsg+0x3e5/0x482 [unix]
 [<c011299d>] recalc_task_prio+0x127/0x133
 [<c020e126>] sock_sendmsg+0xd3/0xef
 [<c015bb94>] alloc_inode+0x104/0x18a
 [<c015c4f2>] get_new_inode_fast+0x32/0xda
 [<c015c971>] iget_locked+0xbb/0xc4
 [<c015adb4>] d_instantiate+0x5a/0x60
 [<c0170878>] proc_lookup+0x77/0xa5
 [<c011418b>] __mmdrop+0x2e/0x33
 [<c013a11b>] zap_pmd_range+0x43/0x60
 [<c013a179>] unmap_page_range+0x41/0x5d
 [<c013a277>] unmap_vmas+0xe2/0x1cf
 [<c013c1de>] remove_vm_struct+0x69/0x6f
 [<c013d5bc>] unmap_vma_list+0x14/0x1f
 [<c01562ef>] sys_ioctl+0x1bb/0x1d8
 [<c0102fa1>] sysenter_past_esp+0x52/0x75
handlers:
[<dcb665a5>] (vnet_interrupt+0x0/0x8d [pcmf502re])
Disabling IRQ #3
 ](*,)  i've tried searching for ways to fix this but have come up with nothing so far. if you need any other type of information just give me a holler and i'll oblige. thanks!

---

### Post by txcountymounty on 2005-10-11
i also have the same problem with the same card my dmsg is a little different than yours i think.

[4294725.925000] irq 3: nobody cared (try booting with the "irqpoll" option.
[4294725.925000]  [<c012de13>] __report_bad_irq+0x31/0x74
[4294725.925000]  [<c012deeb>] note_interrupt+0x7d/0xa2
[4294725.925000]  [<c012da10>] __do_IRQ+0x85/0xb1
[4294725.925000]  [<c0104ca5>] do_IRQ+0x19/0x24
[4294725.925000]  [<c01038b6>] common_interrupt+0x1a/0x20
[4294725.925000]  [<c0119058>] __do_softirq+0x2c/0x7d
[4294725.925000]  [<c01190cb>] do_softirq+0x22/0x26
[4294725.925000]  [<c0104caa>] do_IRQ+0x1e/0x24
[4294725.925000]  [<c01038b6>] common_interrupt+0x1a/0x20
[4294725.925000]  [<c012dbee>] setup_irq+0x9d/0xc1
[4294725.925000]  [<dcbba164>] service_interrupt+0x0/0x262 [atmel]
[4294725.925000]  [<c012dd07>] request_irq+0x72/0x8b
[4294725.925000]  [<dcbbab62>] init_atmel_card+0x300/0x3dc [atmel]
[4294725.925000]  [<dcbba164>] service_interrupt+0x0/0x262 [atmel]
[4294725.925000]  [<dcbaf686>] atmel_config+0x501/0x62f [atmel_cs]
[4294725.925000]  [<dcbaf16e>] card_present+0x0/0x17 [atmel_cs]
[4294725.925000]  [<c0121f00>] __rcu_process_callbacks+0x7/0x97
[4294725.925000]  [<c0121fb8>] rcu_process_callbacks+0x28/0x2c
[4294725.925000]  [<dca586a2>] yenta_set_mem_map+0x196/0x1c6 [yenta_socket]
[4294725.925000]  [<dcae0235>] set_cis_map+0x76/0xab [pcmcia_core]
[4294725.925000]  [<dcae0376>] read_cis_mem+0x10c/0x15b [pcmcia_core]
[4294725.925000]  [<dcae05d1>] read_cis_cache+0xf2/0x147 [pcmcia_core]
[4294725.925000]  [<dcae0a64>] follow_link+0x168/0x178 [pcmcia_core]
[4294725.925000]  [<dcae0af2>] pccard_get_next_tuple+0x7e/0x20a [pcmcia_core]
[4294725.925000]  [<dcae08ef>] pccard_get_first_tuple+0xf6/0x103 [pcmcia_core]
[4294725.925000]  [<dc935d2d>] ext3_mark_inode_dirty+0x27/0x31 [ext3]
[4294725.925000]  [<dc9332cd>] ext3_splice_branch+0x87/0x108 [ext3]
[4294725.925000]  [<dc8e49eb>] do_get_write_access+0x35a/0x379 [jbd]
[4294725.925000]  [<c0121f00>] __rcu_process_callbacks+0x7/0x97
[4294725.925000]  [<c0121fb8>] rcu_process_callbacks+0x28/0x2c
[4294725.925000]  [<dca586a2>] yenta_set_mem_map+0x196/0x1c6 [yenta_socket]
[4294725.925000]  [<dcae0235>] set_cis_map+0x76/0xab [pcmcia_core]
[4294725.925000]  [<dcae0376>] read_cis_mem+0x10c/0x15b [pcmcia_core]
[4294725.925000]  [<dcae05d1>] read_cis_cache+0xf2/0x147 [pcmcia_core]
[4294725.925000]  [<dcae0a64>] follow_link+0x168/0x178 [pcmcia_core]
[4294725.925000]  [<dcae0af2>] pccard_get_next_tuple+0x7e/0x20a [pcmcia_core]
[4294725.925000]  [<dcae08ef>] pccard_get_first_tuple+0xf6/0x103 [pcmcia_core]
[4294725.925000]  [<dcae1d1b>] pccard_parse_tuple+0xe7/0xf8 [pcmcia_core]
[4294725.925000]  [<dcbaf8ad>] atmel_event+0x98/0x144 [atmel_cs]
[4294725.925000]  [<dcb41c8b>] pcmcia_register_client+0x242/0x262 [pcmcia]
[4294725.925000]  [<c0134ab1>] cache_alloc_refill+0x12c/0x15b
[4294725.925000]  [<dcbaf0e3>] atmel_attach+0xe3/0x10a [atmel_cs]
[4294725.925000]  [<c0175aed>] sysfs_add_link+0x7b/0x9d
[4294725.925000]  [<dcbaf815>] atmel_event+0x0/0x144 [atmel_cs]
[4294725.925000]  [<dcb4122c>] pcmcia_device_probe+0x47/0x9c [pcmcia]
[4294725.925000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4294725.925000]  [<c01ec04c>] device_attach+0x48/0x81
[4294725.925000]  [<c01ec4cd>] bus_rescan_devices_helper+0x15/0x20
[4294725.925000]  [<c01ebe6b>] __bus_for_each_dev+0x4f/0x76
[4294725.925000]  [<c01ec502>] bus_rescan_devices+0x2a/0x3b
[4294725.925000]  [<c01ec4b8>] bus_rescan_devices_helper+0x0/0x20
[4294725.925000]  [<dcb419ef>] bind_request+0x104/0x15e [pcmcia]
[4294725.925000]  [<dcb42627>] ds_ioctl+0x4e2/0x5c1 [pcmcia]
[4294725.925000]  [<c0152fd8>] do_ioctl+0x48/0x4e
[4294725.925000]  [<c0153233>] vfs_ioctl+0x172/0x17f
[4294725.925000]  [<c0153286>] sys_ioctl+0x46/0x60
[4294725.925000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4294725.925000] handlers:
[4294725.925000] [<dcbba164>] (service_interrupt+0x0/0x262 [atmel])
[4294725.925000] Disabling IRQ #3
[4294726.441000] eth1: MAC address 00:30:bd:d1:f5:b2
[4294726.441000] eth1: Atmel at76c50x wireless. Version 0.96 [email]simon@thekelleys.org.uk[/email]
[4294726.441000] eth1: Belkin F5D6020-V2 index 0x01: Vcc 5.0, irq 3, io 0x0100-0x011f
[4294726.988000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294726.993000] Detected 1987.682 MHz processor.
[4294727.000000] powernow: No PST tables match this cpuid (0x7a0)
[4294727.000000] powernow: This is indicative of a broken BIOS.
[4294727.000000] powernow: Trying ACPI perflib
[4294727.000000] powernow: Minimum speed 530 MHz. Maximem speed 1987 MHz.
[4294727.381000] Bluetooth: Core ver 2.7
[4294727.381000] NET: Registered protocol family 31
[4294727.381000] Bluetooth: HCI device and connection manager initialized
[4294727.381000] Bluetooth: HCI socket layer initialized
[4294727.555000] Bluetooth: L2CAP ver 2.7
[4294727.555000] Bluetooth: L2CAP socket layer initialized
[4294727.607000] Bluetooth: RFCOMM ver 1.5
[4294727.607000] Bluetooth: RFCOMM sosket layer initialized
[4294727.607000] Bluetooth: RFCOMM TTY layer initialized
[4294737.632000] eth1: no IPv6 routers present

---

