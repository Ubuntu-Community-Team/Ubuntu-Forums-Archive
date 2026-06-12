---
title: "Software raid 5 with XFS causing strange lockup problems"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by DROP on 2006-10-11
I am running XFS on a software raid 5. I am doing this with a PCI controller with 4 SATA drives attached to it.

When I play my music over the network through Samba from the raid volume my audio client will often loose the connection. This isn't remediated until I restart the machine with the raid controller or wait for an unknown amount of time. Either way, the problem still persists.

Initially I though that this was Samba's fault, but I think it may be xfs related due to what was in /var/log/messages:
```

Oct  9 22:37:33 ionlinux kernel: [105657.982701] Modules linked in: serio_raw i2c_nforce2 pcspkr forcedeth r8169 nvidia_agp agpgart i2c_core psmouse sg evdev xfs dm_mod sd_mod generic sata_nv ide_disk ehci_hcd ide_cd cdrom sata_sil ohci_hcd usbcore libata scsi_mod ide_generic processor
Oct  9 22:37:33 ionlinux kernel: [105657.982985] EIP:    0060:[<f8a1353e>]    Not tainted VLI
Oct  9 22:37:33 ionlinux kernel: [105657.982986] EFLAGS: 00010246   (2.6.18 #1)
Oct  9 22:37:33 ionlinux kernel: [105657.984000]  [<f89b290c>] xfs_bmap_search_extents+0xdc/0x100 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.984083]  [<f89baa22>] xfs_bmapi+0x302/0x2840 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.984163]  [ide_dma_exec_cmd+48/64] ide_dma_exec_cmd+0x30/0x40
Oct  9 22:37:33 ionlinux kernel: [105657.984228]  [ide_dma_start+51/80] ide_dma_start+0x33/0x50
Oct  9 22:37:33 ionlinux kernel: [105657.984294]  [mempool_alloc+58/224] mempool_alloc+0x3a/0xe0
Oct  9 22:37:33 ionlinux kernel: [105657.984360]  [cfq_set_request+447/752] cfq_set_request+0x1bf/0x2f0
Oct  9 22:37:33 ionlinux kernel: [105657.984425]  [do_timer+1117/3040] do_timer+0x45d/0xbe0
Oct  9 22:37:33 ionlinux kernel: [105657.984489]  [scheduler_tick+275/800] scheduler_tick+0x113/0x320
Oct  9 22:37:33 ionlinux kernel: [105657.984556]  [<f89fed13>] xfs_inactive_free_eofblocks+0x123/0x340 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.984643]  [<f8a0584a>] xfs_inactive+0xfa/0xcb0 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.984723]  [kmem_freepages+118/160] kmem_freepages+0x76/0xa0
Oct  9 22:37:33 ionlinux kernel: [105657.984784]  [slab_destroy+60/208] slab_destroy+0x3c/0xd0
Oct  9 22:37:33 ionlinux kernel: [105657.984845]  [__pagevec_release_nonlru+49/144] __pagevec_release_nonlru+0x31/0x90
Oct  9 22:37:33 ionlinux kernel: [105657.984910]  [memmove+80/112] memmove+0x50/0x70
Oct  9 22:37:33 ionlinux kernel: [105657.984973]  [<f89ddba0>] xfs_iextract+0x90/0x150 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.985053]  [<f89ddd4e>] xfs_ilock+0x8e/0xc0 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.985132]  [<f89e21c5>] xfs_idestroy+0x65/0x90 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.985212]  [<f8a00c1f>] xfs_finish_reclaim+0x10f/0x150 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.985294]  [<f8a00d78>] xfs_reclaim+0x118/0x120 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.985375]  [<f8a117f2>] xfs_fs_clear_inode+0x42/0x80 [xfs]
Oct  9 22:37:33 ionlinux kernel: [105657.985456]  [dquot_drop+0/128] dquot_drop+0x0/0x80
Oct  9 22:37:33 ionlinux kernel: [105657.985519]  [clear_inode+153/304] clear_inode+0x99/0x130
Oct  9 22:37:33 ionlinux kernel: [105657.985582]  [dispose_list+30/192] dispose_list+0x1e/0xc0
Oct  9 22:37:33 ionlinux kernel: [105657.985642]  [__activate_task+41/64] __activate_task+0x29/0x40
Oct  9 22:37:33 ionlinux kernel: [105657.985704]  [shrink_icache_memory+462/528] shrink_icache_memory+0x1ce/0x210
Oct  9 22:37:33 ionlinux kernel: [105657.985767]  [shrink_slab+297/400] shrink_slab+0x129/0x190
Oct  9 22:37:33 ionlinux kernel: [105657.985830]  [kswapd+718/1120] kswapd+0x2ce/0x460
Oct  9 22:37:33 ionlinux kernel: [105657.985893]  [autoremove_wake_function+0/96] autoremove_wake_function+0x0/0x60
Oct  9 22:37:33 ionlinux kernel: [105657.985960]  [kswapd+0/1120] kswapd+0x0/0x460
Oct  9 22:37:33 ionlinux kernel: [105657.986019]  [kthread+253/272] kthread+0xfd/0x110
Oct  9 22:37:33 ionlinux kernel: [105657.986079]  [kthread+0/272] kthread+0x0/0x110
Oct  9 22:37:33 ionlinux kernel: [105657.986139]  [kernel_thread_helper+5/16] kernel_thread_helper+0x5/0x10

```
When I SSH into the machine I performed a "ps aux" command and noticed that there were a lot of **/usr/bin/smbd -U** processes running

In addition to this is, when I am SSHed into the machine and I attempt to copy files or directories to or from the volume the ssh window stops responding and I am forced to close the connection and open a new one. Performing massive reads and writes has also caused the physical terminal(?) to freeze when I am using the machine (i.e. not sshed/using the thing locally)

Does anyone have any idea what might be causing this? The raid controller card or my XFS setup?

---

