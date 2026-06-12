---
title: "nvidia GTS 360m overheating and glitches"
date: 2019-01-18
forum: Hardware
---

### Post by elgolmon on 2019-01-18
Hey,

I am new to Ubuntu. and I got some problems with my lamtop and Nvidia drivers ; it keep overheating whereas when I'm chosing Nvidia. I tried to update from Nvidia official website but somehow, I still have old versions in "software and updates" :confused: I have drivers 340.107 whereas Nvidia proposes 340.32. 

This is one thing, as I was fed up, I chose "open source drivers" which does not keep my GPU overheating anymore ; but I have some glitches on my screen, see picture below.

[IMG]https://i.ibb.co/Zg58sKN/IMG-20190118-133217.jpg[/IMG]


Please find some information about my config here :



```
antoine@antoine-G60JX:~$ dmesg -k -l emerg,alert,crit,err,warn
[    0.036000] core: CPUID marked event: 'bus cycles' unavailable
[    0.036330]  #2 #3
[    0.218923] pci 0000:07:00.0: [Firmware Bug]: disabling VPD access (can't determine size of non-standard VPD format)
[    1.432760] sdhci-pci 0000:06:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[   49.251361] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   50.807618] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   51.797072] nvidia: loading out-of-tree module taints kernel.
[   51.797093] nvidia: module license 'NVIDIA' taints kernel.
[   51.797094] Disabling lock debugging due to kernel taint
[   51.811092] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.107  Thu May 24 21:54:01 PDT 2018
[   52.784104] uvcvideo 1-1.6:1.0: Entity type for entity Extension 5 was not initialized!
[   52.784107] uvcvideo 1-1.6:1.0: Entity type for entity Extension 4 was not initialized!
[   52.784108] uvcvideo 1-1.6:1.0: Entity type for entity Processing 3 was not initialized!
[   52.784110] uvcvideo 1-1.6:1.0: Entity type for entity Camera 1 was not initialized!
[   53.311575] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000d3fff window]
[   53.311712] caller os_map_kernel_space+0x86/0xb0 [nvidia] mapping multiple BARs
[   54.027089] NVRM: Your system is not currently configured to drive a VGA console
[   54.027092] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   54.027093] NVRM: requires the use of a text-mode VGA console. Use of other console
[   54.027094] NVRM: drivers including, but not limited to, vesafb, may result in
[   54.027095] NVRM: corruption and stability problems, and is not supported.
[   83.435236] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000d3fff window]
[   83.435404] caller os_map_kernel_space+0x86/0xb0 [nvidia] mapping multiple BARs
[   84.033452] ------------[ cut here ]------------
[   84.033458] Bad or missing usercopy whitelist? Kernel memory exposure attempt detected from SLUB object 'nvidia_stack_t' (offset 11864, size 3)!
[   84.033474] WARNING: CPU: 0 PID: 1231 at mm/usercopy.c:81 usercopy_warn+0x81/0xa0
[   84.033475] Modules linked in: ccm bnep btusb btrtl btbcm uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 btintel bluetooth videobuf2_common nvidia_uvm(POE) videodev media ecdh_generic nvidia(POE) snd_hda_codec_hdmi snd_hda_codec_realtek arc4 intel_powerclamp kvm_intel snd_hda_codec_generic iwldvm mac80211 snd_hda_intel snd_hda_codec kvm drm snd_seq_midi snd_seq_midi_event gpio_ich snd_hda_core snd_rawmidi snd_hwdep irqbypass iwlwifi snd_seq snd_pcm intel_cstate snd_seq_device intel_ips joydev input_leds serio_raw snd_timer cfg80211 snd lpc_ich soundcore asus_laptop input_polldev mei_me mei mac_hid shpchp sch_fq_codel sparse_keymap wmi coretemp parport_pc ppdev lp parport ip_tables x_tables autofs4 firewire_ohci ahci psmouse i2c_i801 libahci atl1c firewire_core sdhci_pci cqhci crc_itu_t
[   84.033525]  sdhci video
[   84.033530] CPU: 0 PID: 1231 Comm: Xorg Tainted: P           OE     4.17.19-041719-generic #201808240919
[   84.033531] Hardware name: ASUSTek Computer Inc. G60JX/G60JX, BIOS 204 12/25/2009
[   84.033533] RIP: 0010:usercopy_warn+0x81/0xa0
[   84.033534] RSP: 0018:ffffb42f411a3b60 EFLAGS: 00010286
[   84.033536] RAX: 0000000000000000 RBX: ffff9b418810ae58 RCX: 0000000000000006
[   84.033537] RDX: 0000000000000007 RSI: 0000000000000082 RDI: ffff9b4197c164b0
[   84.033538] RBP: ffffb42f411a3b78 R08: 0000000000000001 R09: 0000000000000381
[   84.033538] R10: 0000000000000004 R11: 0000000000000000 R12: 0000000000000003
[   84.033539] R13: 0000000000000001 R14: ffff9b418810ae5b R15: ffff9b418810aea0
[   84.033541] FS:  00007f2327f04600(0000) GS:ffff9b4197c00000(0000) knlGS:0000000000000000
[   84.033542] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   84.033543] CR2: 00007f231ee6c160 CR3: 00000000d7f84000 CR4: 00000000000006f0
[   84.033544] Call Trace:
[   84.033552]  __check_heap_object+0xc2/0x110
[   84.033554]  __check_object_size+0x14c/0x178
[   84.033715]  os_memcpy_to_user+0x26/0x50 [nvidia]
[   84.033804]  _nv001372rm+0xa5/0x260 [nvidia]
[   84.033807] WARNING: kernel stack frame pointer at 00000000a58f4ac1 in Xorg:1231 has bad value 00000000104bcb29
[   84.033808] unwind stack type:0 next_sp:          (null) mask:0x2 graph_idx:0
[   84.033810] 00000000f0b6722e: ffffb42f411a3b88 (0xffffb42f411a3b88)
[   84.033812] 000000009c16d9f4: ffffffff9bc61b92 (__check_heap_object+0xc2/0x110)
[   84.033813] 000000007e4f95c3: ffffb42f411a3bb8 (0xffffb42f411a3bb8)
[   84.033815] 00000000f303b038: ffffffff9bc89adc (__check_object_size+0x14c/0x178)
[   84.033816] 000000002746ba55: 0000000000000003 (0x3)
[   84.033817] 0000000039fa93e1: ffff9b418810ae58 (0xffff9b418810ae58)
[   84.033818] 000000008f3a8999: 0000561d69fa7650 (0x561d69fa7650)
[   84.033819] 000000000d51fdb9: ffff9b418810ae58 (0xffff9b418810ae58)
[   84.033820] 000000006f82fbb7: ffffb42f411a3be0 (0xffffb42f411a3be0)
[   84.033898] 0000000034a92111: ffffffffc0ee3e66 (os_memcpy_to_user+0x26/0x50 [nvidia])
[   84.033899] 00000000bbe2a06a: 0000000000000003 (0x3)
[   84.033900] 000000005d7a7de2: 0000000000000000 ...
[   84.033900] 00000000deb10cbd: 0000561d69fa7650 (0x561d69fa7650)
[   84.033901] 00000000a58f4ac1: ffff9b418810ae50 (0xffff9b418810ae50)
[   84.033989] 0000000055352b6e: ffffffffc0e69d15 (_nv001372rm+0xa5/0x260 [nvidia])
[   84.033990] 0000000098a3b6c2: 0000000000000000 ...
[   84.033991] 00000000b7d0f1a8: ffff9b41534e26e8 (0xffff9b41534e26e8)
[   84.033992] 000000008b4db637: ffff9b418810aed8 (0xffff9b418810aed8)
[   84.033993] 000000006ba65d7e: ffff9b418810ae80 (0xffff9b418810ae80)
[   84.034093] 000000009b605fec: ffffffffc0ae888a (_nv004784rm+0x4eba/0x5500 [nvidia])
[   84.034094] 0000000076db9c47: 0000000000000000 ...
[   84.034095] 000000008da68d6e: ffff9b418810aed8 (0xffff9b418810aed8)
[   84.034096] 00000000376f888a: 00007ffdaf872020 (0x7ffdaf872020)
[   84.034196] 00000000f66c3d54: ffffffffc0ae8fbc (_nv004331rm+0xec/0xf0 [nvidia])
[   84.034197] 00000000c806c33a: ffff9b418810aed8 (0xffff9b418810aed8)
[   84.034198] 00000000b188c192: ffff9b41535f2008 (0xffff9b41535f2008)
[   84.034199] 00000000ee473ee9: 0000000000000010 (0x10)
[   84.034200] 00000000817a9f26: 00007ffdaf872020 (0x7ffdaf872020)
[   84.034201] 0000000023ab078c: 00000000c1d00041 (0xc1d00041)
[   84.034300] 000000003ec0e880: ffffffffc0ad263a (_nv004326rm+0xca/0x650 [nvidia])
[   84.034301] 0000000052de5916: 00000000c1d00041 (0xc1d00041)
[   84.034302] 00000000d99c6b70: ffff9b418810aed8 (0xffff9b418810aed8)
[   84.034302] 00000000fff44bed: 0000000000000000 ...
[   84.034388] 00000000a6c7cb1e: ffffffffc0e84ef6 (_nv015126rm+0x576/0x5c0 [nvidia])
[   84.034389] 000000000af87373: ffff9b41534e27a0 (0xffff9b41534e27a0)
[   84.034390] 000000002cb838ac: ffff9b41534e27a0 (0xffff9b41534e27a0)
[   84.034391] 00000000c4f943df: ffff9b419199fd00 (0xffff9b419199fd00)
[   84.034392] 00000000c053c8d3: 000000000000002a (0x2a)
[   84.034393] 00000000a08a9ebf: ffff9b419199fd00 (0xffff9b419199fd00)
[   84.034481] 000000004c723573: ffffffffc0e6b25e (_nv000694rm+0x2e/0x60 [nvidia])
[   84.034551] 00000000e05ccb6e: ffffffffc12dd260 (nv_ctl_waitqueue+0x20/0xffffffffffc09dc0 [nvidia])
[   84.034553] 000000004df5c915: ffff9b41534e27a0 (0xffff9b41534e27a0)
[   84.034553] 00000000aba90f85: ffff9b419199fd00 (0xffff9b419199fd00)
[   84.034633] 00000000e77e9e1b: ffffffffc0ec2a95 (_nv000789rm+0x5f5/0x8b0 [nvidia])
[   84.034634] 0000000024ecd992: ffff9b418810aff8 (0xffff9b418810aff8)
[   84.034634] 00000000eb84ad6d: 0000000000000020 (0x20)
[   84.034635] 00000000d09bd05e: ffff9b4188108000 (0xffff9b4188108000)
[   84.034636] 0000000087318434: ffff9b41534e27a0 (0xffff9b41534e27a0)
[   84.034637] 000000003b1aef1c: 000000000000002a (0x2a)
[   84.034715] 00000000410bbb29: ffffffffc0eccdd3 (rm_ioctl+0x73/0x100 [nvidia])
[   84.034716] 00000000524f5746: ffffb42f411a3e28 (0xffffb42f411a3e28)
[   84.034786] 000000007ea6701e: ffffffffc12dd260 (nv_ctl_waitqueue+0x20/0xffffffffffc09dc0 [nvidia])
[   84.034787] 0000000091c0a639: 00000000000004cf (0x4cf)
[   84.034788] 00000000df0e94d6: 157af889b69385a0 (0x157af889b69385a0)
[   84.034789] 00000000b5bafd5b: 157af88aa4feada0 (0x157af88aa4feada0)
[   84.034790] 00000000e6e5fee0: 157af88aa4feada0 (0x157af88aa4feada0)
[   84.034791] 000000000d85146e: 157af88a2dc919a0 (0x157af88a2dc919a0)
[   84.034791] 00000000035b985c: 0000000000000000 ...
[   84.034792] 000000005e8da001: 0000000000000200 (0x200)
[   84.034793] 000000008b6e3d93: 0000002000000000 (0x2000000000)
[   84.034794] 00000000331be9c4: ffffb42f411a3d20 (0xffffb42f411a3d20)
[   84.034795] 00000000012ab091: 00000000000004cf (0x4cf)
[   84.034796] 00000000c07cc6b0: 00000000000004cf (0x4cf)
[   84.034797] 00000000c73650ef: ffffb42f411a3d00 (0xffffb42f411a3d00)
[   84.034797] 000000001edd8b01: 0000000000000000 ...
[   84.034800] 00000000d70bf35b: ffffffff9bc89a31 (__check_object_size+0xa1/0x178)
[   84.034800] 000000000bce9e29: 0000000000000020 (0x20)
[   84.034801] 000000006c2f4fef: ffff9b419199fd00 (0xffff9b419199fd00)
[   84.034802] 00000000c56e73f7: ffff9b41534e27a0 (0xffff9b41534e27a0)
[   84.034803] 00000000b5cd0087: ffff9b419199fd38 (0xffff9b419199fd38)
[   84.034874] 0000000058837bf1: ffffffffc12dd260 (nv_ctl_waitqueue+0x20/0xffffffffffc09dc0 [nvidia])
[   84.034951] 000000009aaa7668: ffffffffc0edb3b0 (nvidia_ioctl+0x220/0x460 [nvidia])
[   84.034952] 00000000d7724d8b: ffff9b4188108000 (0xffff9b4188108000)
[   84.034953] 000000006ebb194e: 00007ffdaf871f90 (0x7ffdaf871f90)
[   84.034954] 000000009e6433ad: 000000200000002a (0x200000002a)
[   84.034955] 00000000b1332d1a: ffff9b4191e37c00 (0xffff9b4191e37c00)
[   84.034956] 000000000c3d07a3: ffffb42f411a3e00 (0xffffb42f411a3e00)
[   84.034957] 000000009449ef44: 4173cce8136faa00 (0x4173cce8136faa00)
[   84.034958] 000000008abb8a92: 00000000000000ff (0xff)
[   84.034959] 00000000c4de4894: 00007ffdaf871f90 (0x7ffdaf871f90)
[   84.034960] 000000007a789e6c: 000000000000000f (0xf)
[   84.034960] 00000000d07e0b71: ffff9b4157e55100 (0xffff9b4157e55100)
[   84.034961] 0000000020d01226: 00007ffdaf871f90 (0x7ffdaf871f90)
[   84.034962] 00000000de35fcf0: ffffb42f411a3e48 (0xffffb42f411a3e48)
[   84.035039] 000000007e704f5a: ffffffffc0ee6b42 (nvidia_frontend_ioctl+0x32/0x70 [nvidia])
[   84.035040] 000000007747737c: ffff9b418d959c38 (0xffff9b418d959c38)
[   84.035041] 0000000081844cca: 00007ffdaf871f90 (0x7ffdaf871f90)
[   84.035042] 00000000e7523eb5: ffffb42f411a3e58 (0xffffb42f411a3e58)
[   84.035119] 0000000088582805: ffffffffc0ee6b9d (nvidia_frontend_unlocked_ioctl+0x1d/0x30 [nvidia])
[   84.035120] 00000000bb384375: ffffb42f411a3ed8 (0xffffb42f411a3ed8)
[   84.035122] 00000000d018971d: ffffffff9bca6b18 (do_vfs_ioctl+0xa8/0x610)
[   84.035123] 00000000daeb87e2: 0000000000000000 ...
[   84.035124] 00000000f4b67c9d: 4173cce8136faa00 (0x4173cce8136faa00)
[   84.035125] 00000000cfd33063: 0000000000000002 (0x2)
[   84.035126] 00000000c4d7d2f4: ffff9b4157e6e800 (0xffff9b4157e6e800)
[   84.035127] 00000000841c8768: ffff9b40b4a93c68 (0xffff9b40b4a93c68)
[   84.035128] 0000000070dc22ba: ffff9b4157e6e810 (0xffff9b4157e6e810)
[   84.035128] 0000000027d9bfef: 0000000000000035 (0x35)
[   84.035129] 0000000019c74497: ffffb42f411a3ed8 (0xffffb42f411a3ed8)
[   84.035130] 000000004fcde274: 4173cce8136faa00 (0x4173cce8136faa00)
[   84.035131] 00000000b1b61f23: ffff9b4157e55100 (0xffff9b4157e55100)
[   84.035132] 00000000323444eb: ffff9b4157e55100 (0xffff9b4157e55100)
[   84.035133] 0000000032c90f0d: 000000000000000f (0xf)
[   84.035134] 00000000f53f6948: 00000000c020462a (0xc020462a)
[   84.035135] 00000000287449af: 00007ffdaf871f90 (0x7ffdaf871f90)
[   84.035136] 00000000207f4017: ffffb42f411a3f18 (0xffffb42f411a3f18)
[   84.035137] 000000008ef41d89: ffffffff9bca70e7 (ksys_ioctl+0x67/0x90)
[   84.035138] 000000003dab60d9: 000000000000244f (0x244f)
[   84.035138] 0000000053361910: 0000000000000000 ...
[   84.035139] 000000009b157dd1: ffffb42f411a3f58 (0xffffb42f411a3f58)
[   84.035140] 00000000e91346a3: 0000000000000000 ...
[   84.035141] 00000000e9a4ba1e: ffffb42f411a3f28 (0xffffb42f411a3f28)
[   84.035142] 000000008ab3b85f: ffffffff9bca712a (__x64_sys_ioctl+0x1a/0x20)
[   84.035143] 00000000b787350f: ffffb42f411a3f48 (0xffffb42f411a3f48)
[   84.035148] 000000009a486213: ffffffff9ba0423a (do_syscall_64+0x5a/0x110)
[   84.035148] 0000000031cee051: 0000000000000000 ...
[   84.035153] 0000000064bcc83b: ffffffff9c400088 (entry_SYSCALL_64_after_hwframe+0x44/0xa9)
[   84.035154] 000000004ec3a026: 000000000000002a (0x2a)
[   84.035155] 000000003666b40f: 0000000000000020 (0x20)
[   84.035156] 0000000034d483b0: 00000000c020462a (0xc020462a)
[   84.035157] 000000008641168b: 00007ffdaf871fac (0x7ffdaf871fac)
[   84.035158] 00000000498f025e: 00007ffdaf871f90 (0x7ffdaf871f90)
[   84.035159] 00000000615a7f47: 000000005c41e664 (0x5c41e664)
[   84.035160] 0000000086c50524: 0000000000003246 (0x3246)
[   84.035160] 00000000865219b5: 0000561d69f5f010 (0x561d69f5f010)
[   84.035161] 00000000a40f940a: 00007ffdaf871fac (0x7ffdaf871fac)
[   84.035162] 00000000bc9a31a1: 00007ffdaf871f90 (0x7ffdaf871f90)
[   84.035163] 00000000adf499fb: ffffffffffffffda (0xffffffffffffffda)
[   84.035164] 00000000636a875d: 00007f23252ff5d7 (0x7f23252ff5d7)
[   84.035165] 000000004f87750e: 00007ffdaf871f90 (0x7ffdaf871f90)
[   84.035166] 00000000ee29c867: 00000000c020462a (0xc020462a)
[   84.035167] 00000000e8c3541d: 000000000000000f (0xf)
[   84.035167] 0000000032f3899a: 0000000000000010 (0x10)
[   84.035168] 0000000047853978: 00007f23252ff5d7 (0x7f23252ff5d7)
[   84.035169] 00000000062415b3: 0000000000000033 (0x33)
[   84.035170] 000000003926c8c8: 0000000000003246 (0x3246)
[   84.035171] 000000003f72f578: 00007ffdaf871ef8 (0x7ffdaf871ef8)
[   84.035172] 00000000bb93bd7e: 000000000000002b (0x2b)
[   84.035273]  ? _nv004784rm+0x4eba/0x5500 [nvidia]
[   84.035374]  ? _nv004331rm+0xec/0xf0 [nvidia]
[   84.035473]  ? _nv004326rm+0xca/0x650 [nvidia]
[   84.035559]  ? _nv015126rm+0x576/0x5c0 [nvidia]
[   84.035647]  ? _nv000694rm+0x2e/0x60 [nvidia]
[   84.035727]  ? _nv000789rm+0x5f5/0x8b0 [nvidia]
[   84.035805]  ? rm_ioctl+0x73/0x100 [nvidia]
[   84.035808]  ? __check_object_size+0xa1/0x178
[   84.035885]  ? nvidia_ioctl+0x220/0x460 [nvidia]
[   84.035963]  ? nvidia_frontend_ioctl+0x32/0x70 [nvidia]
[   84.036052]  ? nvidia_frontend_unlocked_ioctl+0x1d/0x30 [nvidia]
[   84.036055]  ? do_vfs_ioctl+0xa8/0x610
[   84.036057]  ? ksys_ioctl+0x67/0x90
[   84.036058]  ? __x64_sys_ioctl+0x1a/0x20
[   84.036060]  ? do_syscall_64+0x5a/0x110
[   84.036062]  ? entry_SYSCALL_64_after_hwframe+0x44/0xa9
[   84.036064] Code: 9c b0 9c 41 51 4d 89 d8 48 c7 c0 c2 90 af 9c 49 89 f1 48 89 f9 48 0f 45 c2 48 c7 c7 b8 9c b0 9c 4c 89 d2 48 89 c6 e8 81 49 e0 ff <0f> 0b 48 83 c4 18 c9 c3 48 c7 c6 62 56 af 9c 49 89 f1 49 89 f3 
[   84.036092] ---[ end trace a770ad762cefd733 ]---
[ 4280.444714] kauditd_printk_skb: 38 callbacks suppressed
[ 5234.035997] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 5264.033046] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 5282.897181] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 5299.037383] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 5315.036579] Bluetooth: hci0: last event is not cmd complete (0x0f)
```


```
antoine@antoine-G60JX:~$ inxi -Fxxxz -v 7
System:    Host: antoine-G60JX Kernel: 4.17.19-041719-generic x86_64
           bits: 64 gcc: 8.2.0
           Desktop: Gnome 3.28.3 (Gtk 3.22.30-1ubuntu1) info: gnome-shell dm: gdm3
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: ASUSTek product: G60JX v: 1.0 serial: N/A
           Mobo: PEGATRON model: G60JX v: 1.0 serial: N/A
           BIOS: American Megatrends v: 204 date: 12/25/2009
Battery    BAT0: charge: 19.5 Wh 98.6% condition: 19.8/50.6 Wh (39%)
           volts: 12.3/11.1
           model: G60JX M50--24 Li-ion serial: N/A status: N/A cycles: 0
CPU:       Dual core Intel Core i5 M 430 (-MT-MCP-) 
           arch: Nehalem rev.2 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9066
           clock speeds: min/max: 1199/2267 MHz 1: 1268 MHz 2: 1345 MHz
           3: 1249 MHz 4: 1206 MHz
Memory:    Using dmidecode: root required for dmidecode
Graphics:  Card: NVIDIA GT215M [GeForce GTS 360M]
           bus-ID: 01:00.0 chip-ID: 10de:0cb1
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: N/A version: N/A Direct Render: N/A
Audio:     Card-1 NVIDIA High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1 chip-ID: 10de:0be4
           Card-2 Intel 5 Series/3400 Series High Def. Audio
           driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:3b56
           Sound: ALSA v: k4.17.19-041719-generic
Network:   Card-1: Intel Centrino Wireless-N 1000 [Condor Peak]
           driver: iwlwifi bus-ID: 03:00.0 chip-ID: 8086:0083
           IF: wlp3s0 state: up mac: <filter>
           Card-2: Qualcomm Atheros AR8131 Gigabit Ethernet
           driver: atl1c v: 1.0.1.1-NAPI port: b000
           bus-ID: 07:00.0 chip-ID: 1969:1063
           IF: enp7s0 state: down mac: <filter>
           WAN IP: <filter>
           IF: enp7s0 ip-v4: N/A ip-v6-link: N/A
           IF: wlp3s0 ip-v4: <filter> ip-v6-link: <filter>
Drives:    HDD Total Size: 1000.2GB (0.9% used)
           ID-1: /dev/sda model: WDC_WD10JPVX size: 1000.2GB serial: <filter>
           Optical-1: /dev/sr0 model: TSST CDDVDW TS-L633C
           rev: AS01 dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 24x multisession: yes
           audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram state: running
Partition: ID-1: / size: 915G used: 7.8G (1%) fs: ext4 dev: /dev/dm-0
           label: N/A uuid: ce90dd6d-42b6-4a3b-96e6-f014f68c45c1
           ID-2: swap-1 size: 1.02GB used: 0.00GB (0%)
           fs: swap dev: /dev/dm-1
           label: N/A uuid: e456850b-b488-40b7-a0e4-663f04cf61d8
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Unmounted: ID-1: /dev/sda1 size: 1000.20G label: N/A uuid: N/A
Sensors:   System Temperatures: cpu: 50.0C mobo: N/A gpu: 0.0:89C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 238 Uptime: 1:36 Memory: 2090.9/3807.8MB
           Init: systemd v: 237 runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191 running in gnome-terminal-) inxi: 2.3.56 
```


Thanks for your help


edit : I tried to update my paquets with synaptic, now I have a ****** resolution, impossible to change

---

### Post by Autodave on 2019-01-19
Did it overheat before the upgrade?  Upgrading one release to another seldom works properly.  I learned a long time ago to backup everything and do clean installs.

Also, don't use the drivers obtained directly from Nvidia: that just causes problems when the machine updates.  Some specs on your machine like amount of RAM would be helpful.  Ubuntu is a very heavy desktop and you may want to think about switching to a lighter one such as Xubuntu.

---

