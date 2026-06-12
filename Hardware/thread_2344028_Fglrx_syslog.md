---
title: "Fglrx syslog"
date: 2016-11-21
forum: Hardware
---

### Post by wpsd on 2016-11-21
Hi I have two AMD GPU R9 380 in my desktop, now it just detect one 

I use ubuntu 14.04 with latest fglrx driver ( not amdgpu pro ) from AMD page 15.302 or something

I check my syslog and got this

```
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392060] Stack:
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392061]  ffff8801a3c77ab8 ffffffff813ed9eb 0000000000000001 000000ff00000004
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392062]  0000000000000103 0000000000000004 0000000000000102 0000000000000004
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392063]  ffff8801b969d000 ffff8801a3c77b48 ffff8801a3c77ac8 ffffffffc0467bbe
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392065] Call Trace:
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392069]  [<ffffffff813ed9eb>] pci_bus_read_config_byte+0x6b/0x80
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392188]  [<ffffffffc0467bbe>] KCL_PCI_ReadConfigByte+0x1e/0x20 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392230]  [<ffffffffc048286f>] ReadPCIConfig+0x7f/0xc0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392265]  [<ffffffffc047f00e>] ? MCIL_GetPciConfigData+0x9e/0xd0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392339]  [<ffffffffc05a61a3>] ? PECI_ReadPCIeConfigDword+0x83/0x140 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392400]  [<ffffffffc069bb13>] ? PPPCIeBus_FindCap+0x83/0xb0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392460]  [<ffffffffc069b6f4>] ? PPPCIeBus_GetBusParameters+0x34/0x1b0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392534]  [<ffffffffc05acf46>] ? PHM_ReadIndirectRegister+0x46/0xd0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392607]  [<ffffffffc059d577>] ? PHM_GetBusParameters+0x17/0x80 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392681]  [<ffffffffc05bafb3>] ? PEM_CWDDEPM_OD6_GetCurrentStatus+0x213/0x2f0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392719]  [<ffffffffc049c1ba>] ? firegl_trace+0x2a/0xf0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392792]  [<ffffffffc05b695a>] ? PP_Cwdde+0x12a/0x2e0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392824]  [<ffffffffc04674c2>] ? KCL_DEBUG_Print_Trace+0x22/0xd0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392862]  [<ffffffffc049efcd>] ? firegl_cwddepm_adl_handler+0xcd/0x150 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392865]  [<ffffffff811d1172>] ? __kmalloc+0x1d2/0x280
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392899]  [<ffffffffc0479da6>] ? Dispatch+0x1d6/0x240 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392932]  [<ffffffffc0469103>] ? drm_alloc+0x133/0x1a0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.392966]  [<ffffffffc04798de>] ? firegl_adl_escape+0xde/0x190 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.393000]  [<ffffffffc0479800>] ? _r6x_init_hw_ctx+0xd0/0xd0 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.393033]  [<ffffffffc0471414>] ? firegl_ioctl+0x1f4/0x260 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.393063]  [<ffffffffc045f1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.393066]  [<ffffffff81200ecd>] ? do_vfs_ioctl+0x2cd/0x4b0
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.393068]  [<ffffffff8169cbc2>] ? __sys_recvmsg+0x42/0x80
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.393070]  [<ffffffff81201129>] ? SyS_ioctl+0x79/0x90
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.393071]  [<ffffffff817c2ff2>] ? entry_SYSCALL_64_fastpath+0x16/0x75
Nov 22 07:53:55 ubuntu-pc kernel: [1269151.393072] Code: c7 06 00 00 00 00 75 a3 31 c0 eb a7 90 90 90 90 90 90 90 90 90 90 0f 1f 44 00 00 55 48 89 e5 c6 07 00 0f 1f 40 00 48 89 f7 57 9d <0f> 1f 44 00 00 5d c3 0f 1f 40 00 0f 1f 44 00 00 55 48 89 e5 f0
Nov 22 07:54:23 ubuntu-pc kernel: [1269179.383894] NMI watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [Xorg:1137]
Nov 22 07:54:23 ubuntu-pc kernel: [1269179.383896] Modules linked in: fglrx(POE) intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp bnep kvm_intel kvm crct10dif_pclmul crc32_pclmul cryptd rfcomm bluetooth serio_raw lpc_ich snd_seq_midi snd_seq_midi_event snd_rawmidi snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_seq snd_pcm snd_seq_device amd_iommu_v2 snd_timer ttm drm_kms_helper snd drm i2c_algo_bit soundcore mei_me shpchp mei 8250_fintek video mac_hid parport_pc soc_button_array ppdev lp parport uas usb_storage psmouse r8169 mii
```

Does this means my gpu fried ( hardware error ) ?
Or this is driver problem ?

---

### Post by QIII on 2016-11-21
Did you do ```
sudo amdconfig-initial adapter=all
``` after installing fglrx and before rebooting?

---

### Post by wpsd on 2016-11-21
> **QIII said:**
> Did you do ```
sudo amdconfig-initial adapter=all
``` after installing fglrx and before rebooting?

yep it only show one the working one, so I check from my previous syslog and see that part of log

---

### Post by wpsd on 2016-11-21
The symptom is my OS stuck, then I have to hard reboot and then one of the GPU is not detected. 

I check the syslog and got that part.

---

### Post by QIII on 2016-11-21
If they are, indeed, identical hardware, experiment with removing one or the other, switching PCI-e slots, etc.

That should help rule out hardware failure.

---

### Post by wpsd on 2016-11-21
Can I said that if that kind of format appear in syslog means gpu hardware failure ?

I test on windows 10 , the os cannot startup. on Ubuntu it could since the other one is ok but it produce that log.

---

