---
title: "Random freezes with Ryzen CPU"
date: 2018-11-24
forum: Hardware
---

### Post by cristoferoswald on 2018-11-24
Hi, I'm currently having a issue I've never had with Ubuntu. At random use times it completely freezes.

Specifications:
MB: Gigabyte B450M-DS3H
CPU: Ryzen 5 2600X
Memory: HyperX Fury DDR4 2666 2x8GB CL16 White
GPU: RX 580
SSD: BX500 480GB
PSU: 550 W 80 plus bronze
OSs: Ubuntu 18.04.1 + Windows 10 Pro

Short history:
I built a new computer two weeks ago and made a dual boot setup (Ubuntu 18.10 + W10 Pro). Since first day I got random total freezes, only hard reset/shutdown works.
Two days ago I tried switching to 18.04.1 but had no success. Threre is no log errors, can't enter CTRL + ALT + F3, there is not a single clue and Windows works just fine,
got no problems with it running for hours.
Already tried:
 Re-installing both Ubuntu 18.04.1 LTS and 18.10.
                      Installing AMD-GPUPRO drivers (just got things worse)

Long history:
I'm a Ubuntu user for 4+ years and use it mostly for programming (computer science student). Had it in two machines, a low-end and mid-end laptop, both machines never gave me problems (not any I couldn't solve).
Two weeks ago I bought a new desktop computer, with the above specifications, installed Windows then Ubuntu. Since I got some pretty good components, I did some memory and GPU overclocking throught Windows, 
and was able to get some good numbers, did plenty of tests to see if it was stable and everything went fine. After that I went for installing Ubuntu. What a nightmare. First of all, the installation process kept freezing
with 30+- seconds, after some attempts, switched to 18.04.1, I went with it almost untill the end and then I got confident and tired 18.10 again. For some reason things went fine and I was able to install it.
But, after booting, it didn't take long to give my first freeze. Searched a lot and find that some users were having some problems with this Gigabyte + Ryzen setup, but it was in the previous kernel version, and not mine
so this shouldn't be the problem. I've tried some boot/kernel settings and nothing changed. Two days ago I installed 18.04.1 to see if the LTS version would make things better, but got no results. Now, the last thing
I tried was to reset all my overclock, everything is in it's standart configurations but, still, I'm getting freezes.
The worst thing is that I have no ways to see what made the system crash, there is no error prompt, no logs, can't enter terminal mode, nothing. I didn't change my linux distribution yet because I like Ubuntu
and the freezes just waste about 20 seconds of my time (thanks to SSD), but it is really annoying.
Just a final information, the freezes happens with any sort of usage, Chrome, some desktop app, seeing videos, using any IDE, etc.

---

### Post by oleoleole on 2019-02-22
Did you solve this?

I just happen to have just bought the same motherboard as you have, and syslog reports that board in the traces as far as I can tell. I use the same kind of memory, but 2*4GB CL17 instead as I don't need more for this as it should operate as a media center PC with steam. I run Nvidia proprietary drivers (GTX 1070). I have been going for a Ryzen 3 2200G as it suits for this task.

So looking at your specs, I assume we might have a motherboard problem. I end up getting random freezes to, I even tried a newer kernel (4.20). My motherboard is updated to F4 version, which is currently the newest.

**syslog:**
> 
Feb 22 12:31:30 snorre kernel: [ 3076.302042] invalid opcode: 0000 [#1] SMP NOPTI
Feb 22 12:31:30 snorre kernel: [ 3076.302048] CPU: 1 PID: 1362 Comm: irq/58-nvidia Tainted: P           OE     4.20.10-042010-generic #201902150516
Feb 22 12:31:30 snorre kernel: [ 3076.302051] Hardware name: Gigabyte Technology Co., Ltd. B450M DS3H/B450M DS3H-CF, BIOS F4 01/25/2019
Feb 22 12:31:30 snorre kernel: [ 3076.302346] RIP: 0010:_nv017125rm+0x40/0x70 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.302349] Code: 48 85 c0 75 36 48 c7 c6 80 c8 00 c1 e8 39 88 08 00 49 89 c4 31 c0 48 85 db 74 04 48 8b 43 68 48 a9 c7 ff 90 20 01 00 00 48 83 <c4> 08 4c 89 e7 89 c6 5b 41 5c 31 d2 e9 9f 58 e2 ff 48 89 df be cb
Feb 22 12:31:30 snorre kernel: [ 3076.302352] RSP: 0018:ffffafad0176bd08 EFLAGS: 00010213
Feb 22 12:31:30 snorre kernel: [ 3076.302354] RAX: ffff9bcbba5c9010 RBX: ffff9bcbba5c9010 RCX: ffff9bcbb6e84008
Feb 22 12:31:30 snorre kernel: [ 3076.302356] RDX: ffffffffc100c800 RSI: 00000000007ef3cb RDI: ffff9bcbb6e84008
Feb 22 12:31:30 snorre kernel: [ 3076.302358] RBP: ffff9bcbb53cdc60 R08: 0000000000000005 R09: ffffffffc100ccc0
Feb 22 12:31:30 snorre kernel: [ 3076.302360] R10: ffff9bcbb53cdeb0 R11: ffffffffc0c60940 R12: ffff9bcbb6e84008
Feb 22 12:31:30 snorre kernel: [ 3076.302361] R13: ffff9bcbcd63a808 R14: ffff9bcbd2ed7008 R15: ffff9bcbcf37d408
Feb 22 12:31:30 snorre kernel: [ 3076.302364] FS:  0000000000000000(0000) GS:ffff9bcbd6a40000(0000) knlGS:0000000000000000
Feb 22 12:31:30 snorre kernel: [ 3076.302366] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 22 12:31:30 snorre kernel: [ 3076.302368] CR2: 00001cf4246ba8c0 CR3: 00000001d55b2000 CR4: 00000000003406e0
Feb 22 12:31:30 snorre kernel: [ 3076.302369] Call Trace:
Feb 22 12:31:30 snorre kernel: [ 3076.302682]  ? _nv023492rm+0x50/0x1050 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.303030]  ? _nv027813rm+0x557/0x660 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.303350]  ? _nv008125rm+0x16c/0x220 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.303648]  ? _nv027820rm+0x1d/0x170 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.303947]  ? _nv027821rm+0xa2/0x130 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.304124]  ? _nv001098rm+0x10e/0x150 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.304128]  ? irq_finalize_oneshot.part.42+0xf0/0xf0
Feb 22 12:31:30 snorre kernel: [ 3076.304305]  ? rm_isr_bh+0x23/0x70 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.304468]  ? nvidia_isr_common_bh+0x34/0x80 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.304631]  ? nvidia_isr_kthread_bh+0x11/0x20 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.304633]  ? irq_thread_fn+0x24/0x60
Feb 22 12:31:30 snorre kernel: [ 3076.304635]  ? irq_thread+0xea/0x170
Feb 22 12:31:30 snorre kernel: [ 3076.304637]  ? irq_forced_thread_fn+0x80/0x80
Feb 22 12:31:30 snorre kernel: [ 3076.304641]  ? kthread+0x120/0x140
Feb 22 12:31:30 snorre kernel: [ 3076.304643]  ? irq_thread_check_affinity+0xf0/0xf0
Feb 22 12:31:30 snorre kernel: [ 3076.304645]  ? __kthread_parkme+0x70/0x70
Feb 22 12:31:30 snorre kernel: [ 3076.304648]  ? ret_from_fork+0x22/0x40
Feb 22 12:31:30 snorre kernel: [ 3076.304650] Modules linked in: hid_sony ff_memless hidp rfcomm nfsv3 nfs_acl rpcsec_gss_krb5 auth_rpcgss nfsv4 nfs lockd grace fscache cmac bnep nls_iso8859_1 snd_hda_codec_hdmi nvidia_uvm(OE) edac_mce_amd ccp kvm irqbypass nvidia_drm(POE) nvidia_modeset(POE) crct10dif_pclmul crc32_pclmul nvidia(POE) ghash_clmulni_intel snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_hda_intel snd_seq_dummy snd_hda_codec snd_hda_core snd_usbmidi_lib snd_seq_oss snd_hwdep snd_seq_midi snd_seq_midi_event snd_rawmidi aesni_intel aes_x86_64 crypto_simd btusb cryptd glue_helper btrtl drm_kms_helper btbcm btintel snd_seq snd_pcm drm serio_raw bluetooth drm_panel_orientation_quirks ipmi_devintf ipmi_msghandler wmi_bmof joydev snd_seq_device cfbfillrect input_leds snd_timer cfbimgblt ecdh_generic k10temp cfbcopyarea fb_sys_fops syscopyarea snd sysfillrect sysimgblt fb fbdev soundcore mac_hid sch_fq_codel parport_pc sunrpc ppdev lp parport ip_tables x_tables autofs4 hid_logitech_hidpp hid_logitech_dj
Feb 22 12:31:30 snorre kernel: [ 3076.304689]  hid_generic usbhid hid psmouse i2c_piix4 r8169 i2c_core ahci realtek libahci wmi video gpio_amdpt gpio_generic
Feb 22 12:31:30 snorre kernel: [ 3076.304707] ---[ end trace 88c812bb0b4a27fc ]---
Feb 22 12:31:30 snorre kernel: [ 3076.304969] RIP: 0010:_nv017125rm+0x40/0x70 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.304971] Code: 48 85 c0 75 36 48 c7 c6 80 c8 00 c1 e8 39 88 08 00 49 89 c4 31 c0 48 85 db 74 04 48 8b 43 68 48 89 c7 ff 90 20 01 00 00 48 83 <c4> 08 4c 89 e7 89 c6 5b 41 5c 31 d2 e9 9f 58 e2 ff 48 89 df be cb
Feb 22 12:31:30 snorre kernel: [ 3076.304973] RSP: 0018:ffffafad0176bd08 EFLAGS: 00010213
Feb 22 12:31:30 snorre kernel: [ 3076.304975] RAX: ffff9bcbba5c9010 RBX: ffff9bcbba5c9010 RCX: ffff9bcbb6e84008
Feb 22 12:31:30 snorre kernel: [ 3076.304976] RDX: ffffffffc100c800 RSI: 00000000007ef3cb RDI: ffff9bcbb6e84008
Feb 22 12:31:30 snorre kernel: [ 3076.304978] RBP: ffff9bcbb53cdc60 R08: 0000000000000005 R09: ffffffffc100ccc0
Feb 22 12:31:30 snorre kernel: [ 3076.304979] R10: ffff9bcbb53cdeb0 R11: ffffffffc0c60940 R12: ffff9bcbb6e84008
Feb 22 12:31:30 snorre kernel: [ 3076.304980] R13: ffff9bcbcd63a808 R14: ffff9bcbd2ed7008 R15: ffff9bcbcf37d408
Feb 22 12:31:30 snorre kernel: [ 3076.304982] FS:  0000000000000000(0000) GS:ffff9bcbd6a40000(0000) knlGS:0000000000000000
Feb 22 12:31:30 snorre kernel: [ 3076.304984] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 22 12:31:30 snorre kernel: [ 3076.304985] CR2: 00001cf4246ba8c0 CR3: 00000001d55b2000 CR4: 00000000003406e0
Feb 22 12:31:30 snorre kernel: [ 3076.304996] kernel tried to execute NX-protected page - exploit attempt? (uid: 0)
Feb 22 12:31:30 snorre kernel: [ 3076.304998] BUG: unable to handle kernel paging request at ffffafad0176bc58
Feb 22 12:31:30 snorre kernel: [ 3076.304999] PGD 216550067 P4D 216550067 PUD 216551067 PMD 20cf6a067 PTE 80000001f749f163
Feb 22 12:31:30 snorre kernel: [ 3076.305004] Oops: 0011 [#2] SMP NOPTI
Feb 22 12:31:30 snorre kernel: [ 3076.305006] CPU: 1 PID: 1362 Comm: irq/58-nvidia Tainted: P      D    OE     4.20.10-042010-generic #201902150516
Feb 22 12:31:30 snorre kernel: [ 3076.305008] Hardware name: Gigabyte Technology Co., Ltd. B450M DS3H/B450M DS3H-CF, BIOS F4 01/25/2019
Feb 22 12:31:30 snorre kernel: [ 3076.305010] RIP: 0010:0xffffafad0176bc58
Feb 22 12:31:30 snorre kernel: [ 3076.305012] Code: ff ff 0a 46 8d 99 ff ff ff ff 0a 46 8d 99 ff ff ff ff aa 22 8b 99 ff ff ff ff 58 bc 76 01 ad af ff ff e8 bd 76 01 ad af ff ff <11> 00 00 00 00 00 00 00 c0 bc 76 01 ad af ff ff 57 a5 87 98 ff ff
Feb 22 12:31:30 snorre kernel: [ 3076.305013] RSP: 0018:ffffafad0176be98 EFLAGS: 00010286
Feb 22 12:31:30 snorre kernel: [ 3076.305015] RAX: ffffafad0176bc58 RBX: ffff9bcbb6eb9700 RCX: ffffafad0176bec0
Feb 22 12:31:30 snorre kernel: [ 3076.305017] RDX: ffffafad0176bec0 RSI: 0000000000000000 RDI: ffffafad0176bec0
Feb 22 12:31:30 snorre kernel: [ 3076.305018] RBP: ffffafad0176bed0 R08: 0000000000000000 R09: 0000000000000000
Feb 22 12:31:30 snorre kernel: [ 3076.305019] R10: 000000000000000f R11: ffffffff9a1294ad R12: ffff9bcbb6eb9700
Feb 22 12:31:30 snorre kernel: [ 3076.305021] R13: ffff9bcbb6eba200 R14: ffffffff9a1232a0 R15: 0000000000000000
Feb 22 12:31:30 snorre kernel: [ 3076.305023] FS:  0000000000000000(0000) GS:ffff9bcbd6a40000(0000) knlGS:0000000000000000
Feb 22 12:31:30 snorre kernel: [ 3076.305024] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 22 12:31:30 snorre kernel: [ 3076.305026] CR2: ffffafad0176bc58 CR3: 00000001d55b2000 CR4: 00000000003406e0
Feb 22 12:31:30 snorre kernel: [ 3076.305027] Call Trace:
Feb 22 12:31:30 snorre kernel: [ 3076.305030]  ? task_work_run+0x9d/0xc0
Feb 22 12:31:30 snorre kernel: [ 3076.305033]  do_exit+0x2de/0xb30
Feb 22 12:31:30 snorre kernel: [ 3076.305036]  ? kthread+0x120/0x140
Feb 22 12:31:30 snorre kernel: [ 3076.305039]  rewind_stack_do_exit+0x17/0x20
Feb 22 12:31:30 snorre kernel: [ 3076.305041] Modules linked in: hid_sony ff_memless hidp rfcomm nfsv3 nfs_acl rpcsec_gss_krb5 auth_rpcgss nfsv4 nfs lockd grace fscache cmac bnep nls_iso8859_1 snd_hda_codec_hdmi nvidia_uvm(OE) edac_mce_amd ccp kvm irqbypass nvidia_drm(POE) nvidia_modeset(POE) crct10dif_pclmul crc32_pclmul nvidia(POE) ghash_clmulni_intel snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_hda_intel snd_seq_dummy snd_hda_codec snd_hda_core snd_usbmidi_lib snd_seq_oss snd_hwdep snd_seq_midi snd_seq_midi_event snd_rawmidi aesni_intel aes_x86_64 crypto_simd btusb cryptd glue_helper btrtl drm_kms_helper btbcm btintel snd_seq snd_pcm drm serio_raw bluetooth drm_panel_orientation_quirks ipmi_devintf ipmi_msghandler wmi_bmof joydev snd_seq_device cfbfillrect input_leds snd_timer cfbimgblt ecdh_generic k10temp cfbcopyarea fb_sys_fops syscopyarea snd sysfillrect sysimgblt fb fbdev soundcore mac_hid sch_fq_codel parport_pc sunrpc ppdev lp parport ip_tables x_tables autofs4 hid_logitech_hidpp hid_logitech_dj
Feb 22 12:31:30 snorre kernel: [ 3076.305065]  hid_generic usbhid hid psmouse i2c_piix4 r8169 i2c_core ahci realtek libahci wmi video gpio_amdpt gpio_generic
Feb 22 12:31:30 snorre kernel: [ 3076.305072] CR2: ffffafad0176bc58
Feb 22 12:31:30 snorre kernel: [ 3076.305073] ---[ end trace 88c812bb0b4a27fd ]---
Feb 22 12:31:30 snorre kernel: [ 3076.305334] RIP: 0010:_nv017125rm+0x40/0x70 [nvidia]
Feb 22 12:31:30 snorre kernel: [ 3076.305337] Code: 48 85 c0 75 36 48 c7 c6 80 c8 00 c1 e8 39 88 08 00 49 89 c4 31 c0 48 85 db 74 04 48 8b 43 68 48 89 c7 ff 90 20 01 00 00 48 83 <c4> 08 4c 89 e7 89 c6 5b 41 5c 31 d2 e9 9f 58 e2 ff 48 89 df be cb
Feb 22 12:31:30 snorre kernel: [ 3076.305338] RSP: 0018:ffffafad0176bd08 EFLAGS: 00010213
Feb 22 12:31:30 snorre kernel: [ 3076.305340] RAX: ffff9bcbba5c9010 RBX: ffff9bcbba5c9010 RCX: ffff9bcbb6e84008
Feb 22 12:31:30 snorre kernel: [ 3076.305341] RDX: ffffffffc100c800 RSI: 00000000007ef3cb RDI: ffff9bcbb6e84008
Feb 22 12:31:30 snorre kernel: [ 3076.305343] RBP: ffff9bcbb53cdc60 R08: 0000000000000005 R09: ffffffffc100ccc0
Feb 22 12:31:30 snorre kernel: [ 3076.305344] R10: ffff9bcbb53cdeb0 R11: ffffffffc0c60940 R12: ffff9bcbb6e84008
Feb 22 12:31:30 snorre kernel: [ 3076.305346] R13: ffff9bcbcd63a808 R14: ffff9bcbd2ed7008 R15: ffff9bcbcf37d408
Feb 22 12:31:30 snorre kernel: [ 3076.305347] FS:  0000000000000000(0000) GS:ffff9bcbd6a40000(0000) knlGS:0000000000000000
Feb 22 12:31:30 snorre kernel: [ 3076.305349] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 22 12:31:30 snorre kernel: [ 3076.305350] CR2: ffffafad0176bc58 CR3: 00000001d55b2000 CR4: 00000000003406e0
Feb 22 12:31:30 snorre kernel: [ 3076.305352] Fixing recursive fault but reboot is needed!


---

