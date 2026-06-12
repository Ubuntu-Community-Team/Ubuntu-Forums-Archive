---
title: "dmesg: skbuff alloc of size 3904 failed"
date: 2010-02-19
forum: Hardware
---

### Post by archish on 2010-02-19
I was just checking my dmesg logs and found this. Any reason why this is happening?
Using ubuntu 9.10 64bit. using 2.6.32.5 kernel.

> [153886.978869] skbuff alloc of size 3904 failed
[153886.978890] mount.ntfs: page allocation failure. order:1, mode:0x4020
[153886.978896] Pid: 7007, comm: mount.ntfs Tainted: P           2.6.32-02063205-generic #02063205
[153886.978900] Call Trace:
[153886.978903]  <IRQ>  [<ffffffff810ebc1f>] __alloc_pages_slowpath+0x3ff/0x540
[153886.978920]  [<ffffffff810ebea6>] __alloc_pages_nodemask+0x146/0x180
[153886.978928]  [<ffffffff81119c17>] alloc_pages_current+0x87/0xd0
[153886.978934]  [<ffffffff8111ef8d>] allocate_slab+0x19d/0x1b0
[153886.978940]  [<ffffffff8111efcb>] new_slab+0x2b/0x190
[153886.978946]  [<ffffffff81121266>] __slab_alloc+0x1d6/0x230
[153886.978960]  [<ffffffffa0b41030>] ? ath_rxbuf_alloc+0x30/0xb0 [ath]
[153886.978966]  [<ffffffff811221f7>] __kmalloc_node_track_caller+0x137/0x180
[153886.978973]  [<ffffffffa0b41030>] ? ath_rxbuf_alloc+0x30/0xb0 [ath]
[153886.978981]  [<ffffffff81434bb6>] __alloc_skb+0x76/0x180
[153886.978988]  [<ffffffffa0b41030>] ath_rxbuf_alloc+0x30/0xb0 [ath]
[153886.979004]  [<ffffffffa0bc22af>] ath_rx_tasklet+0x20f/0x580 [ath9k]
[153886.979012]  [<ffffffff81018710>] ? nommu_map_page+0x0/0x90
[153886.979027]  [<ffffffffa0bbf51d>] ath9k_tasklet+0xbd/0x150 [ath9k]
[153886.979034]  [<ffffffff810691ec>] tasklet_action+0x6c/0xe0
[153886.979039]  [<ffffffff8106931f>] __do_softirq+0xbf/0x1d0
[153886.979046]  [<ffffffff810bcb99>] ? handle_IRQ_event+0x59/0x140
[153886.979052]  [<ffffffff8101312c>] call_softirq+0x1c/0x30
[153886.979057]  [<ffffffff81014b85>] do_softirq+0x65/0xa0
[153886.979062]  [<ffffffff81068627>] irq_exit+0x77/0x80
[153886.979067]  [<ffffffff81013ee3>] do_IRQ+0x73/0xe0
[153886.979072]  [<ffffffff81012953>] ret_from_intr+0x0/0x11
[153886.979075]  <EOI>  [<ffffffff81213f61>] ? fuse_copy_one+0x1/0x60
[153886.979085]  [<ffffffff81214643>] ? fuse_copy_args+0x53/0xa0
[153886.979090]  [<ffffffff8121471f>] ? copy_out_args+0x8f/0xd0
[153886.979095]  [<ffffffff81214979>] ? fuse_dev_write+0x219/0x2e0
[153886.979101]  [<ffffffff81214760>] ? fuse_dev_write+0x0/0x2e0
[153886.979107]  [<ffffffff8112c45b>] ? do_sync_readv_writev+0xeb/0x130
[153886.979114]  [<ffffffff8107f670>] ? autoremove_wake_function+0x0/0x40
[153886.979121]  [<ffffffff811589d5>] ? blkdev_aio_write+0x55/0x80
[153886.979127]  [<ffffffff8112c591>] ? do_sync_write+0xf1/0x130
[153886.979133]  [<ffffffff8112c6c1>] ? do_sync_read+0xf1/0x130
[153886.979139]  [<ffffffff8122f521>] ? security_file_permission+0x11/0x20
[153886.979144]  [<ffffffff8112d4eb>] ? do_readv_writev+0xcb/0x1e0
[153886.979152]  [<ffffffff81055877>] ? finish_task_switch+0x67/0xd0
[153886.979157]  [<ffffffff8112d639>] ? vfs_writev+0x39/0x60
[153886.979162]  [<ffffffff8112d770>] ? sys_writev+0x50/0xb0
[153886.979169]  [<ffffffff81011fc2>] ? system_call_fastpath+0x16/0x1b

---

### Post by nutznboltz on 2011-01-24
*[153886.978890] mount.ntfs: page allocation failure. order:1, mode:0x4020*

Probably the same as this bug:

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/591947](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/591947)

This is the first one I've seen with ath as the network drivers but e100, e1000, e1000e and virtio have all seen it.

---

