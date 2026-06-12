---
title: "Dell XPS-15 9550 / Nvidia: HDMI causes system hang with Gnome but not Unity."
date: 2016-03-18
forum: Hardware
---

### Post by shinyblue on 2016-03-18
I have the 4K UHD screen version and am running Ubuntu Gnome 16.04 Beta1 using 4.4.0-13-generic and the Nouveau/Intel drivers.

If I plug in an external monitor - HDMI or VGA - then the whole system hangs, completely unresponsive and needing a hard reboot. Before hanging the 2nd display gets an image as expected, but the laptop's screen flashes randomly, sometimes you see weird artifacts. Then the hang comes.

I've also tried to get the nvidia drivers (340 and 361, 'tested' and 'updates') working, but failed. When the Nvidia drivers are installed the display manager doesn't come up and the console screen flashes randomly and won't reliably accept keyboard input. You can SSH in to cleanly shutdown if you're lucky.

I'd really like to get the HDMI working, and ideally I'd like to get the nvidia drivers working too so I can use OpenCL.

**Vanilla Ubuntu, with lightdm and Unity, works fine.** This seems to be related to the Gnome shell DE. Installing Gnome Shell on top of the stock Ubuntu image means I can run Gnome Shell on nvidia (or intel) OK, but the system still hangs when I plug in an external monitor.

---

### Post by shinyblue on 2016-03-24
OK, when I said it works "fine" with untity,  not quite... 

Here's the syslog when plugging in an external HDMI monitor while using intel graphics:


> Mar 24 08:48:30 miaco kernel: [  795.486188] ------------[ cut here ]------------
Mar 24 08:48:30 miaco kernel: [  795.486238] WARNING: CPU: 0 PID: 1410 at /build/linux-lAMkDx/linux-4.4.0/ubuntu/i915/intel_pm.c:3567 skl_update_other_pipe_wm+0x16c/0x180 [i915_bpo]()
Mar 24 08:48:30 miaco kernel: [  795.486242] WARN_ON(!wm_changed)
Mar 24 08:48:30 miaco kernel: [  795.486245] Modules linked in: rfcomm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep bbswitch(OE) drbg ansi_cprng dm_crypt algif_skcipher af_alg nls_iso8859_1 snd_hda_codec_hdmi i2c_designware_platform i2c_designware_core dell_led dell_wmi sparse_keymap mxm_wmi snd_hda_codec_realtek brcmfmac snd_hda_codec_generic brcmutil dell_laptop dcdbas rtsx_pci_ms cfg80211 memstick intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul snd_hda_intel uvcvideo aesni_intel videobuf2_vmalloc snd_hda_codec aes_x86_64 videobuf2_memops lrw gf128mul videobuf2_v4l2 glue_helper ablk_helper snd_hda_core videobuf2_core cryptd v4l2_common snd_hwdep videodev snd_pcm hid_multitouch btusb media btrtl snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device idma64 joydev input_leds snd_timer virt_dma serio_raw snd hci_uart soundcore btbcm mei_me processor_thermal_device mei btqca shpchp intel_soc_dts_iosf btintel intel_lpss_pci bluetooth intel_lpss_acpi intel_lpss int3403_thermal dell_smo8800 int3400_thermal wmi acpi_thermal_rel int3402_thermal acpi_pad acpi_als int340x_thermal_zone kfifo_buf industrialio mac_hid parport_pc ppdev lp parport autofs4 mmc_block usbhid rtsx_pci_sdmmc i915_bpo intel_ips i2c_algo_bit drm_kms_helper syscopyarea psmouse sysfillrect sysimgblt fb_sys_fops ahci nvme drm rtsx_pci libahci i2c_hid hid pinctrl_sunrisepoint video pinctrl_intel fjes [last unloaded: nvidia]
Mar 24 08:48:30 miaco kernel: [  795.486400] CPU: 0 PID: 1410 Comm: Xorg Tainted: P           OE   4.4.0-15-generic #31-Ubuntu
Mar 24 08:48:30 miaco kernel: [  795.486404] Hardware name: Dell Inc. XPS 15 9550/0N7TVV, BIOS 01.01.19 01/25/2016
Mar 24 08:48:30 miaco kernel: [  795.486407]  0000000000000286 000000002d1085fe ffff8804a82a7950 ffffffff813e76a3
Mar 24 08:48:30 miaco kernel: [  795.486413]  ffff8804a82a7998 ffffffffc0281c50 ffff8804a82a7988 ffffffff8107fe12
Mar 24 08:48:30 miaco kernel: [  795.486419]  ffff8804a6e68000 ffff8804a5d39d8c ffff8804a6e69000 ffff8804ad113b78
Mar 24 08:48:30 miaco kernel: [  795.486424] Call Trace:
Mar 24 08:48:30 miaco kernel: [  795.486434]  [<ffffffff813e76a3>] dump_stack+0x63/0x90
Mar 24 08:48:30 miaco kernel: [  795.486443]  [<ffffffff8107fe12>] warn_slowpath_common+0x82/0xc0
Mar 24 08:48:30 miaco kernel: [  795.486448]  [<ffffffff8107feac>] warn_slowpath_fmt+0x5c/0x80
Mar 24 08:48:30 miaco kernel: [  795.486486]  [<ffffffffc01b34cc>] skl_update_other_pipe_wm+0x16c/0x180 [i915_bpo]
Mar 24 08:48:30 miaco kernel: [  795.486522]  [<ffffffffc01b3666>] skl_update_wm+0x186/0x5f0 [i915_bpo]
Mar 24 08:48:30 miaco kernel: [  795.486576]  [<ffffffffc023ef9f>] ? intel_ddi_enable_transcoder_func+0x17f/0x260 [i915_bpo]
Mar 24 08:48:30 miaco kernel: [  795.486613]  [<ffffffffc01b738e>] intel_update_watermarks+0x1e/0x30 [i915_bpo]
Mar 24 08:48:30 miaco kernel: [  795.486666]  [<ffffffffc0223011>] haswell_crtc_enable+0x321/0x8c0 [i915_bpo]
Mar 24 08:48:30 miaco kernel: [  795.486673]  [<ffffffff8181fe62>] ? mutex_lock+0x12/0x30
Mar 24 08:48:30 miaco kernel: [  795.486726]  [<ffffffffc021fcd4>] intel_atomic_commit+0x714/0xab0 [i915_bpo]
Mar 24 08:48:30 miaco kernel: [  795.486767]  [<ffffffffc00c980e>] ? drm_atomic_check_only+0x18e/0x590 [drm]
Mar 24 08:48:30 miaco kernel: [  795.486801]  [<ffffffffc00c9c47>] drm_atomic_commit+0x37/0x60 [drm]
Mar 24 08:48:30 miaco kernel: [  795.486819]  [<ffffffffc016c7f6>] drm_atomic_helper_set_config+0x76/0xb0 [drm_kms_helper]
Mar 24 08:48:30 miaco kernel: [  795.486849]  [<ffffffffc00b8e02>] drm_mode_set_config_internal+0x62/0x100 [drm]
Mar 24 08:48:30 miaco kernel: [  795.486880]  [<ffffffffc00bd322>] drm_mode_setcrtc+0x3d2/0x4f0 [drm]
Mar 24 08:48:30 miaco kernel: [  795.486901]  [<ffffffffc00ae712>] drm_ioctl+0x152/0x540 [drm]
Mar 24 08:48:30 miaco kernel: [  795.486930]  [<ffffffffc00bcf50>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
Mar 24 08:48:30 miaco kernel: [  795.486937]  [<ffffffff8121e7df>] do_vfs_ioctl+0x29f/0x490
Mar 24 08:48:30 miaco kernel: [  795.486944]  [<ffffffff8108cf41>] ? __set_task_blocked+0x41/0xa0
Mar 24 08:48:30 miaco kernel: [  795.486950]  [<ffffffff8108f8d6>] ? __set_current_blocked+0x36/0x60
Mar 24 08:48:30 miaco kernel: [  795.486954]  [<ffffffff8121ea49>] SyS_ioctl+0x79/0x90
Mar 24 08:48:30 miaco kernel: [  795.486960]  [<ffffffff8108fb8e>] ? SyS_rt_sigprocmask+0x8e/0xc0
Mar 24 08:48:30 miaco kernel: [  795.486967]  [<ffffffff81821ff2>] entry_SYSCALL_64_fastpath+0x16/0x71
Mar 24 08:48:30 miaco kernel: [  795.486978] ---[ end trace f4328fda62f16de9 ]---
Mar 24 08:48:30 miaco kernel: [  795.813585] [drm:intel_cpu_fifo_underrun_irq_handler [i915_bpo]] *ERROR* CPU pipe A FIFO underrun

---

