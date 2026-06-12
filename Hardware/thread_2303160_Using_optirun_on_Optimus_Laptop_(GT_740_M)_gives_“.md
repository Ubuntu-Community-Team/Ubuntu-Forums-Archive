---
title: "Using optirun on Optimus Laptop (GT 740 M) gives “Cannot access secondary GPU”"
date: 2015-11-16
forum: Hardware
---

### Post by Geosearchef on 2015-11-16
I'm trying to use bumblebee on an nvidia optimus laptop. I've got the  version 340 of the nvidia dirver installed with bumblebee and bbswitch.
  When trying to run optirun i get:


```
[  576.095946] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[  576.096180] [ERROR]Aborting because fallback start is disabled.
```

I found this error in my dmesg, the screen also blinks some times when starting. I'm using Ubuntu Gnome 15.10.

```
[   12.678314] WARNING: CPU: 0 PID: 282 at /build/linux-jJX2Dm/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:12326 check_crtc_state+0x2c5/0x440 [i915]()
[   12.678315] pipe state doesn't match!
[   12.678317] Modules linked in: arc4 iwldvm mac80211 intel_rapl iosf_mbi x86_pkg_temp_thermal intel_powerclamp snd_hda_codec_hdmi coretemp snd_hda_codec_realtek snd_hda_codec_generic uvcvideo snd_hda_intel kvm snd_hda_codec snd_hda_core hp_wmi sparse_keymap iwlwifi videobuf2_vmalloc videobuf2_memops snd_hwdep snd_pcm videobuf2_core v4l2_common crct10dif_pclmul videodev crc32_pclmul ghash_clmulni_intel snd_seq_midi snd_seq_midi_event snd_rawmidi cfg80211 aesni_intel media snd_seq aes_x86_64 snd_seq_device mei_me hp_accel snd_timer rtsx_pci_ms lrw lis3lv02d gf128mul glue_helper joydev mei memstick snd ablk_helper input_leds input_polldev cryptd serio_raw soundcore shpchp lpc_ich wmi hp_wireless mac_hid parport_pc ppdev lp parport autofs4 hid_generic usbhid hid rtsx_pci_sdmmc i915 i2c_algo_bit drm_kms_helper
[   12.678359]  psmouse ahci drm libahci r8169 mii rtsx_pci video
[   12.678367] CPU: 0 PID: 282 Comm: plymouthd Tainted: G          I     4.2.0-18-generic #22-Ubuntu
[   12.678368] Hardware name: Hewlett-Packard HP Pavilion 15 Notebook PC/2166, BIOS F.21 08/08/2013
[   12.678370]  0000000000000000 0000000099e2906f ffff8802506837c8 ffffffff817e8c09
[   12.678373]  0000000000000000 ffff880250683820 ffff880250683808 ffffffff8107b3c6
[   12.678375]  ffff880250683848 ffff8802506838b0 ffff8802512f2000 0000000000000001
[   12.678378] Call Trace:
[   12.678383]  [<ffffffff817e8c09>] dump_stack+0x45/0x57
[   12.678388]  [<ffffffff8107b3c6>] warn_slowpath_common+0x86/0xc0
[   12.678391]  [<ffffffff8107b455>] warn_slowpath_fmt+0x55/0x70
[   12.678407]  [<ffffffffc01a2bc1>] ? intel_pipe_config_compare+0xb31/0xc60 [i915]
[   12.678420]  [<ffffffffc01a2fb5>] check_crtc_state+0x2c5/0x440 [i915]
[   12.678438]  [<ffffffffc01b6d6d>] intel_modeset_check_state+0x21d/0x6d0 [i915]
[   12.678452]  [<ffffffffc01b7f27>] intel_crtc_set_config+0x4c7/0x580 [i915]
[   12.678467]  [<ffffffffc006cee5>] ? drm_mode_create+0x25/0x60 [drm]
[   12.678478]  [<ffffffffc00664c6>] drm_mode_set_config_internal+0x66/0x100 [drm]
[   12.678489]  [<ffffffffc006ab29>] drm_mode_setcrtc+0x3e9/0x500 [drm]
[   12.678497]  [<ffffffffc005b495>] drm_ioctl+0x125/0x610 [drm]
[   12.678507]  [<ffffffffc006a740>] ? drm_mode_setplane+0x1b0/0x1b0 [drm]
[   12.678511]  [<ffffffff812108a5>] do_vfs_ioctl+0x295/0x480
[   12.678514]  [<ffffffff81210b09>] SyS_ioctl+0x79/0x90
[   12.678518]  [<ffffffff817ef9f2>] entry_SYSCALL_64_fastpath+0x16/0x75
[   12.678520] ---[ end trace b650c54e2574579f ]---
[   12.679888] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in ips_enabled (expected 1, found 0)
```

bumblebee.conf:

```

# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d

## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau



```


```
geosearchef@geosearchef-ubuntuGnome:~$ dpkg --get-selections | grep -v deinstall | grep "bumblebee\|nvidia-\|bbswitch"
bbswitch-dkms                    install
bumblebee                    install
bumblebee-nvidia                install
nvidia-340                    install
nvidia-opencl-icd-340                install
nvidia-settings                    install
```

---

### Post by efflandt on 2015-11-16
Any particular reason you want to use bumblebee instead of nvidia-prime? Since Ubuntu 14.04 (or newer) nvidia driver packages include nvidia-prime and with a hybrid graphics laptop you can switch graphics using *NVIDIA X Server Settings*. I don't know if installing bumblebee uninstalls nvidia-prime (maybe it conflicts).

On my laptop I just need to log out of X and log back in when switching Intel to Nvidia from *NVIDIA X Server Settings*, but I need to reboot when switching Intel to Nvidia. So it may not be on the fly, but it seems to work better for both Intel and Nvidia graphics in 14.04 than it did using optirun in 13.10 (which required extra parameters to run Steam Source games). And I never could get primusrun to work for anything in 13.10.

I am using a newer version of nvidia drivers from graphics-drivers/ppa, but these are the packages that were installed when installing nvidia-355 (bumblebee is not installed):```
efflandt@GE60-2OE:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-355                                            355.11-0ubuntu0~gpu14.04.2                          amd64        NVIDIA binary driver - version 355.11
ii  nvidia-opencl-icd-355                                 355.11-0ubuntu0~gpu14.04.2                          amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       358.09-0ubuntu0~gpu14.04.1                          amd64        Tool for configuring the NVIDIA graphics driver
```

---

