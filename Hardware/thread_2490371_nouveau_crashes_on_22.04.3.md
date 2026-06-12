---
title: "nouveau crashes on 22.04.3"
date: 2023-09-01
forum: Hardware
---

### Post by jszigetvari on 2023-09-01
Dear Members,

I have a Kubuntu 22.04(.3) installation on a Lenovo ThinkStation P330 Tiny. In it I have an NVIDIA Corporation GP107GL [Quadro P1000] (rev a1) graphics card, that I use with the default nouveau drivers.
For a few months now, I have been experiencing problems that can be tracked back to the nouveau driver, and things just have gotten worse over time.
Now I have to boot up my machine 3-4 times every day, just to get it running properly. Because it tends to crash after the GUI login.
At first I only saw timeout error messages like:

```
nouveau 0000:01:00.0: fifo: FB_FLUSH_TIMEOUT
fifo: PBDMA0: 00000004 [MEMACK_EXTRA] ch 2 [00ff962000 Xorg[2523]] subc 0 mthd 0e04 data 00f90062
DRM: base-1: timeout
```

And in order to mitigate the problem, I have ceased to play long running youtube videos, then as the problem got worse, I disabled hardware acceleration in all of my browsers, and that improved things for a while too.
Now I seem to have run out of options, and it is really starting to hurt the overall usability of the machine.
Currently, the nouveau crashes produce logs like this:

```
Aug 23 06:58:14 janos-work-host kernel: [    5.509825] fbcon: nouveaudrmfb (fb0) is primary device
Aug 23 06:58:14 janos-work-host kernel: [    7.695620] nouveau 0000:01:00.0: DRM: core notifier timeout
Aug 23 06:58:14 janos-work-host kernel: [    8.487136] nouveau 0000:01:00.0: [drm] fb0: nouveaudrmfb frame buffer device
Aug 23 06:58:14 janos-work-host kernel: [    8.512533] [drm] Initialized nouveau 1.3.1 20120801 for 0000:01:00.0 on minor 1
Aug 23 06:58:14 janos-work-host kernel: [    8.512553] nouveau 0000:01:00.0: DRM: Disabling PCI power management to avoid bug
Aug 23 06:58:14 janos-work-host kernel: [   20.649242] snd_hda_intel 0000:01:00.1: bound 0000:01:00.0 (ops nv50_audio_component_bind_ops [nouveau])
Aug 23 06:58:14 janos-work-host sensors[1676]: nouveau-pci-0100
Aug 23 06:58:39 janos-work-host kernel: [   46.813257] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000020000 engine 06 [HOST0] client 07 [HUB/HOST_CPU] reason 02 [PTE] on channel 8 [00fef16000 Xorg[2683]]
Aug 23 06:58:39 janos-work-host kernel: [   46.813269] nouveau 0000:01:00.0: fifo: channel 8: killed
Aug 23 06:58:39 janos-work-host kernel: [   46.813272] nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
Aug 23 06:58:39 janos-work-host kernel: [   46.813305] WARNING: CPU: 3 PID: 3183 at drivers/gpu/drm/nouveau/nvkm/engine/fifo/gk104.c:284 gk104_fifo_engine_id+0x4f/0x80 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813408]  snd_seq_midi_event libarc4 snd_rawmidi kvm_intel snd_seq btusb kvm btrtl btbcm btintel btmtk snd_seq_device iwlwifi bluetooth nls_iso8859_1 snd_timer rapl mei_me intel_cstate input_leds joydev snd think_lmi ecdh_generic intel_wmi_thunderbolt firmware_attributes_class ecc wmi_bmof cfg80211 ee1004 mei soundcore mac_hid acpi_pad acpi_tad sch_fq_codel msr parport_pc ppdev lp parport ramoops reed_solomon pstore_blk pstore_zone efi_pstore ip_tables x_tables autofs4 dm_crypt hid_generic i915 nouveau r8152 mxm_wmi drm_ttm_helper i2c_algo_bit ttm cdc_ncm drm_kms_helper cdc_ether syscopyarea sysfillrect usbnet usbhid sysimgblt fb_sys_fops mii hid crct10dif_pclmul cec crc32_pclmul ghash_clmulni_intel rc_core aesni_intel crypto_simd drm nvme cryptd e1000e i2c_i801 xhci_pci nvme_core i2c_smbus xhci_pci_renesas wmi video
Aug 23 06:58:39 janos-work-host kernel: [   46.813448] RIP: 0010:gk104_fifo_engine_id+0x4f/0x80 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813548]  gk104_fifo_fault+0x10c/0x230 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813606]  nvkm_fifo_fault+0x15/0x20 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813662]  gp100_fifo_intr_fault+0xe0/0x110 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813716]  gk104_fifo_intr+0x2a6/0x3c0 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813791]  nvkm_fifo_intr+0x1d/0x20 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813866]  nvkm_engine_intr+0x1f/0x30 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813901]  nvkm_subdev_intr+0x1a/0x20 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813937]  nvkm_mc_intr+0x14e/0x190 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.813984]  ? gp100_mc_intr_unarm+0x3a/0x50 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.814031]  nvkm_pci_intr+0x5e/0xb0 [nouveau]
Aug 23 06:58:39 janos-work-host kernel: [   46.814142] nouveau 0000:01:00.0: Xorg[2683]: channel 8 killed!
Aug 23 06:59:47 janos-work-host kernel: [  115.087275] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 000000000127a000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
Aug 23 06:59:47 janos-work-host kernel: [  115.144046] nouveau 0000:01:00.0: fifo: fault 00 [READ] at 0000000011402000 engine 15 [ce0] client 01 [HUB/CE0] reason 00 [PDE] on channel 2 [00ff962000 Xorg[2683]]
Aug 23 06:59:47 janos-work-host kernel: [  115.144083] nouveau 0000:01:00.0: fifo: channel 2: killed
Aug 23 06:59:47 janos-work-host kernel: [  115.144090] nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
Aug 23 06:59:47 janos-work-host kernel: [  115.144100] nouveau 0000:01:00.0: fifo: engine 0: scheduled for recovery
Aug 23 06:59:47 janos-work-host kernel: [  115.144106] nouveau 0000:01:00.0: fifo: engine 7: scheduled for recovery
Aug 23 06:59:47 janos-work-host kernel: [  115.144117] nouveau 0000:01:00.0: Xorg[2683]: channel 2 killed!
Aug 23 07:00:05 janos-work-host kernel: [  132.316992] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000020000 engine 06 [HOST0] client 07 [HUB/HOST_CPU] reason 02 [PTE] on channel 9 [00fedbc000 gst-plugin-scan[7003]]
Aug 23 07:00:05 janos-work-host kernel: [  132.317005] nouveau 0000:01:00.0: fifo: channel 9: killed
Aug 23 07:00:05 janos-work-host kernel: [  132.317008] nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
Aug 23 07:00:05 janos-work-host kernel: [  132.317042] WARNING: CPU: 3 PID: 6824 at drivers/gpu/drm/nouveau/nvkm/engine/fifo/gk104.c:284 gk104_fifo_engine_id+0x4f/0x80 [nouveau]
Aug 23 07:00:05 janos-work-host kernel: [  132.317140]  snd_pcm mac80211 snd_seq_midi snd_seq_midi_event libarc4 snd_rawmidi kvm_intel snd_seq btusb kvm btrtl btbcm btintel btmtk snd_seq_device iwlwifi bluetooth nls_iso8859_1 snd_timer rapl mei_me intel_cstate input_leds joydev snd think_lmi ecdh_generic intel_wmi_thunderbolt firmware_attributes_class ecc wmi_bmof cfg80211 ee1004 mei soundcore mac_hid acpi_pad acpi_tad sch_fq_codel msr parport_pc ppdev lp parport ramoops reed_solomon pstore_blk pstore_zone efi_pstore ip_tables x_tables autofs4 dm_crypt hid_generic i915 nouveau r8152 mxm_wmi drm_ttm_helper i2c_algo_bit ttm cdc_ncm drm_kms_helper cdc_ether syscopyarea sysfillrect usbnet usbhid sysimgblt fb_sys_fops mii hid crct10dif_pclmul cec crc32_pclmul ghash_clmulni_intel rc_core aesni_intel crypto_simd drm nvme cryptd e1000e i2c_i801 xhci_pci nvme_core i2c_smbus xhci_pci_renesas wmi video
```

Does anyone have any idea how I could improve the situation? Maybe switch over to the official NVIDIA driver?

---

### Post by jszigetvari on 2023-09-02
I am using the following kernel version:
```
[FONT=monospace][COLOR=#000000]# uname -a[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]Linux janos-work-host 5.17.0-1035-oem #36-Ubuntu SMP PREEMPT Fri Jul 14 13:27:38 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux[/COLOR][/FONT]
```

---

### Post by jszigetvari on 2023-09-03
I currently have two Dell 4K displays connected to the VGA over DisplayPort.

---

### Post by jszigetvari on 2023-09-05
Does anyone have any idea how to solve this?

---

### Post by ajgreeny on 2023-09-05
I don't know nvidia cards at all but have you looked to see what drivers are available for that graphic card in **Additional Drivers**?

---

### Post by jszigetvari on 2023-09-05
For the time being I decided to go back to using the generic kernel, and monitor if that brings any change.
As for the '**Additional Drivers'**, I will check that as the next option, should the situation remain unchanged.

---

### Post by SeijiSensei on 2023-09-06
Use the proprietary NVIDIA driver available from the "Driver Manager" or "Additional Drivers" app. If you check the box for third-party software during installation, the correct drivers will be downloaded and installed at that time.

---

### Post by jszigetvari on 2023-09-13
In the meantime I have switched over to the generic kernel, and it seems to perform well enough (the crashes are a thing of the past). I have removed the oem kernel, and will be monitoring the situation for the upcoming few weeks.

---

### Post by jszigetvari on 2023-09-13
Well, this is funny. No crashes for over a week, but right after I post about experiencing no crashes, the GUI crashes... LOL.

```
syslog:Sep 13 09:41:00 janos-work-host kernel: [14932.487478] nouveau 0000:01:00.0: fifo: FB_FLUSH_TIMEOUT
syslog:Sep 13 09:41:00 janos-work-host kernel: [14932.489064] nouveau 0000:01:00.0: fifo: CHSW_ERROR 00000003
syslog:Sep 13 10:26:39 janos-work-host kernel: [17671.321000] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000001344000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143593] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143631] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143652] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143688] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143711] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143733] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143758] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143778] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143798] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143831] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143869] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143884] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:38:33 janos-work-host kernel: [18385.143906] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000fc9000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:59:06 janos-work-host kernel: [19617.807247] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000001010000 engine 05 [BAR2] client 08 [HUB/HOST_CPU_NB] reason 02 [PTE] on channel -1 [00ffebf000 unknown]
syslog:Sep 13 10:59:06 janos-work-host kernel: [19617.901348] nouveau 0000:01:00.0: fifo: fault 00 [READ] at 000000000f402000 engine 15 [ce0] client 01 [HUB/CE0] reason 00 [PDE] on channel 2 [00ff962000 Xorg[2740]]
syslog:Sep 13 10:59:06 janos-work-host kernel: [19617.901363] nouveau 0000:01:00.0: fifo: channel 2: killed
syslog:Sep 13 10:59:06 janos-work-host kernel: [19617.901366] nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
syslog:Sep 13 10:59:06 janos-work-host kernel: [19617.901370] nouveau 0000:01:00.0: fifo: engine 7: scheduled for recovery
syslog:Sep 13 10:59:06 janos-work-host kernel: [19617.901375] nouveau 0000:01:00.0: Xorg[2740]: channel 2 killed
```

---

### Post by jszigetvari on 2023-09-13
This is the latest one:
```
[sze szept 13 14:50:32 2023] nouveau 0000:01:00.0: fifo: fault 01 [WRITE] at 0000000000020000 engine 06 [HOST0] client 07 [HUB/HOST_CPU] reason 02 [PTE] on channel 14 [00ff611000 Xorg[2482]]
[sze szept 13 14:50:32 2023] nouveau 0000:01:00.0: fifo: channel 14: killed
[sze szept 13 14:50:32 2023] nouveau 0000:01:00.0: fifo: runlist 0: scheduled for recovery
[sze szept 13 14:50:32 2023] ------------[ cut here ]------------
[sze szept 13 14:50:32 2023] WARNING: CPU: 3 PID: 0 at drivers/gpu/drm/nouveau/nvkm/engine/fifo/gk104.c:284 gk104_fifo_engine_id+0x4f/0x90 [nouveau]
[sze szept 13 14:50:32 2023] Modules linked in: tls vhost_net vhost vhost_iotlb tap uhid rfcomm xt_CHECKSUM xt_MASQUERADE xt_conntrack ipt_REJECT nf_reject_ipv4 xt_tcpudp nft_compat nft_chain_nat nf_nat nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 nft_counter nf_tables libcrc32c nfnetlink bridge stp llc nvme_fabrics cmac algif_hash algif_skcipher af_alg vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep sunrpc binfmt_misc intel_rapl_msr mei_hdcp snd_sof_pci_intel_cnl snd_sof_intel_hda_common soundwire_intel soundwire_generic_allocation soundwire_cadence snd_sof_intel_hda snd_sof_pci snd_sof_xtensa_dsp snd_sof snd_soc_hdac_hda snd_hda_ext_core snd_soc_acpi_intel_match snd_soc_acpi snd_hda_codec_realtek soundwire_bus snd_hda_codec_generic ledtrig_audio snd_soc_core snd_hda_codec_hdmi snd_compress ac97_bus snd_pcm_dmaengine intel_rapl_common nls_iso8859_1 intel_tcc_cooling x86_pkg_temp_thermal snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi intel_powerclamp snd_hda_codec snd_hda_core snd_hwdep coretemp snd_pcm
[sze szept 13 14:50:32 2023]  iwlmvm snd_seq_midi kvm_intel snd_seq_midi_event kvm snd_rawmidi mac80211 btusb joydev btrtl rapl snd_seq libarc4 btbcm snd_seq_device btintel intel_cstate think_lmi input_leds iwlwifi snd_timer bluetooth pl2303 usbserial wmi_bmof intel_wmi_thunderbolt firmware_attributes_class snd mei_me ecdh_generic ecc ee1004 cfg80211 mei soundcore mac_hid acpi_pad acpi_tad sch_fq_codel msr parport_pc ppdev lp parport ramoops pstore_blk reed_solomon pstore_zone efi_pstore ip_tables x_tables autofs4 dm_crypt cdc_ncm cdc_ether usbnet r8152 mii hid_generic usbhid hid i915 nouveau mxm_wmi i2c_algo_bit drm_ttm_helper ttm drm_kms_helper syscopyarea crct10dif_pclmul sysfillrect crc32_pclmul sysimgblt ghash_clmulni_intel fb_sys_fops aesni_intel cec rc_core nvme crypto_simd i2c_i801 drm cryptd e1000e nvme_core i2c_smbus xhci_pci xhci_pci_renesas wmi video
[sze szept 13 14:50:32 2023] CPU: 3 PID: 0 Comm: swapper/3 Tainted: G        W  OE     5.15.0-83-generic #92-Ubuntu
[sze szept 13 14:50:32 2023] Hardware name: LENOVO 30CECT01WW/3135, BIOS M1UKT65A 03/03/2021
[sze szept 13 14:50:32 2023] RIP: 0010:gk104_fifo_engine_id+0x4f/0x90 [nouveau]
[sze szept 13 14:50:32 2023] Code: 89 f4 48 85 f6 74 23 48 8d 9f 98 03 00 00 31 c0 48 63 f0 48 83 fe 0f 77 31 4c 3b 23 74 13 83 c0 01 48 83 c3 10 44 39 e8 7c e6 <0f> 0b b8 ff ff ff ff 48 83 c4 08 5b 41 5c 41 5d 5d c3 cc cc cc cc
[sze szept 13 14:50:32 2023] RSP: 0018:ffffade580240cd8 EFLAGS: 00010046
[sze szept 13 14:50:32 2023] RAX: 0000000000000009 RBX: ffff91f5c14d9430 RCX: 0000000000000009
[sze szept 13 14:50:32 2023] RDX: 0000000000000009 RSI: 0000000000000008 RDI: ffff91f5c14d9008
[sze szept 13 14:50:32 2023] RBP: ffffade580240cf8 R08: 0000000000000000 R09: 0000000000000000
[sze szept 13 14:50:32 2023] R10: 0000000000000009 R11: ffffffffffffff00 R12: ffff91f5c14d9010
[sze szept 13 14:50:32 2023] R13: 0000000000000009 R14: ffff91f5c14d9008 R15: ffff91f5c14d92b8
[sze szept 13 14:50:32 2023] FS:  0000000000000000(0000) GS:ffff92053c2c0000(0000) knlGS:0000000000000000
[sze szept 13 14:50:32 2023] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[sze szept 13 14:50:32 2023] CR2: 00007f87e0c96750 CR3: 00000002a9044001 CR4: 00000000003726e0
[sze szept 13 14:50:32 2023] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[sze szept 13 14:50:32 2023] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[sze szept 13 14:50:32 2023] Call Trace:
[sze szept 13 14:50:32 2023]  <IRQ>
[sze szept 13 14:50:32 2023]  ? show_trace_log_lvl+0x1d6/0x2ea
[sze szept 13 14:50:32 2023]  ? show_trace_log_lvl+0x1d6/0x2ea
[sze szept 13 14:50:32 2023]  ? gk104_fifo_fault+0x109/0x230 [nouveau]
[sze szept 13 14:50:32 2023]  ? show_regs.part.0+0x23/0x29
[sze szept 13 14:50:32 2023]  ? show_regs.cold+0x8/0xd
[sze szept 13 14:50:32 2023]  ? gk104_fifo_engine_id+0x4f/0x90 [nouveau]
[sze szept 13 14:50:32 2023]  ? __warn+0x8c/0x100
[sze szept 13 14:50:32 2023]  ? gk104_fifo_engine_id+0x4f/0x90 [nouveau]
[sze szept 13 14:50:32 2023]  ? report_bug+0xa4/0xd0
[sze szept 13 14:50:32 2023]  ? handle_bug+0x39/0x90
[sze szept 13 14:50:32 2023]  ? exc_invalid_op+0x19/0x70
[sze szept 13 14:50:32 2023]  ? asm_exc_invalid_op+0x1b/0x20
[sze szept 13 14:50:32 2023]  ? gk104_fifo_engine_id+0x4f/0x90 [nouveau]
[sze szept 13 14:50:32 2023]  gk104_fifo_fault+0x109/0x230 [nouveau]
[sze szept 13 14:50:32 2023]  nvkm_fifo_fault+0x12/0x20 [nouveau]
[sze szept 13 14:50:32 2023]  gp100_fifo_intr_fault+0xe0/0x110 [nouveau]
[sze szept 13 14:50:32 2023]  gk104_fifo_intr+0x2a6/0x3c0 [nouveau]
[sze szept 13 14:50:32 2023]  nvkm_fifo_intr+0x1a/0x30 [nouveau]
[sze szept 13 14:50:32 2023]  nvkm_engine_intr+0x1c/0x30 [nouveau]
[sze szept 13 14:50:32 2023]  nvkm_subdev_intr+0x17/0x30 [nouveau]
[sze szept 13 14:50:32 2023]  nvkm_mc_intr+0x151/0x1a0 [nouveau]
[sze szept 13 14:50:32 2023]  ? gp100_mc_intr_unarm+0x3a/0x50 [nouveau]
[sze szept 13 14:50:32 2023]  nvkm_pci_intr+0x5e/0xc0 [nouveau]
[sze szept 13 14:50:32 2023]  __handle_irq_event_percpu+0x3f/0x170
[sze szept 13 14:50:32 2023]  handle_irq_event+0x59/0xb0
[sze szept 13 14:50:32 2023]  handle_edge_irq+0x8c/0x230
[sze szept 13 14:50:32 2023]  __common_interrupt+0x4f/0xe0
[sze szept 13 14:50:32 2023]  common_interrupt+0x89/0xa0
[sze szept 13 14:50:32 2023]  </IRQ>
[sze szept 13 14:50:32 2023]  <TASK>
[sze szept 13 14:50:32 2023]  asm_common_interrupt+0x27/0x40
[sze szept 13 14:50:32 2023] RIP: 0010:cpuidle_enter_state+0xd9/0x620
[sze szept 13 14:50:32 2023] Code: 3d 54 7a b8 6a e8 67 77 67 ff 49 89 c7 0f 1f 44 00 00 31 ff e8 a8 84 67 ff 80 7d d0 00 0f 85 61 01 00 00 fb 66 0f 1f 44 00 00 <45> 85 f6 0f 88 6d 01 00 00 4d 63 ee 49 83 fd 09 0f 87 e7 03 00 00
[sze szept 13 14:50:32 2023] RSP: 0018:ffffade58015fe28 EFLAGS: 00000246
[sze szept 13 14:50:32 2023] RAX: ffff92053c2f1480 RBX: ffffcde57fac0618 RCX: 0000000000000000
[sze szept 13 14:50:32 2023] RDX: 0000000000000000 RSI: 0000000000000002 RDI: 0000000000000000
[sze szept 13 14:50:32 2023] RBP: ffffade58015fe78 R08: 00000c6fb8fea2ef R09: 00000000000186a0
[sze szept 13 14:50:32 2023] R10: 0000000000000009 R11: 071c71c71c71c71c R12: ffffffff96ad6460
[sze szept 13 14:50:32 2023] R13: 0000000000000002 R14: 0000000000000002 R15: 00000c6fb8fea2ef
[sze szept 13 14:50:32 2023]  ? cpuidle_enter_state+0xc8/0x620
[sze szept 13 14:50:32 2023]  cpuidle_enter+0x2e/0x50
[sze szept 13 14:50:32 2023]  cpuidle_idle_call+0x142/0x1e0
[sze szept 13 14:50:32 2023]  do_idle+0x83/0xf0
[sze szept 13 14:50:32 2023]  cpu_startup_entry+0x20/0x30
[sze szept 13 14:50:32 2023]  start_secondary+0x12a/0x180
[sze szept 13 14:50:32 2023]  secondary_startup_64_no_verify+0xc2/0xcb
[sze szept 13 14:50:32 2023]  </TASK>
[sze szept 13 14:50:32 2023] ---[ end trace dab9ec56d23639a2 ]---
[sze szept 13 14:50:32 2023] nouveau 0000:01:00.0: Xorg[2482]: channel 14 killed!
```

Happened on:
```
# uname -a
Linux janos-work-host 5.15.0-83-generic #92-Ubuntu SMP Mon Aug 14 09:30:42 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```

---

