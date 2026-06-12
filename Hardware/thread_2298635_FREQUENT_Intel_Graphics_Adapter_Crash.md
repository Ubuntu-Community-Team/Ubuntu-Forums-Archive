---
title: "FREQUENT Intel Graphics Adapter Crash"
date: 2015-10-12
forum: Hardware
---

### Post by Ernie_Ewert on 2015-10-12
I am seeing this CRASH happen very frequently in syslog. (Between this crash and the [COLOR=#000000][FONT=monospace]avhihi-daemon flooding my logs I am generating GIGS of logs.)[/FONT][/COLOR][FONT=monospace]
Any ideas?  I have 2 Dell U3014 Monitors attached. Both have DP1.2 disabled (or I get nothing!) One is attached to the HDMI port and the other is attached to the Display Port. I see no VISIBLE issues on EITHER screen.

[/FONT][FONT=monospace][COLOR=#000000]Ubuntu 15.04
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]3.19.0-30-generic[/COLOR]
[/FONT]
[FONT=monospace]
[/FONT]

```

[FONT=monospace][COLOR=#000000]Oct 12 14:08:44 erniee-kubuntu-dev [/COLOR][COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617691] ------------[ cut here ]------------[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617704] WARNING: CPU: 5 PID: 845 at /build/linux-qOmAV7/linux-3.19.0/ubuntu/i915/intel_pm.c:3406 skl_update_other_pipe_wm+0x200/0x210 [i915_bpo]()[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617705] WARN_ON(!wm_changed)[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617705] Modules linked in: cfg80211 binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic eeepc_wmi asus_wmi sparse_keymap snd_hda_intel snd_hd[/COLOR]
a_controller joydev snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi x86_pkg_temp_thermal coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_seq snd_seq_device aesni_intel i91
5_bpo aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd hid_logitech_hidpp snd_timer serio_raw intel_ips snd drm_kms_helper soundcore drm shpchp i2c_algo_bit 8250_fintek i2c_hid acpi_pad mac_hid parport_pc ppdev lp parport 
autofs4 hid_logitech_dj usbhid hid mxm_wmi e1000e psmouse ptp pps_core ahci libahci wmi video
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617723] CPU: 5 PID: 845 Comm: Xorg Tainted: G        W      3.19.0-30-generic #34-Ubuntu[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617724] Hardware name: System manufacturer System Product Name/Z170-AR, BIOS 0502 07/14/2015[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617725]  ffffffffc0711060 ffff880848d3f568 ffffffff817c4d5f 0000000000000007[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617726]  ffff880848d3f5b8 ffff880848d3f5a8 ffffffff81076a8a ffff880848d3f660[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617727]  ffff88084a959000 ffff880848d3f704 ffff880848d3f650 ffff88084a95c000[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617728] Call Trace:[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617732]  [<ffffffff817c4d5f>] dump_stack+0x45/0x57[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617734]  [<ffffffff81076a8a>] warn_slowpath_common+0x8a/0xc0[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617735]  [<ffffffff81076b06>] warn_slowpath_fmt+0x46/0x50[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617740]  [<ffffffffc064e8c0>] skl_update_other_pipe_wm+0x200/0x210 [i915_bpo][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617745]  [<ffffffffc064ea9e>] skl_update_wm+0x1ce/0x740 [i915_bpo][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617753]  [<ffffffffc0698d9f>] ? gen9_read32+0xff/0x300 [i915_bpo][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617758]  [<ffffffffc064fa6e>] intel_update_watermarks+0x1e/0x30 [i915_bpo][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617770]  [<ffffffffc06b6fe0>] intel_finish_crtc_commit+0x180/0x1a0 [i915_bpo][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617774]  [<ffffffffc058abb1>] drm_atomic_helper_commit_planes_on_crtc+0x151/0x270 [drm_kms_helper][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617783]  [<ffffffffc06d0f80>] intel_atomic_commit+0x70/0x110 [i915_bpo][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617792]  [<ffffffffc052a377>] drm_atomic_commit+0x37/0x60 [drm][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617795]  [<ffffffffc05893e6>] drm_atomic_helper_disable_plane+0xf6/0x150 [drm_kms_helper][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617801]  [<ffffffffc0519f70>] __setplane_internal+0x1f0/0x2d0 [drm][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617806]  [<ffffffffc051a16e>] drm_mode_cursor_universal+0x11e/0x210 [drm][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617807]  [<ffffffff817c9783>] ? __ww_mutex_lock+0x63/0xb0[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617812]  [<ffffffffc051a2de>] drm_mode_cursor_common+0x7e/0x1a0 [drm][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617814]  [<ffffffff816a51fc>] ? copy_msghdr_from_user+0x15c/0x210[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617816]  [<ffffffff8120a2f0>] ? poll_select_copy_remaining+0x130/0x130[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617821]  [<ffffffffc051e561>] drm_mode_cursor_ioctl+0x41/0x50 [drm][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617825]  [<ffffffffc050ea6f>] drm_ioctl+0x1df/0x680 [drm][/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617827]  [<ffffffff810dfd39>] ? enqueue_hrtimer+0x29/0x90[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617828]  [<ffffffff810e030c>] ? __hrtimer_start_range_ns+0x2dc/0x410[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617830]  [<ffffffff812096a0>] do_vfs_ioctl+0x2e0/0x4e0[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617831]  [<ffffffff81083792>] ? __set_task_blocked+0x32/0x80[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617833]  [<ffffffff816a6885>] ? __sys_recvmsg+0x65/0x80[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617834]  [<ffffffff81086346>] ? __set_current_blocked+0x36/0x90[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617835]  [<ffffffff81209921>] SyS_ioctl+0x81/0xa0[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617836]  [<ffffffff81086586>] ? SyS_rt_sigprocmask+0x86/0xb0[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617837]  [<ffffffff817cbe8d>] system_call_fastpath+0x16/0x1b[/COLOR]
Oct 12 14:08:44 erniee-kubuntu-dev [COLOR=#FF5454]**kernel**[/COLOR][COLOR=#000000]: [  216.617838] ---[ end trace 5103c8ae79ec0a8d ]---[/COLOR]
[/FONT]
```

---

### Post by Ernie_Ewert on 2015-10-12
Additional information:

The crash happens **EVERY TIME** the mouse crosses the boundary from one Display to another.  

I don't suppose I would care so much if the logs didn't get completely filled.

---

### Post by Yellow Pasque on 2015-10-12
You should try a later kernel, especially since you have a Skylake chip.
[https://bugs.freedesktop.org/show_bug.cgi?id=89055](https://bugs.freedesktop.org/show_bug.cgi?id=89055)

---

