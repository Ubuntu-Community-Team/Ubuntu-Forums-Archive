---
title: "Low memory corruption logged, NVidia 640 in use"
date: 2018-02-25
forum: Hardware
---

### Post by John Nagle on 2018-02-25
I'm getting occasional "Low memory corruption" errors when running a  Second Life viewer. Don't get these when not doing intensive 3D  graphics.

Ubuntu 16.04 LTS, updated to current in the last few hours.

NVidia GeForce GT 640/PCIe/SSE2
Driver is "NVidia binary driver - version 387.34 from nvidia-387 (open source). 

Getting a reliable driver for this card has been a problem. Earlier drivers tended to result in compiz crashes every few minutes.
What's the best thinking on this now?  There's a "390.24" available. I'm going to try that next. 

Error from dmesg: 
[ 2760.744033] Corrupted low memory at ffff880000004000 (4000 phys) = 0002da45
[ 2760.744042] ------------[ cut here ]------------
[  2760.744048] WARNING: CPU: 2 PID: 248 at  /build/linux-HSAA8v/linux-4.4.0/arch/x86/kernel/check.c:141  check_for_bios_corruption.part.1+0xaf/0x100()
[ 2760.744049] Memory corruption detected in low memory
[  2760.744049] Modules linked in: ipmi_msghandler binfmt_misc eeepc_wmi  asus_wmi sparse_keymap intel_rapl x86_pkg_temp_thermal intel_powerclamp  coretemp kvm irqbypass nvidia_uvm(POE) crct10dif_pclmul crc32_pclmul  ghash_clmulni_intel aesni_intel snd_usb_audio snd_usbmidi_lib joydev  input_leds aes_x86_64 snd_hda_codec_realtek snd_hda_codec_hdmi  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core lrw  gf128mul glue_helper ablk_helper cryptd snd_seq_midi snd_seq_midi_event  snd_rawmidi snd_hwdep snd_seq snd_pcm snd_seq_device snd_timer mei_me  mei snd shpchp serio_raw soundcore wmi lpc_ich 8250_fintek  soc_button_array tpm_infineon mac_hid cuse parport_pc ppdev lp parport  autofs4 hid_generic usbhid hid nvidia_drm(POE) nvidia_modeset(POE)  nvidia(POE) drm_kms_helper syscopyarea psmouse sysfillrect
[ 2760.744077]  sysimgblt fb_sys_fops ahci drm r8169 libahci mii fjes video
[ 2760.744082] CPU: 2 PID: 248 Comm: kworker/2:2 Tainted: P           OE   4.4.0-112-generic #135-Ubuntu
[ 2760.744083] Hardware name: ASUS All Series/Z87M-PLUS, BIOS 0311 04/18/2013
[ 2760.744087] Workqueue: events check_corruption
[ 2760.744088]  0000000000000286 af730eaee0514d37 ffff8802103c3d20 ffffffff813fc233
[ 2760.744090]  ffff8802103c3d68 ffffffff81cb25e0 ffff8802103c3d58 ffffffff81081f82
[ 2760.744091]  0000000000000000 ffff880000010000 ffffffff8210d1f0 0000000000000001
[ 2760.744092] Call Trace:
[ 2760.744096]  [<ffffffff813fc233>] dump_stack+0x63/0x90
[ 2760.744099]  [<ffffffff81081f82>] warn_slowpath_common+0x82/0xc0
[ 2760.744101]  [<ffffffff8108201c>] warn_slowpath_fmt+0x5c/0x80
[ 2760.744103]  [<ffffffff8106555f>] check_for_bios_corruption.part.1+0xaf/0x100
[ 2760.744105]  [<ffffffff810655c8>] check_corruption+0x18/0x50
[ 2760.744107]  [<ffffffff8109b815>] process_one_work+0x165/0x480
[ 2760.744109]  [<ffffffff8109bb7b>] worker_thread+0x4b/0x4d0
[ 2760.744110]  [<ffffffff8109bb30>] ? process_one_work+0x480/0x480
[ 2760.744112]  [<ffffffff810a1eb5>] kthread+0xe5/0x100
[ 2760.744114]  [<ffffffff810a1dd0>] ? kthread_create_on_node+0x1e0/0x1e0
[ 2760.744116]  [<ffffffff81845b9f>] ret_from_fork+0x3f/0x70
[ 2760.744117]  [<ffffffff810a1dd0>] ? kthread_create_on_node+0x1e0/0x1e0
[ 2760.744118] ---[ end trace c0779e0d06e54228 ]---

---

### Post by John Nagle on 2018-02-25
Related message:

NVRM: Your system is not currently configured to drive a VGA console
               on the primary VGA device. The NVIDIA Linux graphics driver
               requires the use of a text-mode VGA console. Use of other console
               drivers including, but not limited to, vesafb, may result in
               corruption and stability problems, and is not supported.

There are postings from 2015 about this being due to NVidia not supporting UEFI boot mode yet, but that must have been fixed by now. There are other postings suggesting this is harmless and just results in big fonts on text consoles. Available info is contradictory.

---

### Post by John Nagle on 2018-02-26
Trying NVidia driver "390.24". So far, no low memory corruption.

---

