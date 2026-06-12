---
title: "MEDION AKOYA E2215T notebook support under Ubuntu"
date: 2017-01-24
forum: Hardware
---

### Post by fulgor2011 on 2017-01-24
Hello,

I would like to know if Ubuntu will support this computer in the future:

 MEDION AKOYA E2215T notebook 


[LIST]
[*]CPU: Intel® Atom™™ x5-Z8350
[*]Graphics: Intel® HD
[/LIST]

Linux often crashed: the screen becomes black after several minutes and I have to reboot the computer.
I looked at log file 

```
[   63.284610] ------------[ cut here ]------------
[   63.284801] WARNING: CPU: 2 PID: 804 at  /build/linux-lIgGMF/linux-4.8.11/drivers/gpu/drm/i915/intel_uncore.c:802  __unclaimed_reg_debug+0x49/0x60 [i915]
[   63.284806] Unclaimed write to register 0x1e0100
[   63.284975] Modules linked in: ctr ccm fuse cmac bnep nls_ascii  nls_cp437 vfat fat joydev rtsx_usb_ms rtsx_usb_sdmmc memstick  hid_generic iTCO_wdt arc4 iTCO_vendor_support intel_rapl evdev coretemp  kvm_intel kvm uvcvideo videobuf2_vmalloc iwlmvm irqbypass  videobuf2_memops crct10dif_pclmul crc32_pclmul videobuf2_v4l2 mac80211  videobuf2_core rtsx_usb btusb ghash_clmulni_intel videodev btrtl  efi_pstore media btbcm usbhid btintel efivars pcspkr bluetooth i915  hid_multitouch iwlwifi cfg80211 snd_intel_sst_acpi rfkill drm_kms_helper  snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_sst_match  snd_soc_rt5645 snd_soc_rt5640 shpchp drm snd_soc_rl6231 lpc_ich mfd_core  snd_soc_core snd_compress processor_thermal_device i2c_algo_bit  intel_soc_dts_iosf snd_pcm kxcjk_1013 industrialio_triggered_buffer  dw_dmac
[   63.285099]  kfifo_buf snd_timer video dw_dmac_core industrialio  battery snd soundcore tpm_crb soc_button_array ac int3400_thermal  tpm_tis int3403_thermal acpi_thermal_rel int340x_thermal_zone  tpm_tis_core tpm acpi_pad button efivarfs ip_tables x_tables autofs4  ext4 crc16 jbd2 crc32c_generic fscrypto ecb mbcache mmc_block i2c_hid  hid crc32c_intel aesni_intel aes_x86_64 glue_helper lrw gf128mul  ablk_helper cryptd xhci_pci xhci_hcd usbcore usb_common thermal fjes  sdhci_acpi i2c_designware_platform i2c_designware_core sdhci mmc_core
[   63.285111] CPU: 2 PID: 804 Comm: kworker/u8:16 Not tainted 4.8.0-2-amd64 #1 Debian 4.8.11-1
[   63.285114] Hardware name: MEDION E2218T MD60200/NT16H, BIOS 5.11 11/08/2016
[   63.285135] Workqueue: events_unbound async_run_entry_fn
[   63.285153]  0000000000000086 00000000e46da50a ffffffffbc1269f5 ffffa12a37d4bc98
[   63.285166]  0000000000000000 ffffffffbbe7c16e 0000000000000000 ffffa12a37d4bcf0
[   63.285179]  0000000000000000 00000000050007fc ffffa12a3a310738 ffffffffbc63739c
[   63.285182] Call Trace:
[   63.285201]  [<ffffffffbc1269f5>] ? dump_stack+0x5c/0x77
[   63.285215]  [<ffffffffbbe7c16e>] ? __warn+0xbe/0xe0
[   63.285226]  [<ffffffffbbe7c1ef>] ? warn_slowpath_fmt+0x5f/0x80
[   63.285397]  [<ffffffffc086a827>] ? vlv_sideband_rw.constprop.0+0x187/0x210 [i915]
[   63.285563]  [<ffffffffc082e459>] ? __unclaimed_reg_debug+0x49/0x60 [i915]
[   63.285729]  [<ffffffffc0834d57>] ? chv_write32+0x347/0x3a0 [i915]
[   63.285880]  [<ffffffffc07f640e>] ? intel_power_domains_init_hw+0x3ae/0x550 [i915]
[   63.286021]  [<ffffffffc07d9560>] ? i915_pm_thaw_early+0x10/0x10 [i915]
[   63.286162]  [<ffffffffc07d9428>] ? i915_drm_resume_early+0xb8/0x130 [i915]
[   63.286175]  [<ffffffffbc26b938>] ? dpm_run_callback+0x48/0x130
[   63.286185]  [<ffffffffbc26bc0d>] ? device_resume_early+0x7d/0x130
[   63.286196]  [<ffffffffbc26bcd9>] ? async_resume_early+0x19/0x40
[   63.286204]  [<ffffffffbbe9d5e4>] ? async_run_entry_fn+0x34/0x140
[   63.286214]  [<ffffffffbbe94e00>] ? process_one_work+0x160/0x410
[   63.286223]  [<ffffffffbbe950fd>] ? worker_thread+0x4d/0x480
[   63.286232]  [<ffffffffbbe950b0>] ? process_one_work+0x410/0x410
[   63.286242]  [<ffffffffbbe9aecd>] ? kthread+0xcd/0xf0
[   63.286254]  [<ffffffffbc3efcaf>] ? ret_from_fork+0x1f/0x40
[   63.286264]  [<ffffffffbbe9ae00>] ? kthread_create_on_node+0x190/0x190
[   63.286271] ---[ end trace ee9b4eba38a434bb ]---


lspci
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor  x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 22)
00:02.0 VGA compatible controller: Intel Corporation  Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI  Configuration Registers (rev 22)
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium  Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 22)
00:0b.0 Signal processing controller: Intel Corporation  Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power  Management Controller (rev 22)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor  x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 22)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium  Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 22)
00:1c.0 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 (rev 22)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 22)
01:00.0 Network controller: Intel Corporation Wireless 3165 (rev 91)

lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 090c:037c Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 300k Pixel Camera
Bus 001 Device 006: ID 0911:2188 Philips Speech Processing 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Regards,

---

### Post by wildmanne39 on 2017-01-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by mörgæs on 2017-01-26
> **fulgor2011 said:**
> I would like to know if Ubuntu will support this computer in the future


Maybe they do already. Have you tried a live boot of the development version (17.04)?

---

