---
title: "USB hdd/dvd issues"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by beefsprocket on 2005-11-08
Can anyone make out what is going on here? I'm trying to connect my 80gb Seagate Barracuda or my LG CD/DVD burner to my laptop through a Genesys ide to usb converter. I've heard that with laptops there can be power issues with this brand of adapter, but my 40gb Barracuda drive mounts and powers up just fine (with ext3 partitions vs fat32 on the 80gb). I am using the power adapter that the converter comes with.
```
[4296200.617000] usb 4-2: new high speed USB device using ehci_hcd and address 4[4296200.696000] scsi1 : SCSI emulation for USB Mass Storage devices
[4296200.698000] usb-storage: device found at 4
[4296200.698000] usb-storage: waiting for device to settle before scanning
[4296281.402000] scsi: Device offlined - not ready after error recovery: host 1 channel 0 id 0 lun 0
[4296281.402000] usb 4-2: USB disconnect, address 4
[4296281.403000] usb-storage: device scan complete
[4296281.403000] Unable to handle kernel NULL pointer dereference at virtual address 00000048
[4296281.403000]  printing eip:
[4296281.403000] c018f936
[4296281.403000] *pde = 00000000
[4296281.403000] Oops: 0000 [#1]
[4296281.403000] Modules linked in: hfs hfsplus nls_cp437 ntfs vfat fat isofs nls_utf8 udf ext3 jbd mbcache vmnet vmmon binfmt_misc fglrx speedstep_centrino cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table pcmcia ipv6 tc1100_wmi video battery container i2c_acpi_ec i2c_core button pcc_acpi sony_acpi ac dev_acpi asus_acpi hotkey af_packet pcspkr rtc ipw2200 firmware_class ieee80211 ieee80211_crypt ohci1394 yenta_socket rsrc_nonstatic pcmcia_core snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc tpm_nsc tpm_atmel tpm shpchp pci_hotplug intel_agp agpgart dm_mod tsdev joydev evdev sr_mod sbp2 ieee1394 psmouse mousedev parport_pc lp parport sd_mod md reiserfs thermal processor fan usb_storage scsi_mod usbhid tg3 ehci_hcd uhci_hcd usbcore ide_cd cdrom ide_disk ide_generic piix ide_core unix fbcon tileblit font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect softcursor capability commoncap
[4296281.403000] CPU:    0
[4296281.403000] EIP:    0060:[<c018f936>]    Tainted: P      VLI
[4296281.403000] EFLAGS: 00010292   (2.6.12-9-686)
[4296281.403000] EIP is at sysfs_hash_and_remove+0xb/0xe3
[4296281.403000] eax: 00000000   ebx: c195b250   ecx: c195b190   edx: c195b248
[4296281.403000] esi: c195b248   edi: f895ca00   ebp: f895c9a0   esp: c193bdec
[4296281.403000] ds: 007b   es: 007b   ss: 0068
[4296281.403000] Process khubd (pid: 1848, threadinfo=c193a000 task=dfb44060)
[4296281.403000] Stack: 00000282 00000001 c195b250 c195b248 f895ca00 f895c9a0 c02124a9 00000000
[4296281.403000]        c02ac3da c195b248 c195b190 df86f000 df86a5e4 c02124e5 c195b248 c195b000
[4296281.403000]        f8946028 c195b248 00000003 df86eff8 df86f000 c18f4dc0 f894610d c195b000
[4296281.403000] Call Trace:
[4296281.403000]  [<c02124a9>] class_device_del+0xac/0xd8
[4296281.403000]  [<c02124e5>] class_device_unregister+0x10/0x1d
[4296281.403000]  [<f8946028>] scsi_remove_device+0x46/0xbb [scsi_mod]
[4296281.403000]  [<f894610d>] __scsi_remove_target+0x70/0x8a [scsi_mod]
[4296281.403000]  [<f8945057>] scsi_forget_host+0x2b/0x46 [scsi_mod]
[4296281.403000]  [<f893d2e5>] scsi_remove_host+0x17/0x73 [scsi_mod]
[4296281.403000]  [<f8961a24>] storage_disconnect+0x5a/0x78 [usb_storage]
[4296281.403000]  [<f88d50fe>] usb_unbind_interface+0x78/0x7a [usbcore]
[4296281.403000]  [<c021103c>] device_release_driver+0x77/0x79
[4296281.403000]  [<c02112bc>] bus_remove_device+0x79/0xba
[4296281.403000]  [<c0210282>] device_del+0x57/0x99
[4296281.403000]  [<f88dc43e>] usb_disable_device+0x8f/0x102 [usbcore]
[4296281.403000]  [<f88d734e>] usb_disconnect+0xb4/0x140 [usbcore]
[4296281.403000]  [<f88d869e>] hub_port_connect_change+0x2dd/0x3ad [usbcore]
[4296281.403000]  [<f88d7776>] hub_port_status+0x23/0x89 [usbcore]
[4296281.403000]  [<f88d893c>] hub_events+0x1ce/0x3b5 [usbcore]
[4296281.403000]  [<f88d8b5a>] hub_thread+0x37/0x10b [usbcore]
[4296281.403000]  [<c012aed9>] autoremove_wake_function+0x0/0x57
[4296281.403000]  [<c0102d5a>] ret_from_fork+0x6/0x14
[4296281.403000]  [<c012aed9>] autoremove_wake_function+0x0/0x57
[4296281.403000]  [<f88d8b23>] hub_thread+0x0/0x10b [usbcore]
[4296281.403000]  [<c01012d9>] kernel_thread_helper+0x5/0xb
[4296281.403000] Code: 04 00 02 20 00 89 5c 24 18 8b 46 08 8b 5c 24 08 8b 74 24 0c 89 44 24 14 83 c4 10 e9 fa 51 fe ff 55 57 56 53 83 ec 08 8b 44 24 1c <8b> 48 48 8b 50 08 ff 4a 70 0f 88 c9 00 00 00 8b 51 0c 8d 6a fc
[4296281.403000]

```

---

### Post by weissed on 2006-05-01
I have the same problem with a HDD and a IDE2USB adapter.
Did you manage to find a solution to the problem?

---

