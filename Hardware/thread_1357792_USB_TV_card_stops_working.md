---
title: "USB TV card stops working"
date: 2009-12-17
forum: Hardware
---

### Post by stureid on 2009-12-17
Hi

I've got a problem in Karmic where my USB TV cards stop working.  I wondered if the USB port was going to sleep so I passed usbcore.autosuspend=-1 as a kernel parameter.  This has not remedied the problem.

Here is the relevant part of my dmesg:

[INDENT][12515.611372] usb 2-2: USB disconnect, address 2
[12515.611613] af9015: bulk message failed:-22 (8/0)
[12515.611619] af9013: I2C read failed reg:d730
[12517.092538] BUG: unable to handle kernel NULL pointer dereference at 0000000000000ce8
[12517.092551] IP: [<ffffffff815286e6>] mutex_lock_interruptible+0x16/0x50
[12517.092568] PGD 530ab067 PUD 541f2067 PMD 0
[12517.092577] Oops: 0002 [#1] SMP
[12517.092583] last sysfs file: /sys/devices/pci0000:00/0000:00:09.0/host0/target0:0:0/0:0:0:0/block/sda/uevent
[12517.092590] CPU 2
[12517.092594] Modules linked in: bridge stp bnep ppdev lirc_mceusb lirc_dev snd_hda_codec_via isl6421 cx24116 cx88_dvb cx88_vp3054_i2c videobuf_dvb tuner cx88_alsa cx8802 cx8800 snd_hda_intel cx88xx snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy mxl5005s snd_seq_oss snd_seq_midi snd_rawmidi af9013 snd_seq_midi_event snd_seq snd_timer ir_common snd_seq_device snd soundcore i2c_algo_bit iptable_filter ip_tables v4l2_common videodev dvb_usb_af9015 v4l1_compat lp v4l2_compat_ioctl32 tveeprom dvb_usb videobuf_dma_sg amd64_edac_mod parport shpchp edac_core x_tables videobuf_core btcx_risc dvb_core i2c_nforce2 btusb snd_page_alloc nvidia(P) fbcon tileblit font bitblit softcursor usbhid video output forcedeth
[12517.092686] Pid: 2125, comm: kdvb-ad-1-fe-0 Tainted: P           2.6.31-17-generic #54-Ubuntu GF8100VM-M5
[12517.092692] RIP: 0010:[<ffffffff815286e6>]  [<ffffffff815286e6>] mutex_lock_interruptible+0x16/0x50
[12517.092705] RSP: 0018:ffff8800599d1c90  EFLAGS: 00010246
[12517.092709] RAX: 00000000ffffffff RBX: 0000000000000ce8 RCX: 0000000000000001
[12517.092714] RDX: 0000000000000000 RSI: ffff8800599d1d60 RDI: 0000000000000ce8
[12517.092718] RBP: ffff8800599d1ca0 R08: ffff8800599d1dff R09: 0000000000000000
[12517.092723] R10: 0000000000000000 R11: 00000000ffffffff R12: 0000000000000000
[12517.092727] R13: ffff8800599d1d60 R14: 0000000000000002 R15: 0000000000000000
[12517.092733] FS:  00007fb47c3427a0(0000) GS:ffff880001a32000(0000) knlGS:0000000000000000
[12517.092738] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
[12517.092742] CR2: 0000000000000ce8 CR3: 0000000053038000 CR4: 00000000000006e0
[12517.092747] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[12517.092751] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[12517.092757] Process kdvb-ad-1-fe-0 (pid: 2125, threadinfo ffff8800599d0000, task ffff880058c44410)
[12517.092761] Stack:
[12517.092764]  ffff8800599d1cf0 ffff8800599d1d60 ffff8800599d1d00 ffffffffa0a2b361
[12517.092771] <0> ffff8800599d1d00 0000000000000ce8 ffff8800599d1ce0 0000000000000000
[12517.092779] <0> ffff880001a47880 ffff8800692ea200 0000000000000000 ffff8800599d1d60
[12517.092789] Call Trace:
[12517.092804]  [<ffffffffa0a2b361>] af9015_i2c_xfer+0x31/0x210 [dvb_usb_af9015]
[12517.092814]  [<ffffffff813d05ac>] i2c_transfer+0xac/0x100
[12517.092827]  [<ffffffffa0ac5189>] af9013_read_reg+0x69/0xa0 [af9013]
[12517.092836]  [<ffffffff8106b12a>] ? del_timer_sync+0x1a/0x30
[12517.092845]  [<ffffffffa0ac54a9>] af9013_read_reg_bits+0x29/0x60 [af9013]
[12517.092855]  [<ffffffffa0ac6bd9>] af9013_read_status+0x49/0x160 [af9013]
[12517.092864]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
[12517.092884]  [<ffffffffa0999a5c>] dvb_frontend_swzigzag+0x8c/0x270 [dvb_core]
[12517.092901]  [<ffffffffa099a068>] dvb_frontend_thread+0x428/0x720 [dvb_core]
[12517.092910]  [<ffffffff81078b20>] ? autoremove_wake_function+0x0/0x40
[12517.092926]  [<ffffffffa0999c40>] ? dvb_frontend_thread+0x0/0x720 [dvb_core]
[12517.092933]  [<ffffffff81078736>] kthread+0xa6/0xb0
[12517.092940]  [<ffffffff810130ea>] child_rip+0xa/0x20
[12517.092947]  [<ffffffff81078690>] ? kthread+0x0/0xb0
[12517.092952]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
[12517.092955] Code: 48 89 10 e8 fd dc b0 ff 66 90 b8 fc ff ff ff eb d1 0f 1f 40 00 55 48 89 e5 53 48 89 fb 48 83 ec 08 e8 2f f6 ff ff b8 ff ff ff ff <f0> 0f c1 03 83 e8 01 78 1c 65 48 8b 04 25 88 cb 00 00 48 2d d8
[12517.093009] RIP  [<ffffffff815286e6>] mutex_lock_interruptible+0x16/0x50
[12517.093017]  RSP <ffff8800599d1c90>
[12517.093020] CR2: 0000000000000ce8
[12517.093026] ---[ end trace 786c2d36f405bd5b ]---
[27054.793437] mythfilldatabas[7767]: segfault at 0 ip 00007f6e90da773c sp 00007f6e864d3150 error 4 in libQtCore.so.4.5.2[7f6e90d4e000+22d000]
[/INDENT]

Thanks in advance for any help.

Karmic is driving me potty, it's one thing after another!

---

