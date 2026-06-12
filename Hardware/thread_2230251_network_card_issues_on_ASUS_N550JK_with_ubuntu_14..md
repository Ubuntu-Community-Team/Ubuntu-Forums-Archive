---
title: "network card issues on ASUS N550JK with ubuntu 14.04 LTS"
date: 2014-06-18
forum: Hardware
---

### Post by mp6058 on 2014-06-18
The network card (realtek gigabit ethernet) doesn't work, doesn't send or receive packets. There is an error message saying something about a transmit queue timeout. I'm including some output that may be relevant. I've tried pcie_aspm=off, rmmod+modprobe, but no clue.

Can somebody please help.

Thank you

Martin

# uname -a
Linux astro 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:00:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"

# smbios-sys-info
Libsmbios version:      2.2.28
Product Name:           N550JK
Vendor:                 ASUSTeK COMPUTER INC.
BIOS Version:           N550JK.204

# lspci -k -s 05:00.0
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device 200f
    Kernel driver in use: r8169

output from dmesg

[   89.796072] ------------[ cut here ]------------
[   89.796084] WARNING: CPU: 7 PID: 0 at /build/buildd/linux-3.13.0/net/sched/sch_generic.c:264 dev_watchdog+0x276/0x280()
[   89.796086] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
[   89.796087] Modules linked in: bnep rfcomm nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops rts5139(C) videobuf2_core hid_multitouch mcs7830 videodev usbnet asus_nb_wmi asus_wmi sparse_keymap snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec arc4 snd_hwdep snd_pcm x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel snd_page_alloc ath9k snd_seq_midi ath9k_common snd_seq_midi_event kvm ath9k_hw snd_rawmidi ath snd_seq mac80211 snd_seq_device joydev snd_timer ath3k serio_raw btusb snd bluetooth cfg80211 lpc_ich mei_me mei soundcore parport_pc ppdev lp parport mac_hid dm_crypt usbhid hid crct10dif_pclmul crc32_pclmul ghash_clmulni_intel nouveau aesni_intel aes_x86_64 lrw gf128mul i915 glue_helper ablk_helper cryptd mxm_wmi i2c_algo_bit ttm psmouse ahci r8169 drm_kms_helper libahci drm mii wmi video
[   89.796136] CPU: 7 PID: 0 Comm: swapper/7 Tainted: G         C   3.13.0-29-generic #53-Ubuntu
[   89.796137] Hardware name: ASUSTeK COMPUTER INC. N550JK/N550JK, BIOS N550JK.204 01/23/2014
[   89.796138]  0000000000000009 ffff88042efc3d98 ffffffff8171a214 ffff88042efc3de0
[   89.796141]  ffff88042efc3dd0 ffffffff810676bd 0000000000000000 ffff880412340000
[   89.796144]  ffff8804129b6480 0000000000000001 0000000000000007 ffff88042efc3e30
[   89.796146] Call Trace:
[   89.796148]  <IRQ>  [<ffffffff8171a214>] dump_stack+0x45/0x56
[   89.796156]  [<ffffffff810676bd>] warn_slowpath_common+0x7d/0xa0
[   89.796158]  [<ffffffff8106772c>] warn_slowpath_fmt+0x4c/0x50
[   89.796162]  [<ffffffff8163efc6>] dev_watchdog+0x276/0x280
[   89.796165]  [<ffffffff8163ed50>] ? dev_graft_qdisc+0x80/0x80
[   89.796168]  [<ffffffff81074226>] call_timer_fn+0x36/0x100
[   89.796171]  [<ffffffff8163ed50>] ? dev_graft_qdisc+0x80/0x80
[   89.796173]  [<ffffffff810751bf>] run_timer_softirq+0x1ef/0x2f0
[   89.796176]  [<ffffffff8106caec>] __do_softirq+0xec/0x2c0
[   89.796179]  [<ffffffff8106d035>] irq_exit+0x105/0x110
[   89.796182]  [<ffffffff8172cfc5>] smp_apic_timer_interrupt+0x45/0x60
[   89.796186]  [<ffffffff8172b95d>] apic_timer_interrupt+0x6d/0x80
[   89.796187]  <EOI>  [<ffffffff815cd0f2>] ? cpuidle_enter_state+0x52/0xc0
[   89.796191]  [<ffffffff815cd219>] cpuidle_idle_call+0xb9/0x1f0
[   89.796196]  [<ffffffff8101ce9e>] arch_cpu_idle+0xe/0x30
[   89.796199]  [<ffffffff810beb95>] cpu_startup_entry+0xc5/0x290
[   89.796202]  [<ffffffff81040fb8>] start_secondary+0x218/0x2c0
[   89.796204] ---[ end trace 215922eb1d7267b2 ]---

---

### Post by jeremy31 on 2014-06-18
Should run varunendra's wireless script and post results ```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

---

### Post by mp6058 on 2014-06-19
I'm attaching the resulting tar.gz file.

---

