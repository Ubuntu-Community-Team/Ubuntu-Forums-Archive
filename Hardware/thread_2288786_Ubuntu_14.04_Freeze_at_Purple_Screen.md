---
title: "Ubuntu 14.04 Freeze at Purple Screen"
date: 2015-07-29
forum: Hardware
---

### Post by billyauhk on 2015-07-29
My Acer Aspire with Ubuntu 14.04 freezes when boot and cannot progress to the login screen. It freezes at the 
The recovery mode sometimes work, but the failsafeX also fails reporting no screen detected (that probably due to the CUDA driver).
Before the kernel being tainted by the nVidia driver, I get these from the dmesg:
```

[    8.965205] ------------[ cut here ]------------
[    8.965853] WARNING: CPU: 1 PID: 30 at /build/linux-kDCE9u/linux-3.13.0/drivers/gpu/drm/i915/intel_pm.c:5851 i915_request_power_well+0x77/0x80 [i915]()
[    8.966525] Modules linked in: ath9k(+) crct10dif_pclmul snd_hda_codec_realtek crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper i915 snd_hda_intel ath9k_common ablk_helper cryptd ath9k_hw snd_hda_codec ath joydev serio_raw mac80211 snd_hwdep snd_pcm drm_kms_helper snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq cfg80211 mei_me ath3k snd_seq_device snd_timer rtsx_pci_ms btusb bluetooth drm mei snd memstick i2c_algo_bit soundcore lpc_ich shpchp wmi video mac_hid hid_generic usbhid hid rtsx_pci_sdmmc tg3 ahci libahci ptp psmouse rtsx_pci pps_core
[    8.969578] CPU: 1 PID: 30 Comm: kworker/1:0 Not tainted 3.13.0-59-generic #98-Ubuntu
[    8.970354] Hardware name: Acer Aspire V3-772/VA70_HW, BIOS V1.12 09/19/2013
[    8.971123] Workqueue: events azx_probe_work [snd_hda_intel]
[    8.971887]  0000000000000009 ffff880253b8bd48 ffffffff81723700 0000000000000000
[    8.972706]  ffff880253b8bd80 ffffffff8106785d 0000000000000000 0000000000000000
[    8.973512]  0000000000000000 ffff88003ed12000 0000000000000040 ffff880253b8bd90
[    8.973656] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    8.973939] ieee80211 phy0: Atheros AR9462 Rev:2 mem=0xffffc90011480000, irq=18
[    8.976165] Call Trace:
[    8.977504]  [<ffffffff81723700>] dump_stack+0x45/0x56
[    8.978825]  [<ffffffff8106785d>] warn_slowpath_common+0x7d/0xa0
[    8.979802]  [<ffffffff8106793a>] warn_slowpath_null+0x1a/0x20
[    8.980593]  [<ffffffffa04e64e7>] i915_request_power_well+0x77/0x80 [i915]
[    8.981378]  [<ffffffffa02e1fe2>] hda_display_power+0x32/0x40 [snd_hda_intel]
[    8.982171]  [<ffffffffa02e08a9>] azx_probe_continue+0x59/0xa20 [snd_hda_intel]
[    8.982964]  [<ffffffffa02e1d75>] azx_probe_work+0x15/0x20 [snd_hda_intel]
[    8.983737]  [<ffffffff81083bf2>] process_one_work+0x182/0x450
[    8.984497]  [<ffffffff810849e1>] worker_thread+0x121/0x410
[    8.985254]  [<ffffffff810848c0>] ? rescuer_thread+0x430/0x430
[    8.986010]  [<ffffffff8108b7d2>] kthread+0xd2/0xf0
[    8.986761]  [<ffffffff8108b700>] ? kthread_create_on_node+0x1c0/0x1c0
[    8.987513]  [<ffffffff817341e3>] ret_from_fork+0x53/0x80
[    8.988262]  [<ffffffff8108b700>] ? kthread_create_on_node+0x1c0/0x1c0
[    8.989053] ---[ end trace 6d601bebfd175570 ]---

```

Am I getting the same bug as [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320851](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320851)?

---

### Post by mörgæs on 2015-08-01
How does it work in a live boot of 15.04?

---

### Post by billyauhk on 2015-08-22
Hi Morgaes sorry for the late update as I have been out of town for a week.
Just tested it with a live 15.04 USB and boots okay.
But what's intriguing is the freeze isn't occurs every time when I boot my 14.04.3

Bill

---

### Post by mörgæs on 2015-08-23
It's not really worth it to wonder what's wrong with 14.04. Just go for 15.04.

---

