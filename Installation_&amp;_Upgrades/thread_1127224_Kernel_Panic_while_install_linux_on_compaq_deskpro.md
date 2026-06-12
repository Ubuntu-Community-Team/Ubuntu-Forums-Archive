---
title: "Kernel Panic while install linux on compaq deskpro"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by fuzeman on 2009-04-16
Well im trying to install linux on a compaq deskpro pentium 3 ive tried ubuntu (7.10, 8.04, 8.10, 9.04 beta), openSUSE (10.1, 11.1), centOS 5.2, Fedora 10, kubuntu (7.10, 8.04) with no luck either when i get into the menu then i press install it comes up saying install not found or something or it comes up with a kernel panic error while loading the installer i have also been using ubuntu and kubuntu free cds that get sent to you that means im burning the isos right. Is there some hardware problem in compaq deskpros that are causing this? anyone have any ideas on how to fix this. Ill try booting the installer again very soon to give you the full error.

Thanks.

EDIT this is the full error this is what i can see when the error happens this took 27mins to right down:
```

[   38.386818]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   38.386877] Process swapper (pid: 0, ti=c041c000 task=c03ea3a0 task.ti=c041c0
00)
[   38.386941] Stack: 00000000 c03f5480 000000d0 00000000 00000002 00000002 e7c2
6800 c04259f5
[   38.387322]        00000020 e7c050c0 00000500 e7c26824 00000007 00000101 0000
0120 e7c26000
[   38.387700]        00000210 e7c00097 00000000 00000067 00000001 00000009 0000
0007 e7c05088
[   38.388078] Call Trace:
[   38.388161] [<c04259f5>] huft_build+0x325/0x630
[   38.388269] [<c04262c5>] inflate_fixed+0x15/0x1b0
[   38.388377] [<c0426393>] inflate_fixed+0xe3/0x1b0
[   38.388483] [<c0426b35>] unpack_to_rootfs+0x6d5/0x950
[   38.388589] [<c0426dca>] early_populate_rootfs+0x1a/0x60
[   38.388697] [<c0421a55>] start_kernel+0x315/0x3b0
[   38.388800] [<c0421130>] unknown_bootoption+0x0/0x1e0
[   38.388905] =======================
[   38.388962] Code: 1f 84 00 00 00 00 00 89 c6 fa 0f 1f 84 00 00 00 00 00 90 64
 a1 08 60 47 c0 8b 6c 87 70 8b 5d 00 85 db 0f 84 8a 00 00 00 8b 45 0c <8b> 04 83
 89 45 00 89 f0 50 9d 0f 1f 84 00 00 00 00 00 66 83 7c
[   38.391331] EIP: [<c018e9c4>] __kmalloc+0x64/0x110 SS:ESP 0068:c041de90
[   38.391502] ---[ end trace ca143223eefdc828 ]---
[   38.391568] Kernel panic - not syncing: Attempted to kill the idle task!

```

---

### Post by fuzeman on 2009-04-16
here are my pc specs:
```
RAM: 640mb
CDROM: BTC 24x IDE
CPU: 450mhz
```

Will that help?

---

