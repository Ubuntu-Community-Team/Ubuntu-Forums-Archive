---
title: "USB Drive Issue."
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by Grelf on 2006-06-04
I've got three USB drives connected to a USB hub on my Dell d600. Everything was working fine for awhile. My setup was as follows for the drives:

250 gig - Storage drive (music/movies/etc...)
250 gig - Darkroom drive (raw camera files/post processed negatives)
80  gig - Backup (ran backups from /home and Darkroom)

Everything automounted fine, and mounted to where it's supposed to go. Two days ago while trying to backup the Darkroom drive, it died mid-backup. It's a brand new (less then 3 weeks) Seagate Barracuda 7200. In a firewire/usb enclosure. Now it won't even mount. When I connect it, I get some seriously ugly errors. I'll post the dmesg output below.

Any help would be greatly appreciated, I've got about a year and a halfs of negatives on this drive, and I'd really like to be able to at least mount it long enough to copy it off, and reformat the drive.

Jonathan

DMESG to follow:


[4295585.266000] usb 4-6.4: new full speed USB device using ehci_hcd and address 8
[4295587.289000] usb 4-6.4: device descriptor read/64, error -32
[4295592.412000] usb 4-6.4: device descriptor read/64, error -32
[4295592.535000] usb 4-6.4: new full speed USB device using ehci_hcd and address 9
[4295593.557000] usb 4-6.4: device descriptor read/64, error -32
[4295598.681000] usb 4-6.4: device descriptor read/64, error -32
[4295598.815000] usb 4-6.4: new full speed USB device using ehci_hcd and address 10
[4295609.226000] usb 4-6.4: device not accepting address 10, error -110
[4295609.248000] usb 4-6.4: new full speed USB device using ehci_hcd and address 11
[4295614.650000] usb 4-6.4: device not accepting address 11, error -32
[4295694.836000] usb 4-6.4: new high speed USB device using ehci_hcd and address 12
[4295694.909000] scsi1 : SCSI emulation for USB Mass Storage devices
[4295694.909000] usb-storage: device found at 12
[4295694.909000] usb-storage: waiting for device to settle before scanning
[4295775.476000] scsi: Device offlined - not ready after error recovery: host 1 channel 0 id 0 lun 0
[4295775.477000] usb 4-6.4: USB disconnect, address 12
[4295775.477000] usb-storage: device scan complete
[4295775.477000] Unable to handle kernel NULL pointer dereference at virtual address 00000048
[4295775.477000]  printing eip:
[4295775.477000] c01748fd
[4295775.477000] *pde = 00000000
[4295775.477000] Oops: 0000 [#1]
[4295775.477000] Modules linked in: vmnet vmmon rfcomm l2cap bluetooth speedstep_centrino cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative pcmcia video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi i2c_acpi_ec i2c_core button battery container ac ipv6 ndiswrapper sd_mod pcspkr rtc usblp yenta_socket rsrc_nonstatic pcmcia_core snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc tpm_atmel tpm_nsc tpm pci_hotplug intel_agp agpgart dm_mod joydev tsdev evdev sr_mod sbp2 ieee1394 psmouse mousedev parport_pc lp parport md ext3 jbd thermal processor fan usbhid usb_storage scsi_mod tg3 ehci_hcd uhci_hcd usbcore ide_cd cdrom ide_disk ide_generic piix ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4295775.477000] CPU:    0
[4295775.477000] EIP:    0060:[<c01748fd>]    Tainted: P      VLI
[4295775.477000] EFLAGS: 00010286   (2.6.12-10-386) 
[4295775.477000] EIP is at sysfs_hash_and_remove+0x8/0xd0
[4295775.477000] eax: 00000000   ebx: f8996f00   ecx: 00000003   edx: cdaa1648
[4295775.477000] esi: cdaa1648   edi: f8996ea0   ebp: df87ddec   esp: c1943e3c
[4295775.477000] ds: 007b   es: 007b   ss: 0068
[4295775.477000] Process khubd (pid: 1914, threadinfo=c1942000 task=dfb77aa0)
[4295775.477000] Stack: f8996f00 cdaa1648 f8996ea0 df87ddec c01ed15d 00000000 c0278565 cdaa1648 
[4295775.477000]        cdaa1590 e1ddc800 c01ed198 cdaa1648 cdaa1400 f8980e62 cdaa1648 e1ddc800 
[4295775.477000]        e8f3ed80 e1ddc7f8 f8980f03 cdaa1400 00000202 e1ddc800 e1ddc804 f89802e7 
[4295775.477000] Call Trace:
[4295775.477000]  [<c01ed15d>] class_device_del+0x62/0x92
[4295775.477000]  [<c01ed198>] class_device_unregister+0xb/0x16
[4295775.477000]  [<f8980e62>] scsi_remove_device+0x32/0x77 [scsi_mod]
[4295775.477000]  [<f8980f03>] __scsi_remove_target+0x5c/0x7f [scsi_mod]
[4295775.477000]  [<f89802e7>] scsi_forget_host+0x28/0x3f [scsi_mod]
[4295775.477000]  [<f8979f86>] scsi_remove_host+0xc/0x57 [scsi_mod]
[4295775.477000]  [<f895327b>] storage_disconnect+0x50/0x6a [usb_storage]
[4295775.477000]  [<f88e709c>] usb_unbind_interface+0x36/0x65 [usbcore]
[4295775.477000]  [<c01ec380>] device_release_driver+0x49/0x55
[4295775.477000]  [<c01ec539>] bus_remove_device+0x48/0x77
[4295775.477000]  [<c01eb924>] device_del+0x43/0x6f
[4295775.477000]  [<f88ec9cb>] usb_disable_device+0x77/0xe9 [usbcore]
[4295775.477000]  [<f88e8b77>] usb_disconnect+0x93/0xec [usbcore]
[4295775.477000]  [<f88e97c6>] hub_port_connect_change+0x57/0x2b2 [usbcore]
[4295775.477000]  [<f88e9c43>] hub_events+0x222/0x2c6 [usbcore]
[4295775.477000]  [<f88e9ce7>] hub_thread+0x0/0xe8 [usbcore]
[4295775.477000]  [<f88e9d03>] hub_thread+0x1c/0xe8 [usbcore]
[4295775.477000]  [<c01247e2>] autoremove_wake_function+0x0/0x3a
[4295775.477000]  [<f88e9ce7>] hub_thread+0x0/0xe8 [usbcore]
[4295775.477000]  [<c01247e2>] autoremove_wake_function+0x0/0x3a
[4295775.477000]  [<c0101245>] kernel_thread_helper+0x5/0xb
[4295775.477000] Code: 89 02 74 03 89 50 04 c7 41 04 00 02 20 00 89 5c 24 10 8b 46 08 89 44 24 0c 5b 5e e9 f7 a3 fe ff 5b 5e c3 55 57 56 53 8b 44 24 14 <8b> 58 48 8b 50 08 ff 4a 70 0f 88 b9 00 00 00 8b 53 0c 8d 6a fc 
[4295775.477000]

---

### Post by Grelf on 2006-06-05
Any ideas? Anyone? :>

---

### Post by secdroid on 2006-06-26
What troubleshooting have you done?  Moved the suspect drive to a different port on the hub?  Moved the drive to a direct USB port on the same computer?  Tested the suspect drive on a different computer (NOT using the hub)?

Simplify.  Divide & conquer.  

You'll get more help if you show results from your troubleshooting.

---

