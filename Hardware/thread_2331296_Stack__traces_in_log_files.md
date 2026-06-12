---
title: "Stack  traces in log files"
date: 2016-07-20
forum: Hardware
---

### Post by georgesgiralt on 2016-07-20
Hello !
My laptop is a Lenovo Thinkpad E540 with an Intel Core i5 processor and an Optimus NVidia card. Exact type 20C600JHFR.
It runs Ubuntu 14.04.4 LTS kept current.
Some time ago I began finding error reports in the syslog log file like this one :
```

[17416.423061] ------------[ cut here ]------------
[17416.423096] WARNING: CPU: 0 PID: 1720 at /build/linux-lts-utopic-LNSxQk/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_pm.c:5936 intel_display_power_put+0x135/0x160 [i915]()
[17416.423097] Modules linked in: uas usb_storage msr acpi_call(OE) pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bbswitch(OE) autofs4 ctr ccm uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media btusb snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic arc4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul iwlmvm mac80211 aesni_intel aes_x86_64 lrw gf128mul glue_helper snd_hda_intel ablk_helper cryptd snd_hda_controller iwlwifi snd_hda_codec snd_hwdep snd_pcm joydev serio_raw cfg80211 snd_seq_midi snd_seq_midi_event lpc_ich rtsx_pci_ms memstick bnep wmi rfcomm bluetooth thinkpad_acpi snd_rawmidi 6lowpan_iphc i915 nvram snd_seq snd_seq_device drm_kms_helper snd_timer drm video i2c_algo_bit snd mei_me mei shpchp mac_hid soundcore parport_pc ppdev nfsd auth_rpcgss nfs_acl binfmt_misc lp nfs parport lockd sunrpc fscache nls_iso8859_1 hid_generic usbhid hid raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor rtsx_pci_sdmmc psmouse raid6_pq ahci libahci raid1 r8169 rtsx_pci raid0 mii multipath linear
[17416.423146] CPU: 0 PID: 1720 Comm: Xorg Tainted: G           OE 3.16.0-77-generic #99~14.04.1-Ubuntu
[17416.423147] Hardware name: LENOVO 20C600JHFR/20C600JHFR, BIOS J9ET9DWW (2.23 ) 02/04/2016
[17416.423148]  0000000000000000 ffff88032a353ae8 ffffffff8176d1a8 0000000000000000
[17416.423150]  0000000000000009 ffff88032a353b20 ffffffff8106edbd ffff88032bd1002c
[17416.423151]  ffff88032bd10000 ffff88032a710370 ffff88032bd18548 ffff88032bd10000
[17416.423153] Call Trace:
[17416.423160]  [<ffffffff8176d1a8>] dump_stack+0x64/0x82
[17416.423165]  [<ffffffff8106edbd>] warn_slowpath_common+0x7d/0xa0
[17416.423167]  [<ffffffff8106ee9a>] warn_slowpath_null+0x1a/0x20
[17416.423178]  [<ffffffffc04bab05>] intel_display_power_put+0x135/0x160 [i915]
[17416.423192]  [<ffffffffc0503114>] modeset_update_crtc_power_domains+0x204/0x210 [i915]
[17416.423205]  [<ffffffffc050312e>] haswell_modeset_global_resources+0xe/0x10 [i915]
[17416.423217]  [<ffffffffc05047cb>] __intel_set_mode+0x60b/0xa90 [i915]
[17416.423229]  [<ffffffffc0507a26>] intel_set_mode+0x16/0x30 [i915]
[17416.423240]  [<ffffffffc050899d>] intel_crtc_set_config+0x8ed/0xdb0 [i915]
[17416.423253]  [<ffffffffc0431521>] drm_mode_set_config_internal+0x61/0xe0 [drm]
[17416.423263]  [<ffffffffc0434f51>] drm_mode_setcrtc+0xe1/0x570 [drm]
[17416.423270]  [<ffffffffc0425a3c>] drm_ioctl+0x1ec/0x660 [drm]
[17416.423274]  [<ffffffff811e9960>] do_vfs_ioctl+0x2e0/0x4c0
[17416.423277]  [<ffffffff810831d9>] ? restore_altstack+0x19/0x30
[17416.423279]  [<ffffffff811e9bc1>] SyS_ioctl+0x81/0xa0
[17416.423281]  [<ffffffff8177590d>] system_call_fastpath+0x1a/0x1f
[17416.423282] ---[ end trace f587103f708e273e ]---

```
As I had other hardware related errors and intermittent contacts on the touch pad and USB ports, I thought it was related. 
Last week, the Lenovo support exchanged the main board on this laptop. Since then, no more hardware issues ! 
But today I began getting these errors again ! 
I have to admit I was never been able to make Bumblebee or other Optimus support to work on this laptop. But as !I did not buy this laptop to make use of performance graphic card, i did not care.
I did not find anything about this error that makes sense to me, so your help would be very appreciated.

---

### Post by Yellow Pasque on 2016-07-21
Have you tried a newer kernel? [https://bugs.freedesktop.org/show_bug.cgi?id=89733](https://bugs.freedesktop.org/show_bug.cgi?id=89733)

It looks like you're using the Utopic LTS kernel: 3.16.0-77-generic

---

### Post by georgesgiralt on 2016-07-21
Well,
I choose Ubuntu at home for the ease of use... 
I run the standard software on a standard hardware in order to stay away from such experiments. 
I did not choose the kernel, the installer did it for me. Is there an alternative on the main Ubuntu repos ?

---

### Post by Yellow Pasque on 2016-07-21
You're running an LTS release, so kernels from later releases are backported for you and easily installable. [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)
As you can see, official support for some of the LTS kernels (including the one you're running) comes to an end next month.

The procedure is fairly simple in my view:
1. Install newer kernel
2. Reboot and newer kernel should be chosen automatically
3. See if error occurs and verify everything else still works properly
4. If you're happy, continue using the newer kernel
5. If you're not happy, boot into the older kernel and remove the newer one

If you're not comfortable booting into different kernels or bringing up the GRUB menu, then just forget about the error if it doesn't affect your system's function. I mean, you can file a bug, but the first thing they're going to tell you to do is check if the error occurs in later kernels.

Note: If you do decide to try a newer kernel, I would recommend not install newer graphics/Xserver components.

---

### Post by georgesgiralt on 2016-07-21
OK.
But if I look at the Wiki link you gave me, it seems I've changed kernel a lot since the first install of this laptop ;-) And without my knowledge ;-) 
Could you please point me to a document showing how I install a newer kernel ? Because I would like to keep the laptop in shape and not break it... Things I can do myself ;-) 
Thank a lot for your help.

---

