---
title: "Ethernet stopped working after upgrade to 23.4 (RTL8168/8169)"
date: 2023-07-20
forum: Hardware
---

### Post by dorish on 2023-07-20
Hello,
I upgraded my machine to Kubuntu 23.4, and noticed the ethernet interface stopped working.
Reinstalled clean 23.4: 
- During installation I have internet access
- At boot, I sometimes have ~8 seconds of refreshing internet, then gone. No LAN, no ARP replies, etc.
- Same cable/setup works with an RTL8153 USB adapter

Machine is ASUSTeK COMPUTER INC. TP500LA/TP500LA, BIOS TP500LA.202 05/21/2014
Ethernet adapter is RTL8168 and driver is RTL8169 ?

**uname -a**
```
Linux dorish 6.2.0-25-generic #25-Ubuntu SMP PREEMPT_DYNAMIC Fri Jun 16 17:05:07 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```


**lspci:**
```
02:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
```


**dmesg:**
```
[  525.302296] r8169 0000:02:00.1 enp2s0f1: Link is Up - 1Gbps/Full - flow control rx/tx
[  525.302346] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0f1: link becomes ready
[  535.711104] ------------[ cut here ]------------
[  535.711112] NETDEV WATCHDOG: enp2s0f1 (r8169): transmit queue 0 timed out
[  535.711154] WARNING: CPU: 2 PID: 0 at net/sched/sch_generic.c:525 dev_watchdog+0x23a/0x250
[  535.711175] Modules linked in: hid_microsoft ff_memless snd_seq_dummy snd_hrtimer r8153_ecm cdc_ether usbnet r8152 mii binfmt_misc nls_iso8859_1 snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec intel_rapl_msr snd_hda_core intel_rapl_common mt76x0e x86_pkg_temp_thermal snd_hwdep intel_powerclamp mt76x0_common snd_pcm coretemp mt76x02_lib snd_seq_midi kvm_intel snd_seq_midi_event mt76 snd_rawmidi mei_hdcp mei_pxp kvm snd_seq mac80211 irqbypass uvcvideo rapl intel_cstate videobuf2_vmalloc ak8975 snd_seq_device videobuf2_memops spi_nor videobuf2_v4l2 asus_nb_wmi at24 snd_timer mtd cfg80211 mei_me videodev videobuf2_common snd libarc4 mc mei soundcore inv_mpu6050_i2c inv_mpu6050 industrialio_triggered_buffer kfifo_buf i2c_mux industrialio asus_wireless soc_button_array hid_multitouch joydev input_leds mac_hid serio_raw msr parport_pc ppdev lp parport efi_pstore dmi_sysfs ip_tables x_tables autofs4 hid_generic
[  535.711357]  usbhid hid i915 drm_buddy i2c_algo_bit ttm drm_display_helper cec crct10dif_pclmul crc32_pclmul polyval_clmulni polyval_generic rc_core ghash_clmulni_intel sha512_ssse3 aesni_intel mfd_aaeon drm_kms_helper syscopyarea asus_wmi crypto_simd ledtrig_audio rtsx_pci_sdmmc sysfillrect spi_intel_platform sparse_keymap sysimgblt spi_intel platform_profile cryptd rtsx_pci psmouse r8169 drm realtek ahci xhci_pci i2c_i801 xhci_pci_renesas libahci i2c_smbus lpc_ich video wmi pinctrl_lynxpoint
[  535.711453] CPU: 2 PID: 0 Comm: swapper/2 Not tainted 6.2.0-25-generic #25-Ubuntu
[  535.711461] Hardware name: ASUSTeK COMPUTER INC. TP500LA/TP500LA, BIOS TP500LA.202 05/21/2014
[  535.711465] RIP: 0010:dev_watchdog+0x23a/0x250
[  535.711478] Code: 00 e9 2b ff ff ff 48 89 df c6 05 3a a9 75 01 01 e8 3b 07 f8 ff 44 89 f1 48 89 de 48 c7 c7 38 26 47 b4 48 89 c2 e8 c6 0c 29 ff <0f> 0b e9 1c ff ff ff 66 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 40 00
[  535.711484] RSP: 0018:ffffaf9080144e38 EFLAGS: 00010246
[  535.711491] RAX: 0000000000000000 RBX: ffff9c5e1f738000 RCX: 0000000000000000
[  535.711497] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000000
[  535.711500] RBP: ffffaf9080144e68 R08: 0000000000000000 R09: 0000000000000000
[  535.711504] R10: 0000000000000000 R11: 0000000000000000 R12: ffff9c5e1f7384c8
[  535.711508] R13: ffff9c5e1f73841c R14: 0000000000000000 R15: 0000000000000000
[  535.711513] FS:  0000000000000000(0000) GS:ffff9c5f16f00000(0000) knlGS:0000000000000000
[  535.711519] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  535.711524] CR2: 0000300800795600 CR3: 000000002ca10005 CR4: 00000000001706e0
[  535.711529] Call Trace:
[  535.711533]  <IRQ>
[  535.711540]  ? __pfx_dev_watchdog+0x10/0x10
[  535.711552]  call_timer_fn+0x2c/0x160
[  535.711564]  ? __pfx_dev_watchdog+0x10/0x10
[  535.711575]  __run_timers+0x259/0x310
[  535.711585]  run_timer_softirq+0x1d/0x40
[  535.711593]  __do_softirq+0xd9/0x346
[  535.711601]  ? hrtimer_interrupt+0x11f/0x250
[  535.711613]  __irq_exit_rcu+0xa2/0xd0
[  535.711621]  irq_exit_rcu+0xe/0x20
[  535.711627]  sysvec_apic_timer_interrupt+0x92/0xd0
[  535.711635]  </IRQ>
[  535.711638]  <TASK>
[  535.711641]  asm_sysvec_apic_timer_interrupt+0x1b/0x20
[  535.711650] RIP: 0010:cpuidle_enter_state+0xde/0x6f0
[  535.711661] Code: 81 8e 4c e8 84 5b 42 ff 8b 53 04 49 89 c7 0f 1f 44 00 00 31 ff e8 62 43 41 ff 80 7d d0 00 0f 85 eb 00 00 00 fb 0f 1f 44 00 00 <45> 85 f6 0f 88 12 02 00 00 4d 63 ee 49 83 fd 09 0f 87 c7 04 00 00
[  535.711666] RSP: 0018:ffffaf90800cbe28 EFLAGS: 00000246
[  535.711673] RAX: 0000000000000000 RBX: ffff9c5f16f3db18 RCX: 0000000000000000
[  535.711677] RDX: 0000000000000002 RSI: 0000000000000000 RDI: 0000000000000000
[  535.711680] RBP: ffffaf90800cbe78 R08: 0000000000000000 R09: 0000000000000000
[  535.711684] R10: 0000000000000000 R11: 0000000000000000 R12: ffffffffb4ec31a0
[  535.711688] R13: 0000000000000004 R14: 0000000000000004 R15: 0000007cbade688a
[  535.711697]  ? cpuidle_enter_state+0xce/0x6f0
[  535.711706]  cpuidle_enter+0x2e/0x50
[  535.711714]  cpuidle_idle_call+0x153/0x1e0
[  535.711726]  do_idle+0x82/0x100
[  535.711734]  cpu_startup_entry+0x1d/0x20
[  535.711742]  start_secondary+0x122/0x160
[  535.711757]  secondary_startup_64_no_verify+0xe5/0xeb
[  535.711773]  </TASK>
[  535.711776] ---[ end trace 0000000000000000 ]---
[  535.741652] r8169 0000:02:00.1 enp2s0f1: rtl_chipcmd_cond == 1 (loop: 100, delay: 100).
[  535.763596] r8169 0000:02:00.1 enp2s0f1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[  535.784104] r8169 0000:02:00.1 enp2s0f1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[  535.804807] r8169 0000:02:00.1 enp2s0f1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[  535.825489] r8169 0000:02:00.1 enp2s0f1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[  535.846163] r8169 0000:02:00.1 enp2s0f1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[  535.866921] r8169 0000:02:00.1 enp2s0f1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[  535.887398] r8169 0000:02:00.1 enp2s0f1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[  535.908090] r8169 0000:02:00.1 enp2s0f1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[  535.928840] r8169 0000:02:00.1 enp2s0f1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
```

---

### Post by ahmed-hanafi-data on 2023-08-16
Hi I reported a bug here [https://bugs.launchpad.net/ubuntu/+bug/2031537](https://bugs.launchpad.net/ubuntu/+bug/2031537) may you please post your problem details there I think they could be related

---

### Post by SeijiSensei on 2023-08-16
Realteks are always an issue because they are proprietary. I had to connect one device with Realtek Ethernet and wifi hardware to my router with an Ethernet cable during installation. Then I checked the box to download third-party software when prompted by the installer. Ubuntu detected the Realtek device, downloaded the appropriate driver, and installed it. After that I had wifi.

I stick with LTS versions like 22.04. The next one will be 24.04 next April. I avoid interim releases since they can be buggy and have limited support.

---

### Post by ahmed-hanafi-data on 2023-08-17
thanks for the advice I will to try installing the proprietary driver manually and see what will happen

---

