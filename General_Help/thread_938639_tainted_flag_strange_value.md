---
title: "tainted flag strange value"
date: 2008-10-05
forum: General Help
---

### Post by Trebaruna on 2008-10-05
When I issue the command ```
cat /proc/sys/kernel/tainted
```I get the result "512". I am not sure who is allowed to set the taint flag, but I'd like to know. Is there any way of finding out who set the flag, and/or who set it to this seemingly odd value? As far as I know, there aren't any nonfree modules in use. Could flashplugin-nonfree be messing with it?

---

### Post by Trebaruna on 2008-10-05
After further examination, it seems the flag is raised from 0 to 512 affter resuming from suspend. There's also a warning in dmesg after suspending: 
```

[  702.608260] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x75/0x80()
[  702.608262] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat ipv6 af_packet binfmt_misc vboxdrv ppdev powernow_k8 cpufreq_stats cpufreq_ondemand freq_table cpufreq_conservative cpufreq_userspace cpufreq_powersave sbs pci_slot wmi container sbshc iptable_filter ip_tables x_tables parport_pc lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq serio_raw uvcvideo snd_timer arc4 snd_seq_device psmouse ecb compat_ioctl32 snd crypto_blkcipher i2c_piix4 videodev soundcore v4l1_compat ath5k snd_page_alloc i2c_core mac80211 led_class cfg80211 video output shpchp pci_hotplug battery ac button evdev ext3 jbd mbcache usb_storage usbhid hid libusual sg sd_mod ata_generic crc_t10dif sr_mod cdrom pata_acpi ohci_hcd ehci_hcd pata_atiixp ahci usbcore libata scsi_mod dock r8169 thermal processor fan fbcon tileblit font bitblit softcursor uvesafb cn fuse
[  702.608303] Pid: 7211, comm: pm-suspend Not tainted 2.6.27-4-generic #1
[  702.608305] 
[  702.608305] Call Trace:
[  702.608311]  [<ffffffff8024e8d4>] warn_on_slowpath+0x64/0x90
[  702.608317]  [<ffffffff80518dd6>] ? printk+0x6c/0x6e
[  702.608322]  [<ffffffff802126a4>] ? mcount_call+0x5/0x31
[  702.608325]  [<ffffffff8027de35>] suspend_test_finish+0x75/0x80
[  702.608327]  [<ffffffff8027df44>] suspend_devices_and_enter+0x104/0x1b0
[  702.608330]  [<ffffffff8027e201>] enter_state+0xe1/0x110
[  702.608332]  [<ffffffff8027e2ea>] state_store+0xba/0x100
[  702.608337]  [<ffffffff803a55e7>] kobj_attr_store+0x17/0x20
[  702.608341]  [<ffffffff8034ae0a>] sysfs_write_file+0xca/0x140
[  702.608345]  [<ffffffff802eb81b>] vfs_write+0xcb/0x130
[  702.608347]  [<ffffffff802eb975>] sys_write+0x55/0x90
[  702.608351]  [<ffffffff8021288a>] system_call_fastpath+0x16/0x1b
[  702.608352] 
[  702.608354] ---[ end trace 274d0ffb5e7e9086 ]---

```According to the mentioned source file (in 2.6.27.rc8 ) this warning is given when suspend/resume takes too long (more than 5 seconds). In this case, resume is taking too long. At this point it is relevant to note I am running intrepid beta. Should this be reported as a bug?

---

