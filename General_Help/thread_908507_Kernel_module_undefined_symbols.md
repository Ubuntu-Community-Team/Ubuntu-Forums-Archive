---
title: "Kernel module undefined symbols"
date: 2008-09-02
forum: General Help
---

### Post by n7lyg on 2008-09-02
I have had a long-standing kernel module built against many different versions of Linux.  It has always worked just fine until now.  I am now running Ubuntu 8.04 and the module has started failing.  I first noticed this when calls to iget() started failing.  I noticed that iget is going away in the future, so I thought that I should prepare.  I replaced the call to iget(0 with iget_locked() and some other code.  However, I still get undefined symbols.  Here is what it says:

Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313169] ivdrfs-DEBUG [INODE:udfsai_iget:193] : Calling iget_locked()...
Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313214] Modules linked in: udf i915 drm udfsai(P) af_packet rfcomm l2cap bluetooth nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs ppdev ipv6 acpi_cpufreq cpufreq_ondemand cpufreq_userspace cpufreq_stats cpufreq_powersave freq_table cpufreq_conservative container dock sbs sbshc battery iptable_filter ip_tables x_tables ac sbp2 lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device intel_agp usb_storage snd serio_raw libusual parport_pc agpgart wmi_acer tpm_infineon tpm psmouse pcspkr evdev video output e1000e button iTCO_wdt iTCO_vendor_support tpm_bios shpchp pci_hotplug parport soundcore ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi ata_generic usbhid hid ohci1394 ieee1394 ata_piix floppy libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313265] 
Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313268] Pid: 6672, comm: mount Tainted: P        (2.6.24-19-generic #1)
Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313270] EIP: 0060:[__slab_alloc+0x276/0x4a0] EFLAGS: 00210086 CPU: 0
Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313275] EIP is at __slab_alloc+0x276/0x4a0
Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313276] EAX: 00000000 EBX: ee708000 ECX: 00000000 EDX: c15ce100
Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313278] ESI: ee708000 EDI: 00000000 EBP: f7185600 ESP: ee973cdc
Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313280]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Sep  2 11:46:19 josephk-desktop kernel: [ 1605.313585] ---[ end trace 5db2867375af514d ]---

I do not know how to interpret this error.  My module is udfsai, which appears to be linked in correctly, except for the proprietary nature.

How do I debug this error?

Thanks in advance for any help.

/Joe

---

