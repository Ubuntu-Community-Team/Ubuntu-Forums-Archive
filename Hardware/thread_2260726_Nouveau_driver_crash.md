---
title: "Nouveau driver crash"
date: 2015-01-14
forum: Hardware
---

### Post by dargaud2 on 2015-01-14
Hello all,
I have a system that uses the Nouveau driver. Since the latest kernel update (it'd never happened before 2 weeks ago), it keeps freezing every hour or so. No mouse motion, no Ctrl-Alt-F2 consoles, no Ctrl-Alt-backspace, no Ctrl-Alt-Del... But I can still log via ssh, which is how I managed to get this:
```
[  856.685821] BUG: unable to handle kernel paging request at ffffc900003f8000
[  856.685859] IP: [<ffffffffc01dd84b>] nouveau_bo_wr32+0x1b/0x30 [nouveau]
[  856.685943] PGD 7d01d067 PUD 7d01e067 PMD 7c64d067 PTE 0
[  856.685966] Oops: 0002 [#1] SMP 
[  856.685980] Modules linked in: rfcomm bnep bluetooth 6lowpan_iphc snd_usb_audio snd_intel8x0 snd_usbmidi_lib snd_ac97_codec snd_hwdep ac97_bus snd_seq_midi snd_seq_midi_event snd_rawmidi uvcvideo videobuf2_vmalloc snd_seq videobuf2_memops videobuf2_core v4l2_common snd_pcm videodev media snd_seq_device snd_timer snd serio_raw soundcore shpchp edac_core k8temp edac_mce_amd i2c_nforce2 parport_pc ppdev mac_hid lp parport hid_generic usbhid hid uas usb_storage nouveau mxm_wmi wmi video i2c_algo_bit ttm drm_kms_helper drm tg3 ptp pps_core firewire_ohci firewire_core pata_acpi crc_itu_t floppy pata_amd sata_nv
[  856.686226] CPU: 0 PID: 1407 Comm: Xorg Not tainted 3.16.0-29-generic #39-Ubuntu
[  856.686253] Hardware name:    /NF-CK804, BIOS 6.00 PG 11/14/2006
[  856.686275] task: ffff880079a932f0 ti: ffff880079494000 task.ti: ffff880079494000
[  856.686301] RIP: 0010:[<ffffffffc01dd84b>]  [<ffffffffc01dd84b>] nouveau_bo_wr32+0x1b/0x30 [nouveau]
[  856.686366] RSP: 0018:ffff880079497820  EFLAGS: 00010246
[  856.686386] RAX: ffffc900003e8000 RBX: ffff880035d2e000 RCX: 0000000000003ffd
[  856.686411] RDX: 0000000020000000 RSI: ffffc900003f8000 RDI: ffff880035d5fc00
[  856.686436] RBP: ffff880079497858 R08: 0000000000003ffd R09: 0000000000000001
[  856.686461] R10: 0000000000035cd8 R11: 0000000000000000 R12: 0000000000000000
[  856.686485] R13: 000000000000fff4 R14: 0000000000000001 R15: 000000000000000b
[  856.686511] FS:  00007fa0b484f9c0(0000) GS:ffff88007fc00000(0000) knlGS:0000000000000000
[  856.686539] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  856.686560] CR2: ffffc900003f8000 CR3: 000000007aea2000 CR4: 00000000000007f0
[  856.686584] Stack:
[  856.686593]  ffffffffc01d93cb 00000000000080c0 0000000000000025 ffff880041491c38
[  856.686621]  000000000200c000 0000000000d55000 ffff880035d2e000 ffff880079497890
[  856.686650]  ffffffffc01de602 ffff880041491c00 ffff880035d2e000 ffff880079497a70
[  856.686678] Call Trace:
[  856.686722]  [<ffffffffc01d93cb>] ? nouveau_dma_wait+0xeb/0x590 [nouveau]
[  856.686779]  [<ffffffffc01de602>] nv04_bo_move_m2mf+0xe2/0x280 [nouveau]
[  856.686834]  [<ffffffffc01dc204>] nouveau_bo_move_m2mf+0x154/0x1c0 [nouveau]
[  856.686884]  [<ffffffffc0197576>] ? nv44_vm_flush+0x96/0xa0 [nouveau]
[  856.686939]  [<ffffffffc01dc9d6>] nouveau_bo_move+0xa6/0x4b0 [nouveau]
[  856.686989]  [<ffffffffc019c498>] ? nv_device_map_page+0x48/0xd0 [nouveau]
[  856.687023]  [<ffffffffc0116162>] ttm_bo_handle_move_mem+0x2b2/0x650 [ttm]
[  856.687052]  [<ffffffffc0116c5b>] ? ttm_bo_mem_space+0x16b/0x350 [ttm]
[  856.687106]  [<ffffffffc01dbc00>] ? nouveau_bo_del_ttm+0x50/0x90 [nouveau]
[  856.687137]  [<ffffffffc011667a>] ttm_bo_evict+0x17a/0x380 [ttm]
[  856.687164]  [<ffffffffc0116a3c>] ttm_mem_evict_first+0x1bc/0x270 [ttm]
[  856.687192]  [<ffffffffc0116db9>] ttm_bo_mem_space+0x2c9/0x350 [ttm]
[  856.687220]  [<ffffffffc0117302>] ttm_bo_validate+0x1c2/0x240 [ttm]
[  856.687248]  [<ffffffffc01175bd>] ttm_bo_init+0x23d/0x3a0 [ttm]
[  856.687300]  [<ffffffffc01dd14c>] nouveau_bo_new+0x1fc/0x310 [nouveau]
[  856.687355]  [<ffffffffc01dbbb0>] ? nv10_bo_put_tile_region+0x50/0x50 [nouveau]
[  856.687414]  [<ffffffffc01df8ac>] nouveau_gem_new+0x5c/0x140 [nouveau]
[  856.687469]  [<ffffffffc01dfa31>] nouveau_gem_ioctl_new+0xa1/0x1f0 [nouveau]
[  856.687514]  [<ffffffffc00c9a4f>] drm_ioctl+0x1df/0x680 [drm]
[  856.687539]  [<ffffffff813a3ea0>] ? timerqueue_add+0x60/0xb0
[  856.687589]  [<ffffffffc01d7165>] nouveau_drm_ioctl+0x65/0xa0 [nouveau]
[  856.687616]  [<ffffffff811f5208>] do_vfs_ioctl+0x2c8/0x4a0
[  856.687638]  [<ffffffff81667fd2>] ? __sys_recvmsg+0x42/0x80
[  856.687659]  [<ffffffff811f5461>] SyS_ioctl+0x81/0xa0
[  856.687681]  [<ffffffff810930c1>] ? posix_ktime_get_ts+0x11/0x20
[  856.687705]  [<ffffffff8178a1ad>] system_call_fastpath+0x1a/0x1f
[  856.687726] Code: 55 48 89 c7 48 89 e5 e8 14 32 1d c1 5d c3 66 90 66 66 66 66 90 f6 87 40 02 00 00 80 48 8b 87 30 02 00 00 89 f6 48 8d 34 b0 75 05 <89> 16 c3 66 90 55 89 d7 48 89 e5 e8 b5 32 1d c1 5d c3 0f 1f 00 
[  856.687849] RIP  [<ffffffffc01dd84b>] nouveau_bo_wr32+0x1b/0x30 [nouveau]
[  856.687905]  RSP <ffff880079497820>
[  856.687918] CR2: ffffc900003f8000
[  856.688008] ---[ end trace 2eb00edb8f618a8b ]---
```

Now while I was logged via ssh, I tried to get KDE to restart by typing this:
```
kwin --replace
```
I'd never tried that command before and it restarted all the windows on MY SYSTEM. How is that even possible ?!? I ended up having to reboot both systems since the new windows had no decorations and I couldn't move or Alt-Tab them. I was logged with "ssh -Y", is that how that command managed to affect the caller ?

---

