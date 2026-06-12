---
title: "Help me decipher these DMESG messages"
date: 2010-02-01
forum: Hardware
---

### Post by Turin Turambar on 2010-02-01
Periodically (at least 1x a day) I experience unexpected jerkiness and slowness in mouse control.

These are dmesg messages that appeared right after mouse slowed down...

```
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546686] irq 21: nobody cared (try booting with the "irqpoll" option)
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546692] Pid: 1337, comm: Xorg Not tainted 2.6.31-18-generic #55-Ubuntu
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546694] Call Trace:
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546695]  <IRQ>  [<ffffffff810b54a6>] __report_bad_irq+0x26/0xa0
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546704]  [<ffffffff810b56ac>] note_interrupt+0x18c/0x1d0
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546707]  [<ffffffff810655a5>] ? __do_softirq+0x125/0x200
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546709]  [<ffffffff810b5d25>] handle_fasteoi_irq+0xd5/0x100
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546712]  [<ffffffff81014c5d>] handle_irq+0x1d/0x30
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546714]  [<ffffffff81014137>] do_IRQ+0x67/0xe0
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546717]  [<ffffffff81012a53>] ret_from_intr+0x0/0x11
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546718]  <EOI>  [<ffffffff8127c513>] ? rb_next+0x13/0x60
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546725]  [<ffffffff8152ced9>] ? _spin_lock+0x9/0x10
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546728]  [<ffffffff81102020>] ? alloc_vmap_area+0x1a0/0x360
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546730]  [<ffffffff81102280>] ? __get_vm_area_node+0xa0/0x240
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546732]  [<ffffffff811022d0>] ? __get_vm_area_node+0xf0/0x240
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546753]  [<ffffffffa00aa75f>] ? i915_gem_retire_requests+0xaf/0xd0 [i915]
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546761]  [<ffffffffa00ae652>] ? i915_gem_execbuffer+0x162/0xcd0 [i915]
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546764]  [<ffffffff81102e98>] ? __vmalloc_node+0x88/0xb0
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546771]  [<ffffffffa00ae652>] ? i915_gem_execbuffer+0x162/0xcd0 [i915]
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546778]  [<ffffffffa00aed2a>] ? i915_gem_execbuffer+0x83a/0xcd0 [i915]
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546781]  [<ffffffff81103032>] ? __vmalloc+0x12/0x20
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546788]  [<ffffffffa00ae652>] ? i915_gem_execbuffer+0x162/0xcd0 [i915]
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546801]  [<ffffffffa0072cae>] ? drm_ioctl+0x17e/0x3a0 [drm]
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546808]  [<ffffffffa00ae4f0>] ? i915_gem_execbuffer+0x0/0xcd0 [i915]
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546813]  [<ffffffff81036398>] ? __ticket_spin_lock+0x18/0x20
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546816]  [<ffffffff8112e6cc>] ? vfs_ioctl+0x7c/0xa0
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546817]  [<ffffffff8112ec99>] ? do_vfs_ioctl+0x79/0x370
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546821]  [<ffffffff8111fa8f>] ? vfs_read+0x12f/0x1a0
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546822]  [<ffffffff8112f011>] ? sys_ioctl+0x81/0xa0
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546825]  [<ffffffff8152d719>] ? do_device_not_available+0x9/0x10
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546827]  [<ffffffff81012a4e>] ? common_interrupt+0xe/0x13
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546829]  [<ffffffff81012042>] ? system_call_fastpath+0x16/0x1b
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546831] handlers:
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546832] [<ffffffff813a0cf0>] (usb_hcd_irq+0x0/0x80)
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546836] [<ffffffff8136b630>] (ata_sff_interrupt+0x0/0x130)
Feb  1 22:08:41 ivan-desktop kernel: [ 5891.546840] Disabling IRQ #21
```

Is there anything I can do to prevent this from happening? Thanks.

---

