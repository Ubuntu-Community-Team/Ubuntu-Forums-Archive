---
title: "Lenovo X1: Undock = X11 Crash/Logout"
date: 2016-01-29
forum: Hardware
---

### Post by Michael_Borkowski on 2016-01-29
Hi,


Sorry if this has been asked somewhere before, I looked on different sites for any formation; or if this is the wrong subforum, I tried my best to find the best match.
While I'm new to the Ubuntu Forums, I've been a Ubuntu user for years, and a Linux user for even more years. However, with this issue I don't know where to start, especially since my core field using Linux was always more towards servers and headless operations, and this seems to be X11-related.

I have a Lenovo X1 Carbon (20BS, a 2015 model) and am running Ubuntu 15.10 on it (4.2.0.25-generic). So far everything works great, however, when I undock the notebook from my OneLink Pro Dock, it goes back to text terminal (where old start-up messages are shown), and after a few seconds it goes back to login screen, and my session is terminated. Seems like X11 crashes and re-starts. I hear audio playing (which I'm listening to while working) until the very end of this crash, when the new login screen appears (also during the ~10 seconds of terminal). Then audio stops.

I checked **dmesg**. I noticed that throughout operation, it sporadically displays bursts of the following:

```

...
[13200.298026] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[13200.298199] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[13200.300399] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[13200.300683] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
...
```

I found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1488719](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1488719), which suggests problems with the video subsystem. However, note that these messages appear also during normal operation, not only during undock. I am using a monitor attached to the Dock's DisplayPort output.

These "control interrupt lied" lines appear during undock, along with WARNING messages and call traces (around 38 of them), I also found one segfault coming from TVGuiSlave.64 (TeamViewer, which I'm using).
The WARNING messages are, from what I've seen, always coming in pairs, there are two message types: **crtc's computed enabled state doesn't match tracked enabled state (expected 0, found 1)** and **WARN_ON(crtc->state->enable != intel_crtc_in_use(crtc))**. I'm showing one instance of both of these types each:

```

[17298.223359] ------------[ cut here ]------------
[17298.223369] WARNING: CPU: 1 PID: 1009 at /build/linux-ZKbhxl/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12304 check_crtc_state+0x3b3/0x440 [i915]()
[17298.223369] crtc's computed enabled state doesn't match tracked enabled state (expected 0, found 1)
[17298.223388] Modules linked in: rfcomm bnep dm_crypt drbg ansi_cprng algif_skcipher af_alg nls_iso8859_1 intel_rapl iosf_mbi arc4 x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm c
rct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd iwlmvm mac80211 joydev input_leds serio_raw cdc_ether usbnet r8152 mii iwlwifi uvcvideo lpc_ich vi
deobuf2_vmalloc videobuf2_memops videobuf2_core cfg80211 v4l2_common snd_usb_audio snd_usbmidi_lib snd_hda_codec_realtek snd_hda_codec_generic btusb snd_hda_codec_hdmi btrtl btbcm videodev btint
el media bluetooth snd_hda_intel snd_hda_codec thinkpad_acpi snd_hda_core snd_hwdep nvram snd_pcm snd_seq_midi shpchp snd_seq_midi_event snd_rawmidi mei_me snd_seq mei snd_seq_device snd_timer s
nd soundcore mac_hid parport_pc ppdev
[17298.223392]  lp parport autofs4 hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper psmouse e1000e drm ahci ptp libahci pps_core wmi video
[17298.223393] CPU: 1 PID: 1009 Comm: Xorg Tainted: G        W       4.2.0-25-generic #30-Ubuntu
[17298.223393] Hardware name: LENOVO 20BTS0UE00/20BTS0UE00, BIOS N14ET33W (1.11 ) 11/09/2015
[17298.223394]  0000000000000000 00000000c3b448d4 ffff8800c5e274b8 ffffffff817e94c9
[17298.223395]  0000000000000000 ffff8800c5e27510 ffff8800c5e274f8 ffffffff8107b3d6
[17298.223396]  0000000000000246 ffff8800c5e275a0 ffff88021fac4000 0000000000000001
[17298.223396] Call Trace:
[17298.223397]  [<ffffffff817e94c9>] dump_stack+0x45/0x57
[17298.223399]  [<ffffffff8107b3d6>] warn_slowpath_common+0x86/0xc0
[17298.223400]  [<ffffffff8107b465>] warn_slowpath_fmt+0x55/0x70
[17298.223408]  [<ffffffffc01d13fb>] ? intel_pipe_config_compare+0x5eb/0xc60 [i915]
[17298.223416]  [<ffffffffc01d1e23>] check_crtc_state+0x3b3/0x440 [i915]
[17298.223426]  [<ffffffffc01e5b5d>] intel_modeset_check_state+0x21d/0x6d0 [i915]
[17298.223434]  [<ffffffffc01e6d17>] intel_crtc_set_config+0x4c7/0x580 [i915]
[17298.223441]  [<ffffffffc005c4a6>] drm_mode_set_config_internal+0x66/0x100 [drm]
[17298.223444]  [<ffffffffc01482a5>] drm_fb_helper_pan_display+0x95/0xe0 [drm_kms_helper]
[17298.223453]  [<ffffffffc01f40ea>] intel_fbdev_pan_display+0x1a/0x60 [i915]
[17298.223455]  [<ffffffff81447e0f>] fb_pan_display+0xcf/0x160
[17298.223455]  [<ffffffff814482d2>] fb_set_var+0x252/0x460
[17298.223457]  [<ffffffff817ee176>] ? mutex_lock+0x16/0x40
[17298.223458]  [<ffffffff81212949>] ? do_sys_poll+0x149/0x5c0
[17298.223460]  [<ffffffff8143e512>] fbcon_blank+0x312/0x360
[17298.223468]  [<ffffffffc006bade>] ? drm_modeset_lock+0x4e/0xd0 [drm]
[17298.223469]  [<ffffffff814d3d93>] do_unblank_screen+0xd3/0x1a0
[17298.223471]  [<ffffffff814c927a>] vt_ioctl+0x50a/0x12f0
[17298.223472]  [<ffffffff811ddb84>] ? __slab_free+0x174/0x2c0
[17298.223473]  [<ffffffff814bc55c>] tty_ioctl+0x3cc/0xbc0
[17298.223475]  [<ffffffff811a7641>] ? kzfree+0x31/0x40
[17298.223476]  [<ffffffff811de046>] ? kfree+0x126/0x130
[17298.223477]  [<ffffffff81210aa5>] do_vfs_ioctl+0x295/0x480
[17298.223478]  [<ffffffff8121d9a4>] ? mntput+0x24/0x40
[17298.223479]  [<ffffffff811ff120>] ? __fput+0x190/0x220
[17298.223481]  [<ffffffff81210d09>] SyS_ioctl+0x79/0x90
[17298.223482]  [<ffffffff817f02b2>] entry_SYSCALL_64_fastpath+0x16/0x75
[17298.223483] ---[ end trace 14f3ad0509a289c5 ]---
```

```

[17298.223497] ------------[ cut here ]------------
[17298.223507] WARNING: CPU: 1 PID: 1009 at /build/linux-ZKbhxl/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:11895 __intel_set_mode+0x7f9/0xb60 [i915]()
[17298.223507] WARN_ON(crtc->state->enable != intel_crtc_in_use(crtc))
[17298.223524] Modules linked in: rfcomm bnep dm_crypt drbg ansi_cprng algif_skcipher af_alg nls_iso8859_1 intel_rapl iosf_mbi arc4 x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd iwlmvm mac80211 joydev input_leds serio_raw cdc_ether usbnet r8152 mii iwlwifi uvcvideo lpc_ich videobuf2_vmalloc videobuf2_memops videobuf2_core cfg80211 v4l2_common snd_usb_audio snd_usbmidi_lib snd_hda_codec_realtek snd_hda_codec_generic btusb snd_hda_codec_hdmi btrtl btbcm videodev btintel media bluetooth snd_hda_intel snd_hda_codec thinkpad_acpi snd_hda_core snd_hwdep nvram snd_pcm snd_seq_midi shpchp snd_seq_midi_event snd_rawmidi mei_me snd_seq mei snd_seq_device snd_timer snd soundcore mac_hid parport_pc ppdev
[17298.223528]  lp parport autofs4 hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper psmouse e1000e drm ahci ptp libahci pps_core wmi video
[17298.223529] CPU: 1 PID: 1009 Comm: Xorg Tainted: G        W       4.2.0-25-generic #30-Ubuntu
[17298.223529] Hardware name: LENOVO 20BTS0UE00/20BTS0UE00, BIOS N14ET33W (1.11 ) 11/09/2015
[17298.223530]  0000000000000000 00000000c3b448d4 ffff8800c5e27808 ffffffff817e94c9
[17298.223531]  0000000000000000 ffff8800c5e27860 ffff8800c5e27848 ffffffff8107b3d6
[17298.223532]  ffff8800c5e27878 ffff88021fac4000 ffff8800358c5000 ffff8800b6cd4f00
[17298.223532] Call Trace:
[17298.223533]  [<ffffffff817e94c9>] dump_stack+0x45/0x57
[17298.223535]  [<ffffffff8107b3d6>] warn_slowpath_common+0x86/0xc0
[17298.223536]  [<ffffffff8107b465>] warn_slowpath_fmt+0x55/0x70
[17298.223544]  [<ffffffffc01dfc79>] __intel_set_mode+0x7f9/0xb60 [i915]
[17298.223552]  [<ffffffffc01e6b06>] intel_crtc_set_config+0x2b6/0x580 [i915]
[17298.223559]  [<ffffffffc005c4a6>] drm_mode_set_config_internal+0x66/0x100 [drm]
[17298.223562]  [<ffffffffc01482a5>] drm_fb_helper_pan_display+0x95/0xe0 [drm_kms_helper]
[17298.223571]  [<ffffffffc01f40ea>] intel_fbdev_pan_display+0x1a/0x60 [i915]
[17298.223573]  [<ffffffff81447e0f>] fb_pan_display+0xcf/0x160
[17298.223574]  [<ffffffff81441f40>] bit_update_start+0x20/0x50
[17298.223576]  [<ffffffff8143f003>] fbcon_switch+0x3b3/0x650
[17298.223577]  [<ffffffff814d28dc>] redraw_screen+0x1ac/0x2a0
[17298.223578]  [<ffffffff8143e320>] fbcon_blank+0x120/0x360
[17298.223587]  [<ffffffffc006bade>] ? drm_modeset_lock+0x4e/0xd0 [drm]
[17298.223588]  [<ffffffff814d3d93>] do_unblank_screen+0xd3/0x1a0
[17298.223590]  [<ffffffff814c927a>] vt_ioctl+0x50a/0x12f0
[17298.223590]  [<ffffffff811ddb84>] ? __slab_free+0x174/0x2c0
[17298.223592]  [<ffffffff814bc55c>] tty_ioctl+0x3cc/0xbc0
[17298.223594]  [<ffffffff811a7641>] ? kzfree+0x31/0x40
[17298.223595]  [<ffffffff811de046>] ? kfree+0x126/0x130
[17298.223596]  [<ffffffff81210aa5>] do_vfs_ioctl+0x295/0x480
[17298.223597]  [<ffffffff8121d9a4>] ? mntput+0x24/0x40
[17298.223598]  [<ffffffff811ff120>] ? __fput+0x190/0x220
[17298.223600]  [<ffffffff81210d09>] SyS_ioctl+0x79/0x90
[17298.223601]  [<ffffffff817f02b2>] entry_SYSCALL_64_fastpath+0x16/0x75
[17298.223602] ---[ end trace 14f3ad0509a289c6 ]---
```

After I dock back again, some more "master control interrupt lied" message arrive, USB devices start to register back, network re-connects and no further messages are shown.

The Xorg log shows a segfault on undock:

```

[    20.725] (II) XKB: reuse xkmfile /var/lib/xkb/server-82F42E1A59A2C74D1D61D4D34E56C5CCF8374381.xkm
[ 17283.920] (EE) intel(0): page flipping failed, on CRTC:25 (pipe=1), disabling synchronous page flips
[ 17283.923] (EE) intel(0): failed to set mode: No such file or directory [2]
[ 17283.923] (II) intel(0): Disabled output DP2-1
[ 17283.923] (II) intel(0): Disabled output DP2-2
[ 17283.923] (II) intel(0): Disabled output DP2-3
[ 17283.926] (EE) intel(0): Failed to restore display configuration
[ 17283.926] (EE)
[ 17283.926] (EE) Backtrace:
[ 17283.926] (EE) 0: /usr/bin/X (xorg_backtrace+0x4e) [0x55874666668e]
[ 17283.926] (EE) 1: /usr/bin/X (0x5587464b2000+0x1b89f9) [0x55874666a9f9]
[ 17283.926] (EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (0x7f30709e6000+0x352f0) [0x7f3070a1b2f0]
[ 17283.926] (EE) 3: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f306cdbd000+0x103bf0) [0x7f306cec0bf0]
[ 17283.926] (EE) 4: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f306cdbd000+0x106c19) [0x7f306cec3c19]
[ 17283.926] (EE) 5: /usr/bin/X (DRI2SwapBuffers+0x1c8) [0x558746638d58]
[ 17283.926] (EE) 6: /usr/bin/X (0x5587464b2000+0x1886dc) [0x55874663a6dc]
[ 17283.926] (EE) 7: /usr/bin/X (0x5587464b2000+0x5818f) [0x55874650a18f]
[ 17283.926] (EE) 8: /usr/bin/X (0x5587464b2000+0x5c34b) [0x55874650e34b]
[ 17283.926] (EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf0) [0x7f3070a06a40]
[ 17283.926] (EE) 10: /usr/bin/X (_start+0x29) [0x5587464f86c9]
[ 17283.926] (EE)
[ 17283.926] (EE) Segmentation fault at address 0x47168
[ 17283.926] (EE)
Fatal server error:
[ 17283.926] (EE) Caught signal 11 (Segmentation fault). Server aborting
[ 17283.926] (EE)
[ 17283.926] (EE)
Please consult the The X.Org Foundation support
    at http://wiki.x.org
 for help.
[ 17283.926] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 17283.926] (EE)
[ 17283.926] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 17284.030] (EE) Server terminated with error (1). Closing log file.
```


Another thing I noticed, which could be related, is that when I switch to VT1, and back to VT7, the displays are not aligned as I set it up, and the built-in display has the external monitor's resolution (they're not cloned, though). When I open the "Displays" dialog and use "Detect Displays", it suddenly re-arranges the displays and everything is correct.

What can I further diagnose to track down this problem? I guess it is a bug, since there is no dedicated "undock" functionality of the docking station (that I know of). After all, I'm just unplugging the power, screen and network, which all should be hot-pluggable ... I guess?

Thanks!
Michael

---

