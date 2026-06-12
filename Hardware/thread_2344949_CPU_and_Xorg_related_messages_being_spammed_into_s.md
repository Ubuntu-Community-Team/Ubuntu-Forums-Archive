---
title: "CPU and Xorg related messages being spammed into syslog"
date: 2016-11-29
forum: Hardware
---

### Post by VitasLoWang on 2016-11-29
Hello, I don't know what the heck is this, but this happens several times per minute. Sometimes my computer suddenly pauses and I wonder if it's because of this.
Lenovo thinkpad T460 with Intel Skylake CPU
```
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706389] WARNING: CPU: 0 PID: 1439 at /build/linux-xHzv4a/linux-4.4.0/ubuntu/i915/intel_pm.c:3675 skl_update_other_pipe_wm+0x16c/0x180 [i915_bpo]()
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706390] WARN_ON(!wm_changed)
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706402] Modules linked in: btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c ctr ccm msr nf_log_ipv6 nf_log_ipv4 nf_log_common ip6t_REJECT nf_reject_ipv6 xt_LOG xt_limit ip6t_ah ipt_REJECT nf_conntrack_ipv6 nf_reject_ipv4 nf_defrag_ipv6 xt_tcpudp xt_conntrack iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat ip6table_filter ip6_tables iptable_filter ip_tables x_tables cmac rfcomm bnep symap_custom_dkms_x86_64(POE) uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common videodev btusb media btrtl btbcm btintel pci_stub symev_custom_dkms_x86_64(OE) vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) bluetooth vboxdrv(OE) arc4 snd_soc_skl snd_soc_skl_ipc intel_rapl snd_hda_ext_core snd_soc_sst_ipc x86_pkg_temp_thermal snd_soc_sst_dsp intel_powerclamp snd_soc_core coretemp snd_compress snd_hda_codec_hdmi kvm_intel ac97_bus snd_pcm_dmaengine iwlmvm snd_hda_codec_realtek kvm dw_dmac_core snd_hda_codec_generic mac80211 snd_seq_midi snd_seq_midi_event irqbypass snd_hda_intel snd_hda_codec snd_hda_core snd_rawmidi iwlwifi snd_hwdep input_leds joydev snd_seq snd_pcm serio_raw cfg80211 thinkpad_acpi rtsx_pci_ms memstick mei_me mei nvram shpchp snd_seq_device snd_timer snd soundcore mac_hid nf_conntrack_ftp nf_conntrack parport_pc ppdev lp parport autofs4 drbg ansi_cprng algif_skcipher af_alg dm_crypt hid_generic usbhid hid rtsx_pci_sdmmc crct10dif_pclmul crc32_pclmul i915_bpo aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd intel_ips i2c_algo_bit e1000e drm_kms_helper psmouse syscopyarea ptp sysfillrect pps_core sysimgblt rtsx_pci fb_sys_fops drm ahci libahci wmi video fjes
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706417] CPU: 0 PID: 1439 Comm: Xorg Tainted: P        W  OE   4.4.0-47-generic #68-Ubuntu
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706417] Hardware name: LENOVO 20FMS1R00U/20FMS1R00U, BIOS R06ET42W (1.16 ) 09/20/2016
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706418]  0000000000000286 0000000096fabfd7 ffff880213b87650 ffffffff813f5aa3
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706419]  ffff880213b87698 ffffffffc038e9a0 ffff880213b87688 ffffffff81081262
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706420]  ffff8802133cd000 ffff88021261a148 ffff8802133cc000 ffff880217f6bb78
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706420] Call Trace:
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706422]  [<ffffffff813f5aa3>] dump_stack+0x63/0x90
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706424]  [<ffffffff81081262>] warn_slowpath_common+0x82/0xc0
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706425]  [<ffffffff810812fc>] warn_slowpath_fmt+0x5c/0x80
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706436]  [<ffffffffc02affec>] skl_update_other_pipe_wm+0x16c/0x180 [i915_bpo]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706447]  [<ffffffffc02b0185>] skl_update_wm+0x185/0x610 [i915_bpo]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706463]  [<ffffffffc03413af>] ? intel_ddi_enable_transcoder_func+0x17f/0x260 [i915_bpo]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706474]  [<ffffffffc02b3f0e>] intel_update_watermarks+0x1e/0x30 [i915_bpo]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706489]  [<ffffffffc0323681>] haswell_crtc_enable+0x761/0x8e0 [i915_bpo]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706505]  [<ffffffffc030ecbe>] ? intel_finish_crtc_commit+0xe/0x10 [i915_bpo]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706510]  [<ffffffffc01436d4>] ? drm_atomic_helper_commit_planes_on_crtc+0x154/0x270 [drm_kms_helper]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706525]  [<ffffffffc031f586>] intel_atomic_commit+0x5d6/0x14a0 [i915_bpo]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706536]  [<ffffffffc0071bde>] ? drm_atomic_check_only+0x18e/0x590 [drm]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706546]  [<ffffffffc0072017>] drm_atomic_commit+0x37/0x60 [drm]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706551]  [<ffffffffc0144e4f>] restore_fbdev_mode+0x22f/0x260 [drm_kms_helper]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706561]  [<ffffffffc007079a>] ? drm_modeset_lock_all_ctx+0x9a/0xb0 [drm]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706566]  [<ffffffffc0147023>] drm_fb_helper_restore_fbdev_mode_unlocked+0x33/0x80 [drm_kms_helper]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706570]  [<ffffffffc014709d>] drm_fb_helper_set_par+0x2d/0x50 [drm_kms_helper]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706586]  [<ffffffffc03395ba>] intel_fbdev_set_par+0x1a/0x60 [i915_bpo]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706587]  [<ffffffff8147903f>] ? fb_set_var+0x2ef/0x460
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706588]  [<ffffffff81478f86>] fb_set_var+0x236/0x460
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706589]  [<ffffffff810b546a>] ? check_preempt_wakeup+0xfa/0x220
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706590]  [<ffffffff810b4f59>] ? update_curr+0x79/0x160
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706592]  [<ffffffff8146f27f>] fbcon_blank+0x30f/0x350
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706593]  [<ffffffff810ab329>] ? ttwu_do_wakeup+0x19/0xe0
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706595]  [<ffffffff81506633>] do_unblank_screen+0xd3/0x1a0
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706596]  [<ffffffff814fb709>] complete_change_console+0x59/0xe0
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706598]  [<ffffffff814fbea0>] vt_ioctl+0x710/0x12f0
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706604]  [<ffffffffc0056789>] ? drm_ioctl+0x189/0x540 [drm]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706606]  [<ffffffff814ef15f>] tty_ioctl+0x35f/0xc40
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706608]  [<ffffffff811c082d>] ? handle_mm_fault+0xcdd/0x1820
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706610]  [<ffffffffc08ad836>] ? symap_event_cb+0x219/0x48c [symap_custom_dkms_x86_64]
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706611]  [<ffffffff81224cb4>] ? dput+0x34/0x220
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706612]  [<ffffffff8122156f>] do_vfs_ioctl+0x29f/0x490
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706613]  [<ffffffff8106b504>] ? __do_page_fault+0x1b4/0x400
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706614]  [<ffffffff812217d9>] SyS_ioctl+0x79/0x90
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706615]  [<ffffffff81834ff2>] entry_SYSCALL_64_fastpath+0x16/0x71
Nov 29 13:33:51 vitas-ThinkPad-T460 kernel: [126659.706616] ---[ end trace 5df43f7289588f14 ]---
```

---

### Post by Yellow Pasque on 2016-11-29
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1567417](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1567417)

---

