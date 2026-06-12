---
title: "Dell E6540 Bios A13 Intel GPU Issue"
date: 2015-03-05
forum: Hardware
---

### Post by leeyuentuen on 2015-03-05
Hi,

After suspend i've got the following error in dmesg:

[92650.015178] ------------[ cut here ]------------
[92650.015206] WARNING: CPU: 0 PID: 1330 at /build/buildd/linux-3.16.0/drivers/gpu/drm/i915/intel_pm.c:5992 intel_display_power_put+0x14c/0x160 [i915]()
[92650.015207] Modules linked in: hid_generic snd_usb_audio snd_usbmidi_lib usbhid xt_CHECKSUM iptable_mangle ipt_MASQUERADE iptable_nat nf_nat_ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables bridge stp llc ctr ccm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep rfcomm snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media arc4 fglrx(POE) iwldvm mac80211 dell_wmi sparse_keymap dell_laptop dcdbas intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd btusb bluetooth 6lowpan_iphc joydev
[92650.015223]  serio_raw iwlwifi cfg80211 lpc_ich snd_soc_rt5640 snd_soc_rl6231 amd_iommu_v2 snd_soc_core i2c_hid hid snd_compress snd_pcm_dmaengine wmi dell_smo8800 dw_dmac snd_soc_sst_acpi dw_dmac_core i2c_designware_platform spi_pxa2xx_platform i2c_designware_core 8250_dw snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi i915 snd_seq snd_seq_device snd_timer snd video drm_kms_helper soundcore drm mei_me mei shpchp i2c_algo_bit mac_hid parport_pc ppdev lp parport psmouse ahci sdhci_pci libahci e1000e ptp pps_core sdhci_acpi sdhci
[92650.015239] CPU: 0 PID: 1330 Comm: Xorg Tainted: P        W  OE 3.16.0-31-generic #41-Ubuntu
[92650.015240] Hardware name: Dell Inc. Latitude E6540/0725FP, BIOS A13 02/02/2015
[92650.015241]  0000000000000009 ffff880216bd7af8 ffffffff81782d0b 0000000000000000
[92650.015243]  ffff880216bd7b30 ffffffff8106ff2d ffff88021899002c 000000000000000b
[92650.015244]  ffff880218998520 ffff88021f4a2000 ffff880218990000 ffff880216bd7b40
[92650.015245] Call Trace:
[92650.015250]  [<ffffffff81782d0b>] dump_stack+0x45/0x56
[92650.015253]  [<ffffffff8106ff2d>] warn_slowpath_common+0x7d/0xa0
[92650.015254]  [<ffffffff8107000a>] warn_slowpath_null+0x1a/0x20
[92650.015261]  [<ffffffffc044527c>] intel_display_power_put+0x14c/0x160 [i915]
[92650.015272]  [<ffffffffc048e114>] modeset_update_crtc_power_domains+0x204/0x210 [i915]
[92650.015281]  [<ffffffffc048e12e>] haswell_modeset_global_resources+0xe/0x10 [i915]
[92650.015290]  [<ffffffffc048f82a>] __intel_set_mode+0x5fa/0xab0 [i915]
[92650.015299]  [<ffffffffc0492c36>] intel_set_mode+0x16/0x30 [i915]
[92650.015307]  [<ffffffffc0493cfa>] intel_crtc_set_config+0xa4a/0xda0 [i915]
[92650.015317]  [<ffffffffc03876d1>] drm_mode_set_config_internal+0x61/0xe0 [drm]
[92650.015324]  [<ffffffffc038b413>] drm_mode_setcrtc+0x283/0x580 [drm]
[92650.015329]  [<ffffffffc037ba4f>] drm_ioctl+0x1df/0x680 [drm]
[92650.015334]  [<ffffffff811f5658>] do_vfs_ioctl+0x2c8/0x4a0
[92650.015335]  [<ffffffff811e3b51>] ? __sb_end_write+0x31/0x60
[92650.015337]  [<ffffffff811e16c2>] ? vfs_write+0x1b2/0x1f0
[92650.015339]  [<ffffffff811f58b1>] SyS_ioctl+0x81/0xa0
[92650.015340]  [<ffffffff8178ad2d>] system_call_fastpath+0x1a/0x1f
[92650.015341] ---[ end trace 6c5e436d04bfd357 ]---
[92650.031167] ------------[ cut here ]------------

[92650.031178] WARNING: CPU: 0 PID: 1330 at /build/buildd/linux-3.16.0/drivers/gpu/drm/i915/intel_pm.c:5996 intel_display_power_put+0xf9/0x160 [i915]()
[92650.031179] Modules linked in: hid_generic snd_usb_audio snd_usbmidi_lib usbhid xt_CHECKSUM iptable_mangle ipt_MASQUERADE iptable_nat nf_nat_ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables bridge stp llc ctr ccm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep rfcomm snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media arc4 fglrx(POE) iwldvm mac80211 dell_wmi sparse_keymap dell_laptop dcdbas intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd btusb bluetooth 6lowpan_iphc joydev
[92650.031194]  serio_raw iwlwifi cfg80211 lpc_ich snd_soc_rt5640 snd_soc_rl6231 amd_iommu_v2 snd_soc_core i2c_hid hid snd_compress snd_pcm_dmaengine wmi dell_smo8800 dw_dmac snd_soc_sst_acpi dw_dmac_core i2c_designware_platform spi_pxa2xx_platform i2c_designware_core 8250_dw snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi i915 snd_seq snd_seq_device snd_timer snd video drm_kms_helper soundcore drm mei_me mei shpchp i2c_algo_bit mac_hid parport_pc ppdev lp parport psmouse ahci sdhci_pci libahci e1000e ptp pps_core sdhci_acpi sdhci
[92650.031207] CPU: 0 PID: 1330 Comm: Xorg Tainted: P        W  OE 3.16.0-31-generic #41-Ubuntu
[92650.031208] Hardware name: Dell Inc. Latitude E6540/0725FP, BIOS A13 02/02/2015
[92650.031208]  0000000000000009 ffff880216bd7af8 ffffffff81782d0b 0000000000000000
[92650.031210]  ffff880216bd7b30 ffffffff8106ff2d ffffffffc04f3800 0000000000020000
[92650.031211]  ffff880218998520 0000000000000000 ffff880218990000 ffff880216bd7b40
[92650.031213] Call Trace:
[92650.031215]  [<ffffffff81782d0b>] dump_stack+0x45/0x56
[92650.031217]  [<ffffffff8106ff2d>] warn_slowpath_common+0x7d/0xa0
[92650.031219]  [<ffffffff8107000a>] warn_slowpath_null+0x1a/0x20
[92650.031226]  [<ffffffffc0445229>] intel_display_power_put+0xf9/0x160 [i915]
[92650.031235]  [<ffffffffc048e114>] modeset_update_crtc_power_domains+0x204/0x210 [i915]
[92650.031244]  [<ffffffffc048e12e>] haswell_modeset_global_resources+0xe/0x10 [i915]
[92650.031253]  [<ffffffffc048f82a>] __intel_set_mode+0x5fa/0xab0 [i915]
[92650.031262]  [<ffffffffc0492c36>] intel_set_mode+0x16/0x30 [i915]
[92650.031270]  [<ffffffffc0493cfa>] intel_crtc_set_config+0xa4a/0xda0 [i915]
[92650.031278]  [<ffffffffc03876d1>] drm_mode_set_config_internal+0x61/0xe0 [drm]
[92650.031285]  [<ffffffffc038b413>] drm_mode_setcrtc+0x283/0x580 [drm]
[92650.031290]  [<ffffffffc037ba4f>] drm_ioctl+0x1df/0x680 [drm]
[92650.031293]  [<ffffffff811f5658>] do_vfs_ioctl+0x2c8/0x4a0
[92650.031295]  [<ffffffff811e3b51>] ? __sb_end_write+0x31/0x60
[92650.031296]  [<ffffffff811e16c2>] ? vfs_write+0x1b2/0x1f0
[92650.031298]  [<ffffffff811f58b1>] SyS_ioctl+0x81/0xa0
[92650.031299]  [<ffffffff8178ad2d>] system_call_fastpath+0x1a/0x1f
[92650.031300] ---[ end trace 6c5e436d04bfd358 ]---



I'm thinking these should be some issue with the drivers for the Integrated Graphic Card (i915). Maybe someone can help?
It is a Dell E6540 with Bios version A13.
It has a Dual GPU
Running Ubuntu 14.10

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars XTX [Radeon HD 8790M]

---

### Post by Sane_Malkavian on 2015-05-30
Hi all!

I have a similar message in syslog after a sudden OS lockup on another laptop:

May 30 23:28:23 Aspire-laptop kernel: [41077.413639] mce: [Hardware Error]: Machine check events logged
May 30 23:52:46 Aspire-laptop kernel: [42540.100132] ------------[ cut here ]------------
May 30 23:52:46 Aspire-laptop kernel: [42540.100182] WARNING: CPU: 2 PID: 1534 at /build/buildd/linux-3.16.0/drivers/gpu/drm/i915/intel_pm.c:5936 intel_display_power_put+
0x14c/0x160 [i915]()
May 30 23:52:46 Aspire-laptop kernel: [42540.100185] Modules linked in: uas usb_storage nf_conntrack_ipv6 nf_defrag_ipv6 xt_tcpudp nf_conntrack_ipv4 nf_defrag_ipv4 xt_con
ntrack nf_conntrack ip6table_filter ip6_tables iptable_filter ip_tables x_tables rfcomm bnep binfmt_misc nls_iso8859_1 hid_multitouch uvcvideo videobuf2_vmalloc videobuf2
_memops videobuf2_core v4l2_common joydev videodev media i2c_hid acer_wmi sparse_keymap snd_hda_codec_hdmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_i
ntel kvm arc4 crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw btusb bluetooth 6lowpan_iphc 
snd_seq_midi nouveau snd_seq_midi_event spi_pxa2xx_platform dw_dmac rtl8723be dw_dmac_core mxm_wmi i2c_designware_platform btcoexist 8250_dw i2c_designware_core rtl8723_c
ommon snd_rawmidi snd_hda_codec_realtek rtl_pci snd_hda_codec_generic rtlwifi mac80211 i915 snd_seq snd_hda_intel snd_hda_controller snd_hda_codec wmi cfg80211 ttm snd_hw
dep video snd_seq_device snd_pcm drm_kms_helper mac_hid drm snd_timer lpc_ich shpchp i2c_algo_bit mei_me snd mei soundcore cuse parport_pc ppdev lp parport hid_generic us
bhid hid ahci r8169 libahci mii sdhci_acpi sdhci
May 30 23:52:46 Aspire-laptop kernel: [42540.100283] CPU: 2 PID: 1534 Comm: Xorg Tainted: G        W     3.16.0-38-generic #52-Ubuntu
May 30 23:52:46 Aspire-laptop kernel: [42540.100286] Hardware name: Acer Aspire E5-771G/EA70_HB, BIOS V1.09 07/17/2014
May 30 23:52:46 Aspire-laptop kernel: [42540.100288]  0000000000000009 ffff880093e1faf8 ffffffff817850ee 0000000000000000
May 30 23:52:46 Aspire-laptop kernel: [42540.100293]  ffff880093e1fb30 ffffffff8106fefd ffff88009b21002c 000000000000000b
May 30 23:52:46 Aspire-laptop kernel: [42540.100297]  ffff88009b218548 ffff8801ce505000 ffff88009b210000 ffff880093e1fb40
May 30 23:52:46 Aspire-laptop kernel: [42540.100301] Call Trace:
May 30 23:52:46 Aspire-laptop kernel: [42540.100310]  [<ffffffff817850ee>] dump_stack+0x45/0x56
May 30 23:52:46 Aspire-laptop kernel: [42540.100318]  [<ffffffff8106fefd>] warn_slowpath_common+0x7d/0xa0
May 30 23:52:46 Aspire-laptop kernel: [42540.100323]  [<ffffffff8106ffda>] warn_slowpath_null+0x1a/0x20
May 30 23:52:46 Aspire-laptop kernel: [42540.100343]  [<ffffffffc064016c>] intel_display_power_put+0x14c/0x160 [i915]
May 30 23:52:46 Aspire-laptop kernel: [42540.100376]  [<ffffffffc0689004>] modeset_update_crtc_power_domains+0x204/0x210 [i915]
May 30 23:52:46 Aspire-laptop kernel: [42540.100405]  [<ffffffffc068901e>] haswell_modeset_global_resources+0xe/0x10 [i915]
May 30 23:52:46 Aspire-laptop kernel: [42540.100432]  [<ffffffffc068a71a>] __intel_set_mode+0x5fa/0xab0 [i915]
May 30 23:52:46 Aspire-laptop kernel: [42540.100460]  [<ffffffffc068db26>] intel_set_mode+0x16/0x30 [i915]
May 30 23:52:46 Aspire-laptop kernel: [42540.100486]  [<ffffffffc068ebea>] intel_crtc_set_config+0xa4a/0xda0 [i915]
May 30 23:52:46 Aspire-laptop kernel: [42540.100512]  [<ffffffffc04d26d1>] drm_mode_set_config_internal+0x61/0xe0 [drm]
May 30 23:52:46 Aspire-laptop kernel: [42540.100534]  [<ffffffffc04d6413>] drm_mode_setcrtc+0x283/0x580 [drm]
May 30 23:52:46 Aspire-laptop kernel: [42540.100550]  [<ffffffffc04c6a4f>] drm_ioctl+0x1df/0x680 [drm]
May 30 23:52:46 Aspire-laptop kernel: [42540.100581]  [<ffffffffc06864a2>] ? valleyview_crtc_enable+0x7c2/0xbc0 [i915]
May 30 23:52:46 Aspire-laptop kernel: [42540.100587]  [<ffffffff811f5f78>] do_vfs_ioctl+0x2c8/0x4a0
May 30 23:52:46 Aspire-laptop kernel: [42540.100592]  [<ffffffff811e4451>] ? __sb_end_write+0x31/0x60
May 30 23:52:46 Aspire-laptop kernel: [42540.100598]  [<ffffffff811e1fc2>] ? vfs_write+0x1b2/0x1f0
May 30 23:52:46 Aspire-laptop kernel: [42540.100603]  [<ffffffff811f61d1>] SyS_ioctl+0x81/0xa0
May 30 23:52:46 Aspire-laptop kernel: [42540.100609]  [<ffffffff8178d10d>] system_call_fastpath+0x1a/0x1f
May 30 23:52:46 Aspire-laptop kernel: [42540.100612] ---[ end trace 34c9e84194506b28 ]---
May 30 23:53:17 Aspire-laptop kernel: [42570.341644] SysRq : This sysrq operation is disabled.
May 30 23:53:18 Aspire-laptop kernel: [42571.388865] SysRq : This sysrq operation is disabled.
May 30 23:53:19 Aspire-laptop kernel: [42572.613456] SysRq : This sysrq operation is disabled.
May 30 23:53:20 Aspire-laptop kernel: [42573.830843] SysRq : Emergency Sync
May 30 23:53:20 Aspire-laptop kernel: [42573.868638] Emergency Sync complete
May 30 23:53:21 Aspire-laptop kernel: [42575.104253] SysRq : Emergency Remount R/O
May 30 23:54:04 Aspire-laptop rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="890" x-info="http://www.rsyslog.com"] start
May 30 23:54:04 Aspire-laptop rsyslogd: rsyslogd's groupid changed to 103
May 30 23:54:04 Aspire-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
May 30 23:54:04 Aspire-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
May 30 23:54:04 Aspire-laptop kernel: [    0.000000] Initializing cgroup subsys cpuacct
May 30 23:54:04 Aspire-laptop kernel: [    0.000000] Linux version 3.16.0-38-generic (buildd@allspice) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #52-Ubuntu SMP Thu May 7 10:51:21 UTC 2015 (Ubuntu 3.16.0-38.52-generic 3.16.7-ckt10)

I surfed net with Firefox 38 and the issue appeared suddently as I browsed a page. I couldn't enter terminal via CTRL+ALT+F1 so I pressed REISUB and successfully rebooted the machine.

I run Ubuntu 14.10 on Acer Aspire E5-771G-348S. It has following video cards:

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 0882
    Flags: bus master, fast devsel, latency 0, IRQ 63
    Memory at b3000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device 0882
    Flags: fast devsel, IRQ 16
    Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>

---

