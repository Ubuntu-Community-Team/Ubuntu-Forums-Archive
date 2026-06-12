---
title: "Getting 'Could not apply the stored configuration for monitors' error post-upgrade"
date: 2016-03-10
forum: Hardware
---

### Post by ja-leesa on 2016-03-10
Hi All:

I recently upgraded my Ubuntu installation from 14.04 to 15.10, and have since been getting a 'Could not apply the stored configuration for monitors' error. I use a Dell docking station with my laptop, and this error only appears when my laptop is already docked.

When I log in, the mouse pointer is usually missing and the screen resolution is out of wack. I have to log out and back in to get the mouse pointer back, and then navigate to 'Displays' to get the proper screen resolution. The resolution automatically fixes itself once the 'Displays' window opens, and the 'Could not apply the stored configuration for monitors' error then disappears.

There was a bit of a problem when I did my upgrade. The laptop was docked at the time, but both my external Dell monitor and my laptop's screen went completely black. I was able to boot into a terminal session using Ctrl+Alt+F6 and run a command to complete the upgrade. I'm sorry that I can't remember what it was, but it was mentioned in the upgrade output and I was near panicked that I'd lost my whole computer in this process so I ran it.

My graphics card is Intel Haswell Mobile. I get the following output (full of warnings) when I run the dmesg | grep drm command:

```
[    0.849492] [drm] Initialized drm 1.1.0 20060810
[    1.217618] [drm] Memory usable by graphics device = 2048M
[    1.217624] fb: switching to inteldrmfb from VESA VGA
[    1.217698] [drm] Replacing VGA console driver
[    1.224112] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.224114] [drm] Driver supports precise vblank timestamp query.
[    1.250456] fbcon: inteldrmfb (fb0) is primary device
[    1.250529] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.652403] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[   22.541490] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[   22.541513] WARNING: CPU: 1 PID: 1162 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[   22.541568]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[   22.541695]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[   22.541707]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[   22.541719]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[   22.541727]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[   22.541740]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[   47.568159] WARNING: CPU: 2 PID: 1162 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:1365 assert_plane.constprop.98+0x6f/0x90 [i915]()
[   47.568194]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[   47.568279]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[   47.568283]  [<ffffffffc013a7e2>] restore_fbdev_mode+0xc2/0xf0 [drm_kms_helper]
[   47.568287]  [<ffffffffc013c6b9>] drm_fb_helper_restore_fbdev_mode_unlocked+0x29/0x70 [drm_kms_helper]
[   47.568290]  [<ffffffffc013c731>] drm_fb_helper_set_par+0x31/0x60 [drm_kms_helper]
[   48.970033] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[   48.970055] WARNING: CPU: 1 PID: 2377 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[   48.970108]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[   48.970235]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[   48.970246]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[   48.970258]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[   48.970266]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[   48.970279]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[   68.795338] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[   68.795360] WARNING: CPU: 3 PID: 2377 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[   68.795419]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[   68.795516]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[   68.795525]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[   68.795534]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[   68.795540]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[   68.795547]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[   68.856218] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[   68.856243] WARNING: CPU: 1 PID: 2377 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[   68.856297]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[   68.856424]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[   68.856435]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[   68.856446]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[   68.856455]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[   68.856465]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[  158.141529] WARNING: CPU: 2 PID: 2377 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:1365 assert_plane.constprop.98+0x6f/0x90 [i915]()
[  158.141564]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[  158.141651]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[  158.141656]  [<ffffffffc013a7e2>] restore_fbdev_mode+0xc2/0xf0 [drm_kms_helper]
[  158.141659]  [<ffffffffc013c6b9>] drm_fb_helper_restore_fbdev_mode_unlocked+0x29/0x70 [drm_kms_helper]
[  158.141662]  [<ffffffffc013c731>] drm_fb_helper_set_par+0x31/0x60 [drm_kms_helper]
[  159.582900] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[  159.582922] WARNING: CPU: 1 PID: 3281 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[  159.582976]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[  159.583135]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[  159.583146]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[  159.583163]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[  159.583171]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[  159.583184]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[  178.071513] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[  178.071533] WARNING: CPU: 0 PID: 3281 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[  178.071577]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[  178.071683]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[  178.071693]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[  178.071703]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[  178.071709]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[  178.071718]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[  178.139064] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[  178.139086] WARNING: CPU: 0 PID: 3281 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[  178.139140]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[  178.139276]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[  178.139288]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[  178.139299]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[  178.139308]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[  178.139321]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[ 8989.192981] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[ 8989.192999] WARNING: CPU: 0 PID: 3281 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[ 8989.193040]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[ 8989.193140]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[ 8989.193149]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[ 8989.193158]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[ 8989.193163]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[ 8989.193174]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[ 8989.447588] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[ 8989.447604] WARNING: CPU: 0 PID: 3281 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[ 8989.447640]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[ 8989.447725]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[ 8989.447732]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[ 8989.447740]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[ 8989.447745]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[ 8989.447752]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[ 8989.513992] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
[ 8989.514012] WARNING: CPU: 2 PID: 3281 at /build/linux-PoTihC/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12330 check_crtc_state+0x2c5/0x440 [i915]()
[ 8989.514052]  hid_logitech_hidpp hid_logitech_dj usbhid hid crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw i915 gf128mul glue_helper ablk_helper cryptd psmouse i2c_algo_bit drm_kms_helper ahci e1000e drm libahci sdhci_pci ptp sdhci pps_core wmi video
[ 8989.514166]  [<ffffffffc006ff75>] ? drm_mode_create+0x25/0x60 [drm]
[ 8989.514175]  [<ffffffffc0069526>] drm_mode_set_config_internal+0x66/0x100 [drm]
[ 8989.514185]  [<ffffffffc006dbb9>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[ 8989.514192]  [<ffffffffc005e505>] drm_ioctl+0x125/0x610 [drm]
[ 8989.514205]  [<ffffffffc006d7d0>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]

```

I have tried removing my monitors.xml file, which didn't make a difference. The problem still exists upon reboot. I use a custom Ubuntu theme that was installed before the upgrade was attempted.

As mentioned, I have found that I can follow a few steps upon booting to get things back to normal, or even boot up with my laptop undocked and then dock it after everything loads...but I would greatly prefer to just be able to leave my laptop docked and turn it on using the power button on the docking station in the morning. Habits and such.

Any help or further instructions is appreciated. Thanks!

---

