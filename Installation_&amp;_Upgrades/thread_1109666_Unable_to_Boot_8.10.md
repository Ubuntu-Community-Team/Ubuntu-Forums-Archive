---
title: "Unable to Boot 8.10"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by Sebelas on 2009-03-29
Hi to all, I'm new to Ubuntu.

I've been trying to install 8.10 over the past few days and it has been a thorough exercise in frustration.

None of the installer/boot options - live CD, typical, alternate, recovery - worked. It always hangs/crashes at seemingly random points during boot. Once, it ended up at the command line, and I was able to see a lot of segmentation faults, OOPS and traces in kern.log. Once, I was able to log in at the GUI but it hung immediately after that. In contrast, live CD ran flawlessly on my company notebook PC.

My PC uses an Enlight 865GVSFA P4 mobo with 1GB of RAM. It runs Windoze XP SP2 without any problems.

Please advise. Thanks.

---

### Post by cariboo on 2009-03-29
Have you verified that the CD was burned OK using the verify cd function in the menu?

Jim

---

### Post by Sebelas on 2009-03-30
CD was verified by both burner software and Ubuntu installer.

---

### Post by Sebelas on 2009-04-02
OK, I found some time to further troubleshoot the problem. I also figured out how to capture the system messages.

It appears that there are 2 causes of the crashes:

My system does not like my ATI video card. Even if I disable the on-board video thru BIOS so as to avoid any conflict, it still crashes. Physically removing the card and using the on-board video got me past this problem. However, this is just a workaround and isn't very useful as the on-board video doesn't have DVI output.

Messages related to ATI video card crash:

```

[   14.077079] Linux agpgart interface v0.103
[   14.225891] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   14.255366] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[   14.481941] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.518812] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   14.530829] intel_rng: FWH not detected
[   14.635372] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.711479] iTCO_vendor_support: vendor-support=0
[   14.719028] BUG: unable to handle kernel paging request at ff4f8fed
[   14.720316] IP: [<c038302e>] iret_exc+0x6ee/0x95a
[   14.720316] *pde = 0000f067 *pte = 3784f001 
[   14.720316] Oops: 0003 [#1] SMP 
[   14.720316] Modules linked in: iTCO_vendor_support shpchp pci_hotplug intel_agp agpgart ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg ata_piix ata_generic 8139too pata_acpi ohci1394 libata 8139cp mii uhci_hcd ieee1394 ehci_hcd scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   14.720316] 
[   14.720316] Pid: 2389, comm: udevd Not tainted (2.6.27-7-generic #1)
[   14.720316] EIP: 0060:[<c038302e>] EFLAGS: 00010246 CPU: 0
[   14.720316] EIP is at iret_exc+0x6ee/0x95a
[   14.720316] EAX: 00000000 EBX: 0000000f ECX: 0000000f EDX: f797b00f
[   14.720316] ESI: f797b000 EDI: ff4f8fed EBP: f7961f30 ESP: f7961f1c
[   14.720316]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[   14.720316] Process udevd (pid: 2389, ti=f7960000 task=f744d7f0 task.ti=f7960000)
[   14.720316] Stack: 0000000c 0000000f 0000000f bfffffed c183f928 f7961f68 c01b6b93 f789da00 
[   14.720316]        00000000 c183f928 ff4f8000 bffff000 00000fed 0000000f f789dab4 f797b000 
[   14.720316]        f7960000 c0000000 f797b000 f7961f78 c01b6c19 08ab21f4 00000080 f7961f9c 
[   14.720316] Call Trace:
[   14.720316]  [<c01b6b93>] ? copy_strings+0x133/0x190
[   14.720316]  [<c01b6c19>] ? copy_strings_kernel+0x29/0x40
[   14.720316]  [<c01b80b8>] ? do_execve+0x218/0x2c0
[   14.720316]  [<c0102353>] ? sys_execve+0x43/0x70
[   14.720316]  [<c0103f7b>] ? sysenter_do_call+0x12/0x2f
[   14.720316]  [<c0370000>] ? default_device_exit+0x70/0xb0
[   14.720316]  =======================
[   14.720316] Code: f3 aa 58 59 e9 62 17 ed ff 01 c1 e9 b9 17 ed ff 8d 0c 88 e9 b1 17 ed ff 8d 0c 88 e9 5b 18 ed ff 01 c1 eb 03 8d 0c 88 51 50 31 c0 <f3> aa 58 59 e9 bb 18 ed ff 8d 0c 88 51 50 31 c0 f3 aa 58 59 e9 
[   14.720316] EIP: [<c038302e>] iret_exc+0x6ee/0x95a SS:ESP 0068:f7961f1c
[   14.720316] ---[ end trace e2dff7978aab329b ]---
[   14.925469] BUG: unable to handle kernel paging request at ff4ecfed
[   14.928012] IP: [<c038302e>] iret_exc+0x6ee/0x95a
[   14.928012] *pde = 0000f067 *pte = 3784f001 
[   14.928012] Oops: 0003 [#2] SMP 
[   14.928012] Modules linked in: iTCO_vendor_support shpchp pci_hotplug intel_agp agpgart ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg ata_piix ata_generic 8139too pata_acpi ohci1394 libata 8139cp mii uhci_hcd ieee1394 ehci_hcd scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   14.928012] 
[   14.928012] Pid: 2392, comm: udevd Tainted: G      D   (2.6.27-7-generic #1)
[   14.928012] EIP: 0060:[<c038302e>] EFLAGS: 00010246 CPU: 0
[   14.928012] EIP is at iret_exc+0x6ee/0x95a
[   14.928012] EAX: 00000000 EBX: 0000000f ECX: 0000000f EDX: f797d00f
[   14.928012] ESI: f797d000 EDI: ff4ecfed EBP: f7913f30 ESP: f7913f1c
[   14.928012]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[   14.928012] Process udevd (pid: 2392, ti=f7912000 task=f6a8b240 task.ti=f7912000)
[   14.928012] Stack: 0000000c 0000000f 0000000f bfffffed c188cc8c f7913f68 c01b6b93 f6a67000 
[   14.928012]        00000000 c188cc8c ff4ec000 bffff000 00000fed 0000000f f6a670b4 f797d000 
[   14.928012]        f7912000 c0000000 f797d000 f7913f78 c01b6c19 08aad698 00000080 f7913f9c 
[   14.928012] Call Trace:
[   14.928012]  [<c01b6b93>] ? copy_strings+0x133/0x190
[   14.928012]  [<c01b6c19>] ? copy_strings_kernel+0x29/0x40
[   14.928012]  [<c01b80b8>] ? do_execve+0x218/0x2c0
[   14.928012]  [<c0102353>] ? sys_execve+0x43/0x70
[   14.928012]  [<c0103f7b>] ? sysenter_do_call+0x12/0x2f
[   14.928012]  [<c0370000>] ? default_device_exit+0x70/0xb0
[   14.928012]  =======================
[   14.928012] Code: f3 aa 58 59 e9 62 17 ed ff 01 c1 e9 b9 17 ed ff 8d 0c 88 e9 b1 17 ed ff 8d 0c 88 e9 5b 18 ed ff 01 c1 eb 03 8d 0c 88 51 50 31 c0 <f3> aa 58 59 e9 bb 18 ed ff 8d 0c 88 51 50 31 c0 f3 aa 58 59 e9 
[   14.928012] EIP: [<c038302e>] iret_exc+0x6ee/0x95a SS:ESP 0068:f7913f1c
[   14.928012] ---[ end trace e2dff7978aab329b ]---

```

My system also does not like my D-Link DWL-G520+ wireless card. Replacing it with an SMC card got me past this problem. However, my system reports that the link speed is only 9Mb/s when it should be 54Mb/s.

Messages related to D-Link wireless card crash:

```

[   16.898601] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   16.905216] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   17.143787] acx_pci 0000:01:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.151028] acx: found ACX111-based wireless network card at 0000:01:0b.0, irq:19, phymem1:0xFDEFA000, phymem2:0xFDEC0000, mem1:0xf89d4000, mem1_size:8192, mem2:0xf8b40000, mem2_size:131072
[   17.456478] acx: loading firmware for acx1111 chipset with radio ID 16
[   17.463159] firmware: requesting acx/1.2.1.34/tiacx111c16
[   22.892510] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
[   22.898935] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[   22.907018] AntennaID:00 Len:02 Data:01 02 
[   22.911502] PowerLevelID:01 Len:02 Data:001E 000A 
[   22.917485] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[   22.923062] DomainID:03 Len:06 Data:30 20 30 31 32 40 
[   22.928692] ProductID:04 Len:09 Data:TI ACX100
[   22.933252] ManufacturerID:05 Len:07 Data:TI Test
[   22.996030] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[   23.011923] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.27-7-generic
.
.
.
 * Checking battery state...
[  130.052931] BUG: unable to handle kernel NULL pointer dereference at 00000029
[  130.056008] IP: [<f8a41ca4>] :acx:acx_l_process_authen+0x124/0x380
[  130.056008] Oops: 0000 [#1] SMP 
[  130.056008] Modules linked in: af_packet i915 drm binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev speedstep_lib cpufreq_powersave cpufreq_userspace cpufreq_stats cpufreq_conservative cpufreq_ondemand freq_table wmi video output pci_slot sbs sbshc container battery iptable_filter ip_tables x_tables ac sbp2 lp loop ipv6 snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm evdev snd_seq_dummy psmouse serio_raw snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device pcspkr snd soundcore snd_page_alloc parport_pc parport acx iTCO_wdt iTCO_vendor_support button shpchp pci_hotplug intel_agp agpgart ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg ata_piix ata_generic 8139too pata_acpi libata ohci1394 8139cp mii uhci_hcd ehci_hcd ieee1394 scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  130.056008] 
[  130.056008] Pid: 5018, comm: NetworkManager Not tainted (2.6.27-7-generic #1)
[  130.056008] EIP: 0060:[<f8a41ca4>] EFLAGS: 00010002 CPU: 0
[  130.056008] EIP is at acx_l_process_authen+0x124/0x380 [acx]
[  130.056008] EAX: 00000000 EBX: f7950480 ECX: 00000006 EDX: 00000000
[  130.056008] ESI: 00000029 EDI: f7af24ee EBP: f4625e68 ESP: f4625e28
[  130.056008]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[  130.056008] Process NetworkManager (pid: 5018, ti=f4624000 task=f45b9920 task.ti=f4624000)
[  130.056008] Stack: f4625e78 f4625e3c c01bac2e f72b6c38 00025e64 f7af24ee f4625e90 f795074c 
[  130.056008]        f7af24e4 00000000 f494c900 00000000 00000000 f4625e90 00000029 f4625ea8 
[  130.056008]        f4625ed4 f8a426d1 c18e8180 c18e8180 c18e46a4 c18e46a0 f7af24d8 f7950480 
[  130.056008] Call Trace:
[  130.056008]  [<c01bac2e>] ? path_to_nameidata+0x1e/0x50
[  130.056008]  [<f8a426d1>] ? acx_l_process_mgmt_frame+0x361/0x5d0 [acx]
[  130.056008]  [<f8a4299e>] ? acx_l_rx_ieee802_11_frame+0x5e/0x290 [acx]
[  130.056008]  [<c012a571>] ? hrtick_start_fair+0x181/0x1a0
[  130.056008]  [<c0102df6>] ? __switch_to+0xa6/0x160
[  130.056008]  [<f8a42c0b>] ? acx_l_process_rxbuf+0x3b/0x90 [acx]
[  130.056008]  [<f8a44f4b>] ? acxpci_i_interrupt+0x20b/0x320 [acx]
[  130.056008]  [<c037c989>] ? schedule+0x429/0x790
[  130.056008]  [<c01770b1>] ? handle_IRQ_event+0x41/0x80
[  130.056008]  [<c0178954>] ? handle_fasteoi_irq+0x74/0xe0
[  130.056008]  [<c0106c15>] ? do_IRQ+0x45/0x80
[  130.056008]  [<c0105003>] ? common_interrupt+0x23/0x30
[  130.056008]  =======================
[  130.056008] Code: ff ff 31 d2 e9 38 ff ff ff 8d b6 00 00 00 00 8b 93 f4 1f 00 00 b9 06 00 00 00 8b 7d e0 89 d6 83 c7 0a 83 c6 29 89 55 e4 89 7d d4 <f3> a6 74 99 8b 43 14 c7 04 24 10 9d a4 f8 89 44 24 04 e8 1e a7 
[  130.056008] EIP: [<f8a41ca4>] acx_l_process_authen+0x124/0x380 [acx] SS:ESP 0068:f4625e28
[  130.056008] Kernel panic - not syncing: Fatal exception in interrupt

```

If the developers are interested in spending time in examining the above problems, I'd be happy to spend time working with them.

Dennis

---

### Post by klafilin on 2009-04-02
Hi Sebelas, I had the same Problem. My solution was: Install
UBUNTU 8.04LTS with all updates and also install the proprietarDriver for the ATI Video Card. ( It will show up
automaticly next to your Download-Manager Icon) After that upgrade
with your Download-Manager to UBUNTU 8.10.
Works perfect for me.

---

### Post by Sebelas on 2009-04-06
klafilin, thanks for the advice, but I decided to grit my teeth and try to resolve the problems w/o falling back to 8.04, which I managed to do after a lot of reading.

Apparently, it isn't always enough to just disable the on-board video thru BIOS. I had to blacklist intel_agp. After that, my system booted, drm and radeon loaded, and the desktop came up nicely.

As for my D-Link DWL-G520+ wireless card, acx crashed when NetworkManager tried to interact with it. Configuring the card manually in /etc/network/interfaces kept NetworkManager out of the way. Wireless works now.

---

