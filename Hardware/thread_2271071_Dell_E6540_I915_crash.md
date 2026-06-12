---
title: "Dell E6540 I915 crash"
date: 2015-03-27
forum: Hardware
---

### Post by Tuen_Lee on 2015-03-27
Hi,
This is the error message:

[47418.962438] ------------[ cut here ]------------
[47418.962444] WARNING: CPU: 1 PID: 1376 at /build/buildd/linux-3.16.0/drivers/gpu/drm/i915/intel_pm.c:5996 intel_display_power_put+0xf9/0x160 [i915]()
[47418.962444] Modules linked in: nfsd auth_rpcgss nfs_acl nfs lockd sunrpc fscache ctr ccm xt_CHECKSUM iptable_mangle ipt_MASQUERADE iptable_nat nf_nat_ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables bridge stp llc pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep rfcomm hid_generic uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media snd_usb_audio snd_usbmidi_lib usbhid snd_hda_codec_hdmi fglrx(POE) arc4 iwldvm mac80211 btusb bluetooth 6lowpan_iphc dell_wmi sparse_keymap dell_laptop dcdbas intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd
[47418.962460]  joydev serio_raw snd_hda_codec_realtek snd_hda_codec_generic iwlwifi snd_soc_rt5640 snd_soc_rl6231 cfg80211 lpc_ich snd_hda_intel i915 snd_soc_core snd_hda_controller snd_hda_codec mei_me snd_hwdep mei snd_compress snd_pcm_dmaengine amd_iommu_v2 snd_pcm drm_kms_helper drm shpchp i2c_algo_bit snd_seq_midi wmi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer dell_smo8800 snd video soundcore i2c_hid hid dw_dmac dw_dmac_core snd_soc_sst_acpi i2c_designware_platform spi_pxa2xx_platform i2c_designware_core 8250_dw mac_hid parport_pc ppdev lp parport psmouse e1000e ahci sdhci_pci libahci ptp pps_core sdhci_acpi sdhci
[47418.962473] CPU: 1 PID: 1376 Comm: Xorg Tainted: P        W  OE 3.16.0-33-generic #44-Ubuntu
[47418.962474] Hardware name: Dell Inc. Latitude E6540/0725FP, BIOS A13 02/02/2015
[47418.962474]  0000000000000009 ffff88021781faf8 ffffffff8178345b 0000000000000000
[47418.962476]  ffff88021781fb30 ffffffff8106fedd ffffffffc064d800 0000000000020000
[47418.962477]  ffff880217698520 0000000000000000 ffff880217690000 ffff88021781fb40
[47418.962478] Call Trace:
[47418.962480]  [<ffffffff8178345b>] dump_stack+0x45/0x56
[47418.962481]  [<ffffffff8106fedd>] warn_slowpath_common+0x7d/0xa0
[47418.962484]  [<ffffffff8106ffba>] warn_slowpath_null+0x1a/0x20
[47418.962489]  [<ffffffffc059f1c9>] intel_display_power_put+0xf9/0x160 [i915]
[47418.962498]  [<ffffffffc05e80d4>] modeset_update_crtc_power_domains+0x204/0x210 [i915]
[47418.962507]  [<ffffffffc05e80ee>] haswell_modeset_global_resources+0xe/0x10 [i915]
[47418.962515]  [<ffffffffc05e97ea>] __intel_set_mode+0x5fa/0xab0 [i915]
[47418.962524]  [<ffffffffc05ecbf6>] intel_set_mode+0x16/0x30 [i915]
[47418.962533]  [<ffffffffc05edcba>] intel_crtc_set_config+0xa4a/0xda0 [i915]
[47418.962539]  [<ffffffffc04626d1>] drm_mode_set_config_internal+0x61/0xe0 [drm]
[47418.962546]  [<ffffffffc0466413>] drm_mode_setcrtc+0x283/0x580 [drm]
[47418.962551]  [<ffffffffc0456a4f>] drm_ioctl+0x1df/0x680 [drm]
[47418.962554]  [<ffffffffc06864a2>] ? rfcomm_sock_getsockopt+0x1c2/0x290 [rfcomm]
[47418.962556]  [<ffffffff811f5568>] do_vfs_ioctl+0x2c8/0x4a0
[47418.962557]  [<ffffffff81084c19>] ? restore_altstack+0x19/0x30
[47418.962559]  [<ffffffff811f57c1>] SyS_ioctl+0x81/0xa0
[47418.962560]  [<ffffffff8178b46d>] system_call_fastpath+0x1a/0x1f
[47418.962561] ---[ end trace f49dd92232a37a22 ]---


Seems like the integrated graphic card has a issue
this are my VGA hardware:
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars XTX [Radeon HD 8790M]

I'm using the lastest bios version A13 and running ubuntu 14.10

---

