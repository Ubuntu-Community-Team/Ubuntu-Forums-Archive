---
title: "nVidia Module Segfault on Boot With Kernel 3.0.x"
date: 2011-10-15
forum: Hardware
---

### Post by CharlesT423 on 2011-10-15
I had this problem with 11.04 and it remains with 11.10.  Whenever the nVidia module is loaded at boot time it segfaults when I'm using a 3.0 kernel (I've tried 3.0.0-12 and 3.0.3-03003) with nVidia drivers 280.13 and 285.05.09  Both packages work fine with kernel 2.6.38-11 and earlier.

The relevant part of the boot log seems to be:
```

[   21.334303] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   21.475839] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   21.564103] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   21.783906] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   22.103824] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/000
0:01:00.1/sound/card1/input10
[   22.103863] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   22.103898] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   22.103932] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   22.104085] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.104093] nvidia 0000:01:00.0: setting latency timer to 64
[   22.104097] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.104236] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011
[   22.104303] BUG: unable to handle kernel paging request at ffff8800dfce835c
[   22.104484] IP: [<ffffffff810a05bc>] module_put+0x2c/0x90
[   22.104612] PGD 1a04063 PUD 0 
[   22.106327] Oops: 0002 [#1] SMP 
[   22.106484] CPU 0 
[   22.106534] Modules linked in: nfsd binfmt_misc snd_hda_codec_hdmi xfs nfs lockd fscache auth_rpcgss nfs_acl sunrpc nvidia(P) usb_storage uas snd_hda_codec_realtek ir_lirc_codec ppdev lirc_dev parport_pc eeepc_wmi ir_sony_decoder snd_hda_intel ir_jvc_decoder snd_hda_codec snd_hwdep ir_rc6_decoder ir_rc5_decoder snd_pcm snd_seq_midi rc_rc6_mce ir_nec_decoder snd_rawmidi snd_seq_midi_event mceusb rc_core lp joydev snd_seq snd_timer snd_seq_device asus_wmi video parport snd soundcore psmouse snd_page_alloc sparse_keymap serio_raw mei(C) wmi usbhid hid pata_via xhci_hcd r8169 configfs
[   22.109497] 
[   22.109556] Pid: 366, comm: modprobe Tainted: P         C  3.0.3-030003-generic #201108180913 System manufacturer System Product Name/P8H67-M PRO
[   22.109780] RIP: 0010:[<ffffffff810a05bc>]  [<ffffffff810a05bc>] module_put+0x2c/0x90
[   22.109902] RSP: 0018:ffff8801349cff28  EFLAGS: 00010286
[   22.109965] RAX: ffffffffa08e835c RBX: ffffffffa0c48440 RCX: 0000000000000000
[   22.110029] RDX: ffff8801349cffd8 RSI: 0000000000000286 RDI: ffffffffa0c48440
[   22.110094] RBP: ffff8801349cff48 R08: 0000000000000000 R09: 0000000000000000
[   22.110158] R10: 0000000000000001 R11: 00000000000000ff R12: 0000000000000000
[   22.110223] R13: 00007fb0bad2f000 R14: 0000000000000000 R15: 0000000000405e30
[   22.110288] FS:  00007fb0bc25b720(0000) GS:ffff88013f400000(0000) knlGS:0000000000000000
[   22.110363] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   22.110426] CR2: ffff8800dfce835c CR3: 00000001343fa000 CR4: 00000000000406f0
[   22.110490] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   22.110555] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   22.110620] Process modprobe (pid: 366, threadinfo ffff8801349ce000, task ffff880134b15bc0)
[   22.110694] Stack:
[   22.110753]  ffff8801349cff48 ffffffffa0c48440 0000000000000000 00007fb0bad2f000
[   22.111017]  ffff8801349cff78 ffffffff810a3726 0000000000000049 00000000006f0750
[   22.111288]  0000000000000008 00000000006ec140 00000000006f0860 ffffffff815e5842
[   22.111552] Call Trace:
[   22.111613]  [<ffffffff810a3726>] sys_init_module+0x126/0x220
[   22.111677]  [<ffffffff815e5842>] system_call_fastpath+0x16/0x1b
[   22.111740] Code: 48 89 e5 48 83 ec 20 48 89 5d e8 4c 89 65 f0 4c 89 6d f8 66 66 66 66 90 48 85 ff 48 89 fb 74 21 48 8b 87 48 02 00 00 48 83 c0 04 
[   22.113895]  ff 00 8b 05 e3 d7 a0 00 4c 8b 65 08 85 c0 75 13 83 3b 02 74 
[   22.115022] RIP  [<ffffffff810a05bc>] module_put+0x2c/0x90
[   22.115133]  RSP <ffff8801349cff28>
[   22.115193] CR2: ffff8800dfce835c
[   22.115254] ---[ end trace 9a8f50bfaa26e687 ]---
[   22.257161] init: udev-fallback-graphics main process (1166) terminated with status 1


```I have a GeForce GT 240 card and an ASUS P8 H67-M motherboard with an Intel i5-2500k CPU if that helps.  Any ideas would be appreciated.

---

