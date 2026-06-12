---
title: "Weird issues with raid5 (mdadm)"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by deebo32 on 2007-09-23
ok i had a raid0 with mdadm that worked nicely, i bought two more disks and decided to change to raid5

it worked fine for some hours, then kernel panic and boom the whole system goes down the drain

it said something about interrupts etc [http://funkiest.net/~globe/panic.jpg](http://funkiest.net/~globe/panic.jpg)

so i fiddled around bios to look for answers and noticed that i had "plug and play bios: off", i turned it on and turned off other useless stuff i dont need (sound, parallel, serial etc etc) and booted back to linux and left it to run for the night to see if this happens again

it didnt

so i reassembled my raid5, mounted it, started moving stuff to it and then this happens:

```
[34726.252370] irq 11: nobody cared (try booting with the "irqpoll" option)
[34726.252490]  [<c0154334>] __report_bad_irq+0x24/0x80
[34726.252508]  [<c01545ee>] note_interrupt+0x25e/0x290
[34726.252514]  [<e08d806c>] ata_altstatus+0x1c/0x30 [libata]
[34726.252566]  [<e08f1f32>] usb_hcd_irq+0x22/0x60 [usbcore]
[34726.252612]  [<c0153860>] handle_IRQ_event+0x30/0x60
[34726.252619]  [<c0154f21>] handle_fasteoi_irq+0xc1/0xf0
[34726.252626]  [<c0105b70>] do_IRQ+0x40/0x80
[34726.252636]  [<c0104233>] common_interrupt+0x23/0x30
[34726.252646]  [<c012b401>] __do_softirq+0x61/0x100
[34726.252659]  [<c012b4f5>] do_softirq+0x55/0x60
[34726.252664]  [<c0105b75>] do_IRQ+0x45/0x80
[34726.252671]  [<c0104233>] common_interrupt+0x23/0x30
[34726.252680]  [<e0b593b5>] raid5_compute_sector+0x165/0x260 [raid456]
[34726.252698]  [<e0b6061a>] make_request+0x2fa/0x770 [raid456]
[34726.252715]  [<c013ae00>] autoremove_wake_function+0x0/0x50
[34726.252728]  [<c01e1527>] generic_make_request+0xc7/0x240
[34726.252742]  [<c012b422>] __do_softirq+0x82/0x100
[34726.252754]  [<c015a032>] mempool_alloc+0x32/0x100
[34726.252761]  [<c01e3dd3>] submit_bio+0x53/0xe0
[34726.252770]  [<e0b59140>] raid5_mergeable_bvec+0x0/0x90 [raid456]
[34726.252776]  [<c019aa04>] __bio_add_page+0xf4/0x170
[34726.252784]  [<c019aab7>] bio_add_page+0x37/0x50
[34726.252790]  [<c019e0f8>] mpage_bio_submit+0x18/0x20
[34726.252796]  [<c019ec3c>] do_mpage_readpage+0x41c/0x710
[34726.252802]  [<c013ae1b>] autoremove_wake_function+0x1b/0x50
[34726.252809]  [<e095f230>] ext3_get_block+0x0/0x100 [ext3]
[34726.252850]  [<c01eed16>] radix_tree_node_alloc+0x16/0x60
[34726.252857]  [<c01ef359>] radix_tree_insert+0x179/0x1e0
[34726.252864]  [<c0157358>] add_to_page_cache+0x98/0xa0
[34726.252873]  [<c019f515>] mpage_readpages+0x95/0x150
[34726.252879]  [<e095f230>] ext3_get_block+0x0/0x100 [ext3]
[34726.252906]  [<e095e550>] ext3_readpages+0x0/0x20 [ext3]
[34726.252919]  [<c015dbd8>] __do_page_cache_readahead+0x178/0x250
[34726.252927]  [<e095f230>] ext3_get_block+0x0/0x100 [ext3]
[34726.252943]  [<c01ee985>] prio_tree_insert+0x1e5/0x250
[34726.252949]  [<c01797a9>] cp_new_stat64+0xf9/0x110
[34726.252960]  [<c016100f>] vma_prio_tree_insert+0x1f/0x50
[34726.252969]  [<c015e119>] force_page_cache_readahead+0x59/0x80
[34726.252977]  [<c0162cf9>] sys_madvise+0x429/0x440
[34726.252990]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[34726.252998]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[34726.253010]  =======================
[34726.253012] handlers:
[34726.253056] [<e08f1f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[34726.253185] [<e08f1f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[34726.253314] Disabling IRQ #11

```

is the hardware going down the drain or wth is going on here?

---

### Post by deebo32 on 2007-09-23
[http://funkiest.net/~globe/reboot.jpg](http://funkiest.net/~globe/reboot.jpg) more info, thsi is after mdadm finally had rebuilt the raid5 after 7 hours, i decided to reboot and test what happens, apparently not good things

---

### Post by deebo32 on 2007-09-23
ontop of all this, it wont come up at startup, fstab has /dev/md0 -> /store, but the init script complains of broken FS (it aint)

when i try to do "mdadm --assemble --auto=yes /dev/md0 /dev/sd[a-d]1" dmesg populates with :

```

[  345.036354] md: md0 stopped.
[  345.036472] md: unbind<sda1>
[  345.036554] md: export_rdev(sda1)
[  345.036645] md: unbind<sdb1>
[  345.036712] md: export_rdev(sdb1)
[  345.043510] md: bind<sdb1>
[  345.043891] md: invalid superblock checksum on sdc1
[  345.043896] md: sdc1 has invalid sb, not importing!
[  345.044095] md: md_import_device returned -22
[  345.044494] md: invalid superblock checksum on sdd1
[  345.044498] md: sdd1 has invalid sb, not importing!
[  345.044694] md: md_import_device returned -22
[  345.045077] md: bind<sda1>

```

i can get it running with 
"mdadm --assemble --update summaries /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1"

and after that i can mount it and everything seems fine:

```

root@sb32:~# cat /proc/mdstat
Personalities : [raid0] [raid6] [raid5] [raid4]
md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      1465151808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>

```

EDIT: and heres the mdadm.conf since i forgot it:

```

root@sb32:~# cat /etc/mdadm/mdadm.conf
DEVICE /dev/sd*1

ARRAY /dev/md0 level=raid5 num-devices=4 UUID=c0ae9cc8:0a367db1:60eac324:f662aeae devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1

MAILADDR root@localhost

```

---

### Post by deebo32 on 2007-09-23
more weird stuff happening...

while running "fsck -f -C0 /dev/md0"

```

[ 3207.602177] irq 16: nobody cared (try booting with the "irqpoll" option)
[ 3207.602265]  [<c0154334>] __report_bad_irq+0x24/0x80
[ 3207.602283]  [<c01545ee>] note_interrupt+0x25e/0x290
[ 3207.602292]  [<c0153860>] handle_IRQ_event+0x30/0x60
[ 3207.602299]  [<c0154f21>] handle_fasteoi_irq+0xc1/0xf0
[ 3207.602307]  [<c0105b70>] do_IRQ+0x40/0x80
[ 3207.602317]  [<c0104233>] common_interrupt+0x23/0x30
[ 3207.602323]  [<c0101e00>] default_idle+0x0/0x60
[ 3207.602331]  [<c011c0a2>] native_safe_halt+0x2/0x10
[ 3207.602341]  [<c0101e3d>] default_idle+0x3d/0x60
[ 3207.602345]  [<c0101409>] cpu_idle+0x49/0xd0
[ 3207.602351]  [<c03d97f5>] start_kernel+0x365/0x420
[ 3207.602362]  [<c03d9230>] unknown_bootoption+0x0/0x260
[ 3207.602372]  =======================
[ 3207.602374] handlers:
[ 3207.602418] [<e087c5c0>] (sil_interrupt+0x0/0x2a0 [sata_sil])
[ 3207.602540] Disabling IRQ #16
[ 3237.688962] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3237.689035] ata1.00: cmd 25/00:08:3f:a6:4e/00:00:10:00:00/e0 tag 0 cdb 0x0 data 4096 in
[ 3237.689038]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3238.000718] ata1: soft resetting port
[ 3238.156606] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)

```

should i just buy new hardware... :P

---

### Post by deebo32 on 2007-09-23
yah, f*ck this, ill burn the old msi mobo and stick ina newer nf430 mobo and hope it works

if it doesnt i might have to kill someone

---

