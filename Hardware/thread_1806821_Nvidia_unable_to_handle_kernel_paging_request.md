---
title: "Nvidia: unable to handle kernel paging request"
date: 2011-07-18
forum: Hardware
---

### Post by kwurzel on 2011-07-18
I'm having huge problems running any version of Ubuntu (10.04 to 11.10) on a Fujitsu CELSIUS R670. Every time I start up X.org, I get the following syslog: (Nvidia Quadro NVS 295)

```
Jul 18 13:34:16 apollo34 kernel: [  373.499027] init: plymouth-stop pre-start process (1599) terminated with status 1
Jul 18 13:34:17 apollo34 udevd[470]: timeout: killing '/sbin/modprobe -bv pci:v000010ECd0000816Csv00001734sd00001178bc0Csc07i01' [478]
Jul 18 13:34:17 apollo34 kernel: [  374.377728] BUG: unable to handle kernel paging request at ffffc900033df000
Jul 18 13:34:17 apollo34 kernel: [  374.377733] IP: [<ffffffffa01abfa9>] _nv022543rm+0x127/0x202 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.377855] PGD 23f80e067 PUD 43f803067 PMD 4333ea067 PTE 0
Jul 18 13:34:17 apollo34 kernel: [  374.377858] Oops: 0000 [#1] SMP 
Jul 18 13:34:17 apollo34 kernel: [  374.377860] CPU 0 
Jul 18 13:34:17 apollo34 kernel: [  374.377861] Modules linked in: parport_pc ppdev tpm_infineon psmouse snd_hda_codec_realtek nvidia(P) mxm_wmi appletalk ipx serio_raw p8023 snd_hda_intel snd_hda_codec snd_hwdep tpm_tis tpm snd_pcm tpm_bios snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd i7core_edac lp parport ipmi_si(+) soundcore ipmi_msghandler edac_core snd_page_alloc usbhid hid firewire_ohci mptsas firewire_core crc_itu_t mptscsih ahci libahci mptbase r8169 scsi_transport_sas
Jul 18 13:34:17 apollo34 kernel: [  374.377883] 
Jul 18 13:34:17 apollo34 kernel: [  374.377885] Pid: 1604, comm: Xorg Tainted: P            3.0-3-generic #4-Ubuntu FUJITSU                          CELSIUS R670-2                /D2618-C1
Jul 18 13:34:17 apollo34 kernel: [  374.377888] RIP: 0010:[<ffffffffa01abfa9>]  [<ffffffffa01abfa9>] _nv022543rm+0x127/0x202 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.377951] RSP: 0018:ffff88022f1df8b8  EFLAGS: 00010206
Jul 18 13:34:17 apollo34 kernel: [  374.377953] RAX: 00000000000000b9 RBX: ffffc900033def47 RCX: 000000000000001e
Jul 18 13:34:17 apollo34 kernel: [  374.377954] RDX: 000000000000010c RSI: 0000000000000000 RDI: 0000000000000000
Jul 18 13:34:17 apollo34 kernel: [  374.377956] RBP: ffff88022f9f5f10 R08: 00000000bf7c2fff R09: ffff880000000000
Jul 18 13:34:17 apollo34 kernel: [  374.377957] R10: 0000000000000001 R11: 0000000000000000 R12: ffff880428668800
Jul 18 13:34:17 apollo34 kernel: [  374.377958] R13: 00000000bf7baf47 R14: 00000000bf7baf47 R15: 0000000000000000
Jul 18 13:34:17 apollo34 kernel: [  374.377960] FS:  00007f03a15b28a0(0000) GS:ffff88023fc00000(0000) knlGS:0000000000000000
Jul 18 13:34:17 apollo34 kernel: [  374.377962] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul 18 13:34:17 apollo34 kernel: [  374.377963] CR2: ffffc900033df000 CR3: 00000004324f6000 CR4: 00000000000006f0
Jul 18 13:34:17 apollo34 kernel: [  374.377965] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul 18 13:34:17 apollo34 kernel: [  374.377966] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul 18 13:34:17 apollo34 kernel: [  374.377968] Process Xorg (pid: 1604, threadinfo ffff88022f1de000, task ffff88022fa92de0)
Jul 18 13:34:17 apollo34 kernel: [  374.377969] Stack:
Jul 18 13:34:17 apollo34 kernel: [  374.377970]  ffff880428669000 ffff880428668800 ffff880428669000 ffff880232498000
Jul 18 13:34:17 apollo34 kernel: [  374.377972]  0000000000000018 ffffffffa01ac304 ffff880232ea9000 ffff880232ea9000
Jul 18 13:34:17 apollo34 kernel: [  374.377975]  ffff880232498000 ffffffffa01a7528 ffff880232ea9000 ffff880232498000
Jul 18 13:34:17 apollo34 kernel: [  374.377977] Call Trace:
Jul 18 13:34:17 apollo34 kernel: [  374.378040]  [<ffffffffa01ac304>] ? _nv022559rm+0x76/0x9e [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378103]  [<ffffffffa01a7528>] ? _nv022516rm+0xcf/0x301 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378165]  [<ffffffffa01a7805>] ? _nv022566rm+0xab/0x174 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378226]  [<ffffffffa01a791e>] ? _nv022515rm+0x50/0x5d [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378289]  [<ffffffffa01ae58d>] ? _nv022507rm+0x6e/0x78 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378401]  [<ffffffffa07bda74>] ? _nv019299rm+0x69/0x121 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378507]  [<ffffffffa07bd9f2>] ? _nv019313rm+0xe8/0x101 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378579]  [<ffffffffa01ea211>] ? _nv004710rm+0x68/0x1f4 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378713]  [<ffffffffa058462d>] ? _nv015076rm+0x176/0x4c3 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378848]  [<ffffffffa05831b8>] ? _nv015378rm+0xe9/0x165 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.378905]  [<ffffffffa01723b5>] ? _nv015558rm+0xd/0x12 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.379012]  [<ffffffffa07bd7b9>] ? _nv002413rm+0x19d/0x28a [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.379119]  [<ffffffffa07be828>] ? _nv002407rm+0x4a5/0x684 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.379226]  [<ffffffffa07c5724>] ? rm_init_adapter+0x9e/0x1b6 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.379332]  [<ffffffffa07e4c74>] ? nv_kern_open+0x414/0x7a0 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.379336]  [<ffffffff81168d50>] ? mount_fs+0x1b0/0x1b0
Jul 18 13:34:17 apollo34 kernel: [  374.379338]  [<ffffffff8116979a>] ? chrdev_open+0xda/0x230
Jul 18 13:34:17 apollo34 kernel: [  374.379342]  [<ffffffff81163312>] ? __dentry_open+0x132/0x310
Jul 18 13:34:17 apollo34 kernel: [  374.379344]  [<ffffffff811696c0>] ? cdev_put+0x30/0x30
Jul 18 13:34:17 apollo34 kernel: [  374.379346]  [<ffffffff81164a31>] ? nameidata_to_filp+0x71/0x80
Jul 18 13:34:17 apollo34 kernel: [  374.379348]  [<ffffffff81173440>] ? do_last+0x3a0/0x700
Jul 18 13:34:17 apollo34 kernel: [  374.379351]  [<ffffffff811749ca>] ? path_openat+0xca/0x3f0
Jul 18 13:34:17 apollo34 kernel: [  374.379354]  [<ffffffff815eeaae>] ? _raw_spin_lock+0xe/0x20
Jul 18 13:34:17 apollo34 kernel: [  374.379357]  [<ffffffff81174d32>] ? do_filp_open+0x42/0xa0
Jul 18 13:34:17 apollo34 kernel: [  374.379360]  [<ffffffff812ea021>] ? strncpy_from_user+0x31/0x40
Jul 18 13:34:17 apollo34 kernel: [  374.379362]  [<ffffffff815eeaae>] ? _raw_spin_lock+0xe/0x20
Jul 18 13:34:17 apollo34 kernel: [  374.379364]  [<ffffffff81182047>] ? alloc_fd+0xf7/0x150
Jul 18 13:34:17 apollo34 kernel: [  374.379366]  [<ffffffff81164b2d>] ? do_sys_open+0xed/0x220
Jul 18 13:34:17 apollo34 kernel: [  374.379369]  [<ffffffff811845cf>] ? mntput+0x1f/0x30
Jul 18 13:34:17 apollo34 kernel: [  374.379371]  [<ffffffff81164c80>] ? sys_open+0x20/0x30
Jul 18 13:34:17 apollo34 kernel: [  374.379374]  [<ffffffff815f6e82>] ? system_call_fastpath+0x16/0x1b
Jul 18 13:34:17 apollo34 kernel: [  374.379375] Code: 55 14 48 89 c6 4c 89 ef 41 ff 94 24 78 02 00 00 48 89 c3 48 85 c0 0f 84 b3 00 00 00 b8 00 00 00 00 48 83 7d 08 00 76 12 8b 55 2c <0f> b6 0c 03 00 4d 2b 48 ff c0 48 39 c2 77 f1 80 7d 2b 00 75 7c 
Jul 18 13:34:17 apollo34 kernel: [  374.379393] RIP  [<ffffffffa01abfa9>] _nv022543rm+0x127/0x202 [nvidia]
Jul 18 13:34:17 apollo34 kernel: [  374.379455]  RSP <ffff88022f1df8b8>
Jul 18 13:34:17 apollo34 kernel: [  374.379456] CR2: ffffc900033df000
Jul 18 13:34:17 apollo34 kernel: [  374.379458] ---[ end trace a70cffce926a2f2c ]---
Jul 18 13:34:18 apollo34 udevd[470]: timeout: killing '/sbin/modprobe -bv pci:v000010ECd0000816Csv00001734sd00001178bc0Csc07i01' [478]
```

This one is from Oneiric, but it's the same error on other Versions.

memtest ran for 3 days and detected no errors. Using another (known working) GFX card gives the same errors. I used many combinations of mainline kernels and Nvidia driver versions, not giving an improvement.

Open Source nouveu driver seems to work, but I need the proprietary 

I'm at my wits' end what the problem might be. Anybody got some clues?

---

### Post by andersgb1 on 2011-08-06
I'm in the exact same situation...

---

