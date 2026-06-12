---
title: "System hangs when booting with thunderbolt dock attached"
date: 2023-04-28
forum: Hardware
---

### Post by falka777 on 2023-04-28
Hello,

I have had this weird problem for a while where, if I boot my laptop with the dock attached, it hangs during the startup process. Until now, the error message was minimalistic, but with the update to 23.04, I am getting some more output, so I decided to try and ask ;)

First, here are the system details:

Laptop model: Thinkpad P14s
Dock: Lenovo ThinkPad Thunderbolt 3 Dock

lspci output:
```
[FONT=monospace][COLOR=#000000]00:00.0 Host bridge: Intel Corporation 11th Gen Core Processor Host Bridge/DRAM Registers (rev 01) [/COLOR]
00:02.0 VGA compatible controller: Intel Corporation TigerLake-LP GT2 [Iris Xe Graphics] (rev 01) 
00:04.0 Signal processing controller: Intel Corporation TigerLake-LP Dynamic Tuning Processor Participant (rev 01) 
00:06.0 PCI bridge: Intel Corporation 11th Gen Core Processor PCIe Controller (rev 01) 
00:07.0 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #1 (rev 01) 
00:07.2 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #2 (rev 01) 
00:0d.0 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 USB Controller (rev 01) 
00:0d.2 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 NHI #0 (rev 01) 
00:0d.3 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 NHI #1 (rev 01) 
00:14.0 USB controller: Intel Corporation Tiger Lake-LP USB 3.2 Gen 2x1 xHCI Host Controller (rev 20) 
00:14.2 RAM memory: Intel Corporation Tiger Lake-LP Shared SRAM (rev 20) 
00:14.3 Network controller: Intel Corporation Wi-Fi 6 AX201 (rev 20) 
00:15.0 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #0 (rev 20) 
00:15.1 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #1 (rev 20) 
00:16.0 Communication controller: Intel Corporation Tiger Lake-LP Management Engine Interface (rev 20) 
00:1c.0 PCI bridge: Intel Corporation Device a0b8 (rev 20) 
00:1c.7 PCI bridge: Intel Corporation Tiger Lake-LP PCI Express Root Port #8 (rev 20) 
00:1d.0 PCI bridge: Intel Corporation Tiger Lake-LP PCI Express Root Port #9 (rev 20) 
00:1f.0 ISA bridge: Intel Corporation Tiger Lake-LP LPC Controller (rev 20) 
00:1f.3 Audio device: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 20) 
00:1f.4 SMBus: Intel Corporation Tiger Lake-LP SMBus Controller (rev 20) 
00:1f.5 Serial bus controller: Intel Corporation Tiger Lake-LP SPI Controller (rev 20) 
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (13) I219-V (rev 20) 
01:00.0 3D controller: NVIDIA Corporation TU117GLM [Quadro T500 Mobile] (rev a1) 
04:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983 
08:00.0 Unassigned class [ff00]: Quectel Wireless Solutions Co., Ltd. EM120R-GL LTE Modem 
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01) 
50:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge DD 2018] (rev 06) 
51:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge DD 2018] (rev 06) 
51:04.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge DD 2018] (rev 06) 
52:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge DD 2018] (rev 06)[/FONT]
```

The root and swap partitions are encrypted (logical volume, default Ubuntu encryption setup, nothing fancy).

What works is booting without the dock attached, and then attaching it after the desktop manager has come up. If I boot with the dock attached, I can enter the disk encryption password and get the confirmation that the volume was successfully mounted, but then the boot process stops. If I press ESC, I get the following error message (seems to be a kernel panic, as I can't switch to virtual consoles and the error message "kernel NULL pointer dereference" doesn't sound like you can recover from it...):

```

[03415] blacklist: Problem blacklisting hash (-13) 
[38854] 
  Failed to start apport-autoreport.service - Process error reports when automatic reporting is enabled. 
[57.130964] pcieport 0000:51:04.0: Unable to change power state from D3hot to DO, device inaccessible
[39954] xhci_hcd 0000:52:00.0: xHCI host controller not responding, assume dead 
[35040] BUG: kernel NULL pointer dereference, address: 00000000000000398
[35055] #PF: supervisor write access in kernel mode
[35068] #PF: error_code(0x0002) - not-present page 
[35078] PGD 0 P4D 0
[35085] Oops: 0002 [#1] PREEMPT SMP NOPTI 
[35094] CPU: 0 PID: 202 Comm: kworker/0:2 Tainted: P OE 6.2.0-20-generic #20-Ubuntu 
[35110] Hardware name: LENOVO 20VX007VGE/20VX007VGE, BIOS N34ET52W (1.52 ) 06/21/2022
[35124] Workqueue: kacpi_notify acpi_os_execute_deferred 
[35137] RIP: 0010:queue_work_on+0x22/0x70 
[35147] Code: 90 90 90 90 90 90 90 90 ef 1f 44 00 00 55 41 89 fb 49 89 f2 49 89 de 48 89 e5 53 9c 58 Of if 40 00 48 89 c3 fa 0f 1f 44 00 00 <f0> 49 0f ba 28 00 73 2f 45 31 c9 80 e7 02 74 06 fb 0f 1f 44 00 00
[35174] RSP: 0018:ffffac80008a7df0 EFLAGS: 00010002 
[35184] RAX: 0000000000000202 RBX: 0000000000000202 RCX: 0000000000000000
[35196] RDX: eeeeeeeeeeeee39e RSI: ffffa05c40051000 RDI: 0000000000002000
[35208] RBP: ffffac80008a7df8 ROB: esegeeeeeseeesse R09: 0000000000000000 
[35221] R10: ffffa05c40051000 R11: 0000000000002000 R12:  0000000000000004
[35233] R13: eeeeeeeeeeeeeeee R14: ffffa05c584a0c50 R15: ffffaeSc44f4C300 
[35246] FS: 0000000000000000(0000) GS: ffffa0676f600000(0000) kn1GS:0000000000000000 
[35259] CS: 0010 DS: 0000 ES: 0000 CRO: 0000000080050033 
[35271] CR2: 0000000000000398 CR3: 0000000118612003 CR4: 0000000000770ef0
[35285] PKRU: 55555554 
[35291] Call Trace: 
[35298] <TASK> 
[35307] ucsi_connector_change+0x56/0xa0 [typec_ucsi] 
[35320] ucsi_acpi_notify+0xa1/0xb0 [ucsi_acpi] 
[35330] acpi_ev_notify_dispatch+0x54/0x80 
[35339] acpi_os_execute_deferred+0x17/0x40 
[35349] process_one_work+0x222/0x430 
[35358] worker_thread+0x50/0x3e0 
[35367] ? __pfx_worker_thread+0x10/0x10 
[35376] kthread+0xe6/0x110 
[35383] ? __pfx_kthread+0x10/0x10 
[35392] ret_from_fork+0x29/0x50 
[35400] </TASK> 
[35407] Modules linked in: vboxnetadp(OE) vboxnetflt(0E) yboxdr1(0E) xt_CHECKSUM xt_HASQUERADE xt_conntrack ipt_REJECT nf_reject_ipv4 xt_tcpudp nft_compat nft_chain_nat nf_nat nf_conntrack nf_defrag_ipv6 ni_defrag_ipv4 nf_tables libc tlink bridge stp Ilc rfcomm cmac algif_hash algif skcipher af alg bnep binfmt_misc nls_iso8859_1 snd_ctl_led snd_soc_skl_hda_dsp snd_soc_intel_hda_dsp_common snd_soc_hdac_hdmi snd_sof_probes srmilda_codec_hdmi snd_hda_codec_realte .codec_generic snd_soc_dmic snd_sof_pci_intel_tgl snd_sof_intel_hda_common soundwire_intel soundwire_generic_allocation soundwire_cadence snd_sof_intel_hda snd_sof_pci snd_sof_xtensa_dsp snd_sof snd_sof_utils snd soc_hdac hda snd_h e intel_tcc_cooling snd_soc_acpi_intel_match x86_pkg_temp_thermal snd_soc_acpi intel_powerclamp soundwire_bus coretemp mei_pxp mei_hdcp intel_rapl_msr snd_soc_core kvm_intel iwImma snd_compress ac97_bus kvm snd_T,cm_dmaeniine irqby 211 snd_hda_intel btusb rapl 439] libarc4 snd_intel_dspcfg btrtl intel_cstate snd_intel_sdw_acpi btbcm cmdlinepart btintel uvcvideo snd_hda_codec think_lmi videobuf2_vmalloc iwlwif i btmtk processor_thermal_device_pci_legacy snd_usb_audio spi_nor videobuf2_me ssor_thermal_device snd_hda_core processor_thermal_rfim videobuf2_v412 snd_seq_midi firmware_attributes_class bluetooth wmi_brnof snd_usbmidi_lib videodev thinkpad_acpi ecdh_generic snd_hwdep mad ee1004 warn ecc snd_seq_midi_event _common mei_me processor_thermal_mbox ucsi_acpi me cfg80211 mei snd_pcm snd_rawmidi processor_thermal_rapl typec_ucsi intel_rapl_common igen6_edac intel_soc_dts_iosf typec snd_seq sni_gm_device snd_limer snd soundcore ledtrig_aud _thermal int3403_thermal platform_profile int340x_thermal_zone acpi_thermal_rel intel_hid nvidia_uvm(POE) sparse_keymap acpi_tad acpi.pad hid_multitouch input_leds joydev serio_raw mac_hid msr parport_pc ppdev 1p parport efi_pstor s ip_tables x_tables autofs4 599] dm_crypt cdc_ether usbnet r8152 mii hid_microsoft ff_nemless mhi_wwan_mbim mhi_wwan_ctrl usbhid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) i915 drm_buddy ttmdmdisplay_helper cec rc_core crctiOdif_pclmul ii drm_kms_helper polyval_clmulni polyval_generic ghash_clmulni_intel sha512_ssse3 aesni_intel syscopyarea sysfillrect hid_generic sysimgblt rtsx_pci_sdmmc name crygrto_sird ihi_pct_germric i2c_hid_acpi drm cryptd psm _lpss_pci e1000e 12c_1001 intel_lpss video rtsx_pci spi_Intel I2c_smbus mhi thunderbolt nvme_core idma64 xhci_pci i2c_hid xhci_pci_renesas nvme_common hid wmi pinctrl_titerbike 
[..359] CR2: 080000005.1103
[..385] ---[ end trace 000000000000000000 ]--- 
[...72] RIP: 0010:queue_work_onAbe2/0x70 
[...43] Code: 90 90 90 90 90 90 90 90 04 1f 44 00 00 55 41 89 fb 49 89 f2 49 89 de 48 89 e5 53 9c 58 0f 1f 40 00 48 89 c3 fa Of 1f 44 00 00 <f0> 49 0f ba 28 OS 79 24 45 31 c9 80 e7 02 74 06 fb 0f 1f 44 O4 44 
[...37] RSP: 0018:ffffac80008a7df0 EFLAGS: 00010002 
[...44] RAX: 600000800.100202 RBX: 0000000000000202 RCX: 0000000000000000 
[.....] RDX: 0000000900000398 RSI: ffffa05c40051000 RDI: 00000000011002000 
[...22] RBP: fffface0006a7df8 R08: 0000000000000398 R09: 0000001~11000 
[...37] RIO: ffffa05c40051000 Ril: 0000004100002000 R12: 0000000000000004 
[...66] R13: 0080000000000000 R14: ffffa6501400c50 R15: ffffa05c44f4c300 
[...98] FS: 08013080000ONIN3(0.00) GS:ffff0070614008(0000) knlGS:0000000000000000 
[...53] CS: 0010 DS: 0000 ES: 0000 CRO: 000000000000050033
[...04] CR2: 0000000000000398 CR3: 0000000110612003 CR4: 0000000000770ef0 
[...74] PKRU: 55555554 
[...42] note: kworker/0:2[202] exited with irqs disabled 

```

There might be errors in that text, it's a picture taken of the screen, run through OCR and manually somewhat cleaned up. That's also why some of the timestamps towards the end are missing, I accidentially cut off the side of the screen in the picture, but I don't suspect that this or the exact register values matter much at this point.

I suspect that the first message about apport-autoreport.service is irrelevant, that also comes up when successfully booting without the dock attached. However, the next message "Unable to change power state from D3hot to DO, device inaccessible" does not come up during a successful boot, and 22.04 also said something about not being able to change the power state/an illegal power state when it failed to boot with the dock attached.

As a side note: Is there any better way to get to such an error message? Is that saved anywhere that's accessible after a reboot?

Thanks a lot in advance!

---

### Post by stevermann on 2023-04-28
Probably, not related, but I have a HDMI selector on my desktop because I use the same HDMI monitor with my Ubuntu computer and my Chromecast.
I spent a couple of days trying to figure out why my Ubuntu PC would never appear on the monitor, then I tried plugging the monitor directly into the computer (An Intel NUC). Ant it boots, no problem.
I tried another HDMI display through the HDMI selector and it works just fine.

So, just for grins, do you have another HDMI display to try?

---

### Post by falka777 on 2023-04-29
Thanks for the tip! Unfortunately, the problem persists whether or not any displays are connected.  However, I have an additional data point: If I disable PCIe tunneling in the BIOS, the system boots without any problems with the dock attached. However, then the network cable connected to the dock does not get passed through to the laptop - I don't have a wired connection then, which is not helpful either :( But this might be a pointer towards where the problem is exactly.

---

