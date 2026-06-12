---
title: "Problem with Intrepid suspend/resume on Compaq SR1750NX"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by davidamcl on 2009-03-21
I am trying to get Ubuntu working well enough that I can use it for the majority of my computer use.  Though this is a desktop unit, it's important to me that I be able to use suspend and resume.

The problem involves one or more of the following symptoms:
1.  Suspend doesn't suspend at all.  After 30 seconds or so, I get brought back to the password screen just as if the screen-saver had kicked in.
2.  Resume works but the wireless connection is dead.  In that case, I can reactivate it by disconnecting and reconnecting my USB wireless adapter (Belkin G+MIMO).
3.  Getting around problem 2 by editing /usr/lib/pm-utils/sleep.d/10NetworkManager:
# Following 4 lines added by DM 2/24/09 to fix wireless sleep problem:
#               /sbin/ifdown wlan0
                /sbin/modprobe -rv rt73usb
                /sbin/modprobe -v rt73usb
#               /sbin/ifup wlan0
These need to be inserted BEFORE resume_nm!  I thought ifdown/ifup should help but they don't seem to make a difference.
This fix works some of the time but then this problem:
4.  Resume hangs while network manager is attempting to reconnect to the wireless router.  (The little balls are spinning around in the notification area.)  If I run top in a terminal window, "events/0" is chewing up nearly all CPU time, and top shows that it's consuming in system mode rather than user mode.  At this point I usually end up using the power switch to reboot.

This is all with a restricted video driver in use (ATI/AMD proprietary FGLRX graphics driver).  It seems to be working fine.  Without it, resume presents a black screen.

I have tried the generic 32-bit distro and the one for AMD64, and the results seem to be the same.  I would prefer to use the latter if possible (have Athlon 64 processor 3500+).

I have tried enabling both backport and proposed updates, and that doesn't seem to make a difference.  Right now I am running kernel 2.6.27-14-generic and GNOME 2.24.1.  Have also tried special network-manager updates.  Here's my current list of active binary sources:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

Aside from this one problem, things seem to work wonderfully -- but I'm about to throw in the towel buy a new system with a preinstalled Unix-based OS (that well-known company in California)...

I'm willing to post snippets from console logs, etc., if that might help.

Thanks in advance for any help!

---

### Post by davidamcl on 2009-03-22
I thought I might as well post part of the system log that demonstrates the problem.  This sequence of messages includes from the time of the SUSPEND command, through the RESUME (which worked except for the network being hung & having high CPU activity), then through the shutdown that didn't succeed fully.  (I didn't write the times down as things were happening, so perhaps I've included a bit more or less.)

After the GUI exited, there were various system messages on the screen in normal character mode except for the fact that the screen was divided into about 10 vertical stripes (black and white) which were flashing on and off.  After the text messages stopped, I had to force the system down with the power switch.

Mar 22 14:43:41 ubuntu kernel: [  689.662329] Freezing user space processes ... (elapsed 0.00 seconds) done.
Mar 22 14:43:41 ubuntu kernel: [  689.663276] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Mar 22 14:43:41 ubuntu kernel: [  689.663332] Suspending console(s) (use no_console_suspend to debug)
Mar 22 14:43:41 ubuntu kernel: [  689.756032] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Mar 22 14:43:41 ubuntu kernel: [  689.772109] sd 0:0:0:0: [sda] Stopping disk
Mar 22 14:43:41 ubuntu kernel: [  690.017275] parport_pc 00:07: disabled
Mar 22 14:43:41 ubuntu kernel: [  690.036076] [fglrx] Power down the ASIC .
Mar 22 14:43:41 ubuntu kernel: [  691.520042] fglrx_pci 0000:01:05.0: PCI INT A disabled
Mar 22 14:43:41 ubuntu kernel: [  691.520285] ATI IXP AC97 controller 0000:00:14.5: PCI INT B disabled
Mar 22 14:43:41 ubuntu kernel: [  691.520488] ehci_hcd 0000:00:13.2: PCI INT A disabled
Mar 22 14:43:41 ubuntu kernel: [  691.536068] ohci_hcd 0000:00:13.1: PCI INT A disabled
Mar 22 14:43:41 ubuntu kernel: [  691.536120] ohci_hcd 0000:00:13.0: PCI INT A disabled
Mar 22 14:43:41 ubuntu kernel: [  691.536412] PM: suspend devices took 1.876 seconds
Mar 22 14:43:41 ubuntu kernel: [  691.536569] ACPI: Preparing to enter system sleep state S3
Mar 22 14:43:41 ubuntu kernel: [  691.536821] Disabling non-boot CPUs ...
Mar 22 14:43:41 ubuntu kernel: [  691.536821] ACPI: Waking up from system sleep state S3
Mar 22 14:43:41 ubuntu kernel: [  691.536821] ACPI: Unable to turn cooling device [f7811b70] 'off'
Mar 22 14:43:41 ubuntu kernel: [  691.536821] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 22 14:43:41 ubuntu kernel: [  691.560017] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 22 14:43:41 ubuntu kernel: [  691.600018] ehci_hcd 0000:00:13.2: enabling device (0000 -> 0002)
Mar 22 14:43:41 ubuntu kernel: [  691.600022] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 22 14:43:41 ubuntu kernel: [  691.601183] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar 22 14:43:41 ubuntu kernel: [  691.604996] fglrx_pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 22 14:43:41 ubuntu kernel: [  691.605081] [fglrx] Power up the ASIC
Mar 22 14:43:41 ubuntu kernel: [  692.320682] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fddfe000-fddfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar 22 14:43:41 ubuntu kernel: [  692.328750] parport_pc 00:07: activated
Mar 22 14:43:41 ubuntu kernel: [  692.357288] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 22 14:43:41 ubuntu kernel: [  692.364492] ata2.00: ACPI cmd ef/03:46:00:00:00:a0 filtered out
Mar 22 14:43:41 ubuntu kernel: [  692.380494] ata2.00: configured for UDMA/100
Mar 22 14:43:41 ubuntu kernel: [  692.542026] sd 0:0:0:0: [sda] Starting disk
Mar 22 14:43:41 ubuntu kernel: [  697.588051] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 22 14:43:41 ubuntu kernel: [  697.596485] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 filtered out
Mar 22 14:43:41 ubuntu kernel: [  697.612492] ata1.00: configured for UDMA/100
Mar 22 14:43:41 ubuntu kernel: [  697.632699] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Mar 22 14:43:41 ubuntu kernel: [  697.632713] sd 0:0:0:0: [sda] Write Protect is off
Mar 22 14:43:41 ubuntu kernel: [  697.632736] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 22 14:43:41 ubuntu kernel: [  698.057335] PM: resume devices took 6.520 seconds
Mar 22 14:43:41 ubuntu kernel: [  698.057341] ------------[ cut here ]------------
Mar 22 14:43:41 ubuntu kernel: [  698.057343] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
Mar 22 14:43:41 ubuntu kernel: [  698.057345] Modules linked in: ipv6 aes_i586 aes_generic af_packet binfmt_misc ppdev powernow_k8 cpufreq_stats cpufreq_userspace cpufreq_ondemand freq_table cpufreq_powersave cpufreq_conservative wmi container video output sbs sbshc pci_slot battery iptable_filter ip_tables x_tables ac sbp2 lp snd_atiixp snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd pcspkr serio_raw k8temp soundcore snd_page_alloc arc4 ecb crypto_blkcipher joydev evdev usblp rt73usb crc_itu_t rt2x00usb rt2x00lib rfkill led_class mac80211 cfg80211 fglrx(P) parport_pc parport button i2c_piix4 i2c_core ati_agp agpgart shpchp pci_hotplug ext3 jbd mbcache loop usb_storage libusual usbhid hid sr_mod cdrom sd_mod crc_t10dif sg 8139cp ohci1394 ieee1394 8139too mii pata_atiixp ohci_hcd sata_sil ehci_hcd pata_acpi ata_generic usbcore libata scsi_mod dock thermal processor fan fbcon tileblit font 
Mar 22 14:43:41 ubuntu kernel: itblit softcursor fuse
Mar 22 14:43:41 ubuntu kernel: [  698.057388] Pid: 6006, comm: pm-suspend Tainted: P          2.6.27-14-generic #1
Mar 22 14:43:41 ubuntu kernel: [  698.057391]  [<c037d836>] ? printk+0x1d/0x1f
Mar 22 14:43:41 ubuntu kernel: [  698.057395]  [<c0131ef9>] warn_on_slowpath+0x59/0x90
Mar 22 14:43:41 ubuntu kernel: [  698.057400]  [<c014d435>] ? sched_clock_cpu+0xd5/0x170
Mar 22 14:43:41 ubuntu kernel: [  698.057404]  [<c014c24f>] ? down_trylock+0x2f/0x40
Mar 22 14:43:41 ubuntu kernel: [  698.057407]  [<c01325d2>] ? try_acquire_console_sem+0x12/0x40
Mar 22 14:43:41 ubuntu kernel: [  698.057410]  [<c024ee30>] ? kobject_put+0x20/0x50
Mar 22 14:43:41 ubuntu kernel: [  698.057413]  [<c015d344>] suspend_test_finish+0x74/0x80
Mar 22 14:43:41 ubuntu kernel: [  698.057416]  [<c015d436>] suspend_devices_and_enter+0xe6/0x190
Mar 22 14:43:41 ubuntu kernel: [  698.057418]  [<c015d6b1>] enter_state+0xd1/0x100
Mar 22 14:43:41 ubuntu kernel: [  698.057421]  [<c015d765>] state_store+0x85/0xd0
Mar 22 14:43:41 ubuntu kernel: [  698.057423]  [<c015d6e0>] ? state_store+0x0/0xd0
Mar 22 14:43:41 ubuntu kernel: [  698.057425]  [<c024ecf4>] kobj_attr_store+0x24/0x30
Mar 22 14:43:41 ubuntu kernel: [  698.057427]  [<c01ffc27>] sysfs_write_file+0x97/0x100
Mar 22 14:43:41 ubuntu kernel: [  698.057430]  [<c01b2870>] vfs_write+0xa0/0x110
Mar 22 14:43:41 ubuntu kernel: [  698.057433]  [<c01ffb90>] ? sysfs_write_file+0x0/0x100
Mar 22 14:43:41 ubuntu kernel: [  698.057436]  [<c01b29b2>] sys_write+0x42/0x70
Mar 22 14:43:41 ubuntu kernel: [  698.057438]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar 22 14:43:41 ubuntu kernel: [  698.057442]  =======================
Mar 22 14:43:41 ubuntu kernel: [  698.057443] ---[ end trace 47269401b444d0d1 ]---
Mar 22 14:43:41 ubuntu kernel: [  698.057581] Restarting tasks ... <6>usb 2-1: USB disconnect, address 2
Mar 22 14:43:41 ubuntu kernel: [  698.388057] done.
Mar 22 14:43:44 ubuntu kernel: [  699.788035] usbcore: deregistering interface driver rt73usb
Mar 22 14:43:44 ubuntu kernel: [  700.402267] Registered led device: rt73usb-phy0:radio
Mar 22 14:43:44 ubuntu kernel: [  700.402462] Registered led device: rt73usb-phy0:assoc
Mar 22 14:43:44 ubuntu kernel: [  700.402635] Registered led device: rt73usb-phy0:quality
Mar 22 14:43:44 ubuntu kernel: [  700.403328] usbcore: registered new interface driver rt73usb
Mar 22 14:43:44 ubuntu kernel: [  700.411616] eth0: link down
Mar 22 14:43:44 ubuntu kernel: [  700.411940] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 22 14:43:48 ubuntu kernel: [  704.504556] firmware: requesting rt73.bin
Mar 22 14:43:49 ubuntu kernel: [  704.671973] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 22 14:43:49 ubuntu kernel: [  704.708059] usb 2-1: new full speed USB device using ohci_hcd and address 4
Mar 22 14:43:56 ubuntu kernel: [  712.099512] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 22 14:43:59 ubuntu kernel: [  714.963956] usb 2-1: configuration #1 chosen from 1 choice
Mar 22 14:52:11 ubuntu kernel: [ 1206.695411] PM: Syncing filesystems ... done.
Mar 22 15:33:31 ubuntu kernel: [ 1206.750656] Freezing user space processes ... (elapsed 0.00 seconds) done.
Mar 22 15:33:31 ubuntu kernel: [ 1206.751575] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Mar 22 15:33:31 ubuntu kernel: [ 1206.751633] Suspending console(s) (use no_console_suspend to debug)
Mar 22 15:33:31 ubuntu kernel: [ 1206.848031] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Mar 22 15:33:31 ubuntu kernel: [ 1206.878874] sd 0:0:0:0: [sda] Stopping disk
Mar 22 15:33:31 ubuntu kernel: [ 1207.529457] parport_pc 00:07: disabled
Mar 22 15:33:31 ubuntu kernel: [ 1207.548075] [fglrx] Power down the ASIC .
Mar 22 15:33:31 ubuntu kernel: [ 1209.028037] fglrx_pci 0000:01:05.0: PCI INT A disabled
Mar 22 15:33:31 ubuntu kernel: [ 1209.028267] ATI IXP AC97 controller 0000:00:14.5: PCI INT B disabled
Mar 22 15:33:31 ubuntu kernel: [ 1209.028467] ehci_hcd 0000:00:13.2: PCI INT A disabled
Mar 22 15:33:31 ubuntu kernel: [ 1209.044067] ohci_hcd 0000:00:13.1: PCI INT A disabled
Mar 22 15:33:31 ubuntu kernel: [ 1209.044118] ohci_hcd 0000:00:13.0: PCI INT A disabled
Mar 22 15:33:31 ubuntu kernel: [ 1209.044407] PM: suspend devices took 2.296 seconds
Mar 22 15:33:31 ubuntu kernel: [ 1209.044555] ACPI: Preparing to enter system sleep state S3
Mar 22 15:33:31 ubuntu kernel: [ 1209.044805] Disabling non-boot CPUs ...
Mar 22 15:33:31 ubuntu kernel: [ 1209.044805] ACPI: Waking up from system sleep state S3
Mar 22 15:33:31 ubuntu kernel: [ 1209.044805] ACPI: Unable to turn cooling device [f7811b70] 'off'
Mar 22 15:33:31 ubuntu kernel: [ 1209.044805] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 22 15:33:31 ubuntu kernel: [ 1209.068018] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 22 15:33:31 ubuntu kernel: [ 1209.108016] ehci_hcd 0000:00:13.2: enabling device (0000 -> 0002)
Mar 22 15:33:31 ubuntu kernel: [ 1209.108020] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 22 15:33:31 ubuntu kernel: [ 1209.109181] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar 22 15:33:31 ubuntu kernel: [ 1209.112994] fglrx_pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 22 15:33:31 ubuntu kernel: [ 1209.113080] [fglrx] Power up the ASIC
Mar 22 15:33:31 ubuntu kernel: [ 1209.828681] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fddfe000-fddfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar 22 15:33:31 ubuntu kernel: [ 1209.836749] parport_pc 00:07: activated
Mar 22 15:33:31 ubuntu kernel: [ 1209.865275] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 22 15:33:31 ubuntu kernel: [ 1209.872495] ata2.00: ACPI cmd ef/03:46:00:00:00:a0 filtered out
Mar 22 15:33:31 ubuntu kernel: [ 1209.888497] ata2.00: configured for UDMA/100
Mar 22 15:33:31 ubuntu kernel: [ 1210.050026] sd 0:0:0:0: [sda] Starting disk
Mar 22 15:33:31 ubuntu kernel: [ 1215.096051] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 22 15:33:31 ubuntu kernel: [ 1215.104487] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 filtered out
Mar 22 15:33:31 ubuntu kernel: [ 1215.120509] ata1.00: configured for UDMA/100
Mar 22 15:33:31 ubuntu kernel: [ 1215.140950] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
Mar 22 15:33:31 ubuntu kernel: [ 1215.140964] sd 0:0:0:0: [sda] Write Protect is off
Mar 22 15:33:31 ubuntu kernel: [ 1215.140987] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 22 15:33:31 ubuntu kernel: [ 1215.565369] PM: resume devices took 6.520 seconds
Mar 22 15:33:31 ubuntu kernel: [ 1215.565374] ------------[ cut here ]------------
Mar 22 15:33:31 ubuntu kernel: [ 1215.565376] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
Mar 22 15:33:31 ubuntu kernel: [ 1215.565378] Modules linked in: rt73usb crc_itu_t rt2x00usb rt2x00lib rfkill led_class mac80211 cfg80211 ipv6 aes_i586 aes_generic af_packet binfmt_misc ppdev powernow_k8 cpufreq_stats cpufreq_userspace cpufreq_ondemand freq_table cpufreq_powersave cpufreq_conservative wmi container video output sbs sbshc pci_slot battery iptable_filter ip_tables x_tables ac sbp2 lp snd_atiixp snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd pcspkr serio_raw k8temp soundcore snd_page_alloc arc4 ecb crypto_blkcipher joydev evdev usblp fglrx(P) parport_pc parport button i2c_piix4 i2c_core ati_agp agpgart shpchp pci_hotplug ext3 jbd mbcache loop usb_storage libusual usbhid hid sr_mod cdrom sd_mod crc_t10dif sg 8139cp ohci1394 ieee1394 8139too mii pata_atiixp ohci_hcd sata_sil ehci_hcd pata_acpi ata_generic usbcore libata scsi_mod dock thermal processor fan fbcon tileblit font 
Mar 22 15:33:31 ubuntu kernel: itblit softcursor fuse [last unloaded: cfg80211]
Mar 22 15:33:31 ubuntu kernel: [ 1215.565421] Pid: 6385, comm: pm-suspend Tainted: P        W 2.6.27-14-generic #1
Mar 22 15:33:31 ubuntu kernel: [ 1215.565424]  [<c037d836>] ? printk+0x1d/0x1f
Mar 22 15:33:31 ubuntu kernel: [ 1215.565428]  [<c0131ef9>] warn_on_slowpath+0x59/0x90
Mar 22 15:33:31 ubuntu kernel: [ 1215.565433]  [<c014d435>] ? sched_clock_cpu+0xd5/0x170
Mar 22 15:33:31 ubuntu kernel: [ 1215.565437]  [<c014c24f>] ? down_trylock+0x2f/0x40
Mar 22 15:33:31 ubuntu kernel: [ 1215.565440]  [<c01325d2>] ? try_acquire_console_sem+0x12/0x40
Mar 22 15:33:31 ubuntu kernel: [ 1215.565443]  [<c024ee30>] ? kobject_put+0x20/0x50
Mar 22 15:33:31 ubuntu kernel: [ 1215.565446]  [<c015d344>] suspend_test_finish+0x74/0x80
Mar 22 15:33:31 ubuntu kernel: [ 1215.565449]  [<c015d436>] suspend_devices_and_enter+0xe6/0x190
Mar 22 15:33:31 ubuntu kernel: [ 1215.565451]  [<c015d6b1>] enter_state+0xd1/0x100
Mar 22 15:33:31 ubuntu kernel: [ 1215.565454]  [<c015d765>] state_store+0x85/0xd0
Mar 22 15:33:31 ubuntu kernel: [ 1215.565456]  [<c015d6e0>] ? state_store+0x0/0xd0
Mar 22 15:33:31 ubuntu kernel: [ 1215.565458]  [<c024ecf4>] kobj_attr_store+0x24/0x30
Mar 22 15:33:31 ubuntu kernel: [ 1215.565461]  [<c01ffc27>] sysfs_write_file+0x97/0x100
Mar 22 15:33:31 ubuntu kernel: [ 1215.565464]  [<c01b2870>] vfs_write+0xa0/0x110
Mar 22 15:33:31 ubuntu kernel: [ 1215.565467]  [<c01ffb90>] ? sysfs_write_file+0x0/0x100
Mar 22 15:33:31 ubuntu kernel: [ 1215.565469]  [<c01b29b2>] sys_write+0x42/0x70
Mar 22 15:33:31 ubuntu kernel: [ 1215.565472]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar 22 15:33:31 ubuntu kernel: [ 1215.565475]  =======================
Mar 22 15:33:31 ubuntu kernel: [ 1215.565477] ---[ end trace 47269401b444d0d1 ]---
Mar 22 15:33:31 ubuntu kernel: [ 1215.565616] Restarting tasks ... <6>usb 2-1: USB disconnect, address 4
Mar 22 15:33:31 ubuntu kernel: [ 1215.755072] done.
Mar 22 15:33:33 ubuntu kernel: [ 1216.630528] usbcore: deregistering interface driver rt73usb
Mar 22 15:33:33 ubuntu kernel: [ 1217.050155] Registered led device: rt73usb-phy0:radio
Mar 22 15:33:33 ubuntu kernel: [ 1217.051008] Registered led device: rt73usb-phy0:assoc
Mar 22 15:33:33 ubuntu kernel: [ 1217.051800] Registered led device: rt73usb-phy0:quality
Mar 22 15:33:33 ubuntu kernel: [ 1217.054620] usbcore: registered new interface driver rt73usb
Mar 22 15:33:33 ubuntu kernel: [ 1217.067475] eth0: link down
Mar 22 15:33:33 ubuntu kernel: [ 1217.068341] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 22 15:33:37 ubuntu kernel: [ 1221.232563] firmware: requesting rt73.bin
Mar 22 15:33:37 ubuntu kernel: [ 1221.330947] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 22 15:33:38 ubuntu kernel: [ 1222.200047] usb 2-1: new full speed USB device using ohci_hcd and address 5
Mar 22 15:33:48 ubuntu kernel: [ 1232.432055] usb 2-1: configuration #1 chosen from 1 choice
Mar 22 15:36:32 ubuntu kernel: [ 1395.868047] NetworkManage D 00000000     0  5109      1
Mar 22 15:36:32 ubuntu kernel: [ 1395.868051]        e82ffca4 00000082 c01bff15 00000000 e82ffc54 ffffffea 00000000 e82fffa0 
Mar 22 15:36:32 ubuntu kernel: [ 1395.868057]        c01c00df e82fffa8 f6ddb240 0009dbd0 00000000 00000001 00000000 00000000 
Mar 22 15:36:32 ubuntu kernel: [ 1395.868062]        c0512080 f786e000 e82fe000 f6ddb4b8 c187bd00 00000000 00100100 c187bd00 
Mar 22 15:36:32 ubuntu kernel: [ 1395.868067] Call Trace:
Mar 22 15:36:32 ubuntu kernel: [ 1395.868069]  [<c01bff15>] ? poll_freewait+0x45/0xb0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868077]  [<c01c00df>] ? do_sys_poll+0x15f/0x1c0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868081]  [<c037ea76>] __mutex_lock_slowpath+0x76/0xb0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868085]  [<c037e88c>] mutex_lock+0x1c/0x20
Mar 22 15:36:32 ubuntu kernel: [ 1395.868088]  [<c02fd2f5>] rtnetlink_rcv+0x15/0x30
Mar 22 15:36:32 ubuntu kernel: [ 1395.868093]  [<c030e625>] netlink_unicast+0x265/0x290
Mar 22 15:36:32 ubuntu kernel: [ 1395.868097]  [<c030f6a3>] netlink_sendmsg+0x1d3/0x2c0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868100]  [<c02e775f>] sock_sendmsg+0xef/0x120
Mar 22 15:36:32 ubuntu kernel: [ 1395.868103]  [<c0234ee5>] ? apparmor_socket_recvmsg+0x15/0x20
Mar 22 15:36:32 ubuntu kernel: [ 1395.868108]  [<c01475c0>] ? autoremove_wake_function+0x0/0x50
Mar 22 15:36:32 ubuntu kernel: [ 1395.868112]  [<c01475c0>] ? autoremove_wake_function+0x0/0x50
Mar 22 15:36:32 ubuntu kernel: [ 1395.868116]  [<c025517a>] ? copy_from_user+0x3a/0x130
Mar 22 15:36:32 ubuntu kernel: [ 1395.868120]  [<c02eedd5>] ? verify_iovec+0x35/0xb0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868124]  [<c02e78a1>] sys_sendmsg+0x111/0x230
Mar 22 15:36:32 ubuntu kernel: [ 1395.868127]  [<c025203d>] ? rb_erase+0xcd/0x150
Mar 22 15:36:32 ubuntu kernel: [ 1395.868130]  [<c01230aa>] ? __dequeue_entity+0x2a/0xb0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868134]  [<c012859b>] ? finish_task_switch+0x2b/0xe0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868137]  [<c037ddc9>] ? schedule+0x429/0x790
Mar 22 15:36:32 ubuntu kernel: [ 1395.868140]  [<c02e808b>] sys_socketcall+0xeb/0x2d0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868143]  [<c02552ab>] ? copy_to_user+0x3b/0x130
Mar 22 15:36:32 ubuntu kernel: [ 1395.868147]  [<c0137080>] ? sys_gettimeofday+0x30/0x70
Mar 22 15:36:32 ubuntu kernel: [ 1395.868150]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar 22 15:36:32 ubuntu kernel: [ 1395.868154]  =======================
Mar 22 15:36:32 ubuntu kernel: [ 1395.868161] wpa_supplican D f6dba5dc     0  5113      1
Mar 22 15:36:32 ubuntu kernel: [ 1395.868164]        e8235cf8 00200082 0000008d f6dba5dc 081764e9 c187bd3c e8235cb8 c0124b8a 
Mar 22 15:36:32 ubuntu kernel: [ 1395.868169]        ffffffff ffffffff e81abed0 00967865 00000000 c0516d00 00000000 e93b7180 
Mar 22 15:36:32 ubuntu kernel: [ 1395.868174]        c0512080 f53fe000 e8234000 e81ac148 c187bd00 00000000 00001e7f c187bd00 
Mar 22 15:36:32 ubuntu kernel: [ 1395.868179] Call Trace:
Mar 22 15:36:32 ubuntu kernel: [ 1395.868180]  [<c0124b8a>] ? enqueue_entity+0xda/0x2f0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868184]  [<c037ea76>] __mutex_lock_slowpath+0x76/0xb0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868187]  [<c037e88c>] mutex_lock+0x1c/0x20
Mar 22 15:36:32 ubuntu kernel: [ 1395.868190]  [<c02fd2f5>] rtnetlink_rcv+0x15/0x30
Mar 22 15:36:32 ubuntu kernel: [ 1395.868193]  [<c030e625>] netlink_unicast+0x265/0x290
Mar 22 15:36:32 ubuntu kernel: [ 1395.868196]  [<c030f6a3>] netlink_sendmsg+0x1d3/0x2c0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868200]  [<c02e775f>] sock_sendmsg+0xef/0x120
Mar 22 15:36:32 ubuntu kernel: [ 1395.868203]  [<c01475c0>] ? autoremove_wake_function+0x0/0x50
Mar 22 15:36:32 ubuntu kernel: [ 1395.868206]  [<c02e612a>] ? sock_aio_write+0xda/0x130
Mar 22 15:36:32 ubuntu kernel: [ 1395.868209]  [<c01b3234>] ? fget_light+0x14/0xc0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868213]  [<c01b208d>] ? do_sync_readv_writev+0xbd/0x100
Mar 22 15:36:32 ubuntu kernel: [ 1395.868217]  [<c02e7ab7>] sys_sendto+0xa7/0xd0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868219]  [<c01230aa>] ? __dequeue_entity+0x2a/0xb0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868222]  [<c0123256>] ? set_next_entity+0x126/0x160
Mar 22 15:36:32 ubuntu kernel: [ 1395.868225]  [<c0102df6>] ? __switch_to+0xa6/0x160
Mar 22 15:36:32 ubuntu kernel: [ 1395.868228]  [<c012859b>] ? finish_task_switch+0x2b/0xe0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868232]  [<c02e7b1b>] sys_send+0x3b/0x40
Mar 22 15:36:32 ubuntu kernel: [ 1395.868235]  [<c02e818e>] sys_socketcall+0x1ee/0x2d0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868238]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar 22 15:36:32 ubuntu kernel: [ 1395.868241]  =======================
Mar 22 15:36:32 ubuntu kernel: [ 1395.868253] multiload-app D ca691e30     0  5664      1
Mar 22 15:36:32 ubuntu kernel: [ 1395.868255]        ca691e5c 00000086 ca691f04 ca691e30 ca691df4 c01bafee 00000246 ca691e1c 
Mar 22 15:36:32 ubuntu kernel: [ 1395.868260]        ca691e44 000000d0 cd993ed0 000ac115 00000000 c014a298 00000000 00000000 
Mar 22 15:36:32 ubuntu kernel: [ 1395.868265]        c0512080 f786e000 ca690000 cd994148 c187bd00 00000000 00000002 c187bd00 
Mar 22 15:36:32 ubuntu kernel: [ 1395.868270] Call Trace:
Mar 22 15:36:32 ubuntu kernel: [ 1395.868271]  [<c01bafee>] ? path_to_nameidata+0x1e/0x50
Mar 22 15:36:32 ubuntu kernel: [ 1395.868275]  [<c014a298>] ? __mutex_init+0x8/0x20
Mar 22 15:36:32 ubuntu kernel: [ 1395.868278]  [<c037ea76>] __mutex_lock_slowpath+0x76/0xb0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868282]  [<c037e88c>] mutex_lock+0x1c/0x20
Mar 22 15:36:32 ubuntu kernel: [ 1395.868284]  [<c02fd2d2>] rtnl_lock+0x12/0x20
Mar 22 15:36:32 ubuntu kernel: [ 1395.868287]  [<c036ab5e>] wext_handle_ioctl+0x4e/0xe0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868291]  [<c0254ae2>] ? strncmp+0x12/0x40
Mar 22 15:36:32 ubuntu kernel: [ 1395.868294]  [<c02f57ff>] dev_ioctl+0x45f/0x520
Mar 22 15:36:32 ubuntu kernel: [ 1395.868297]  [<c0232c84>] ? aa_revalidate_sk+0x14/0xb0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868301]  [<c037fa7d>] ? _spin_lock+0xd/0x10
Mar 22 15:36:32 ubuntu kernel: [ 1395.868304]  [<c02153d8>] ? cap_d_instantiate+0x8/0x10
Mar 22 15:36:32 ubuntu kernel: [ 1395.868308]  [<c0214598>] ? security_d_instantiate+0x18/0x30
Mar 22 15:36:32 ubuntu kernel: [ 1395.868311]  [<c01c60b7>] ? d_instantiate+0x57/0x60
Mar 22 15:36:32 ubuntu kernel: [ 1395.868315]  [<c01b34ca>] ? init_file+0xa/0xa0
Mar 22 15:36:32 ubuntu kernel: [ 1395.868319]  [<c02e5d00>] ? sock_ioctl+0x0/0x250
Mar 22 15:36:32 ubuntu kernel: [ 1395.868321]  [<c02e5df5>] sock_ioctl+0xf5/0x250
Mar 22 15:36:32 ubuntu kernel: [ 1395.868324]  [<c02e5d00>] ? sock_ioctl+0x0/0x250
Mar 22 15:36:32 ubuntu kernel: [ 1395.868327]  [<c01bf28d>] vfs_ioctl+0x2d/0x90
Mar 22 15:36:32 ubuntu kernel: [ 1395.868330]  [<c01bf476>] do_vfs_ioctl+0x66/0x200
Mar 22 15:36:32 ubuntu kernel: [ 1395.868333]  [<c0214f48>] ? cap_file_ioctl+0x8/0x10
Mar 22 15:36:32 ubuntu kernel: [ 1395.868336]  [<c01bf67b>] sys_ioctl+0x6b/0x70
Mar 22 15:36:32 ubuntu kernel: [ 1395.868339]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar 22 15:36:32 ubuntu kernel: [ 1395.868342]  =======================
Mar 22 15:38:45 ubuntu kernel: [ 1529.012043] NetworkManage D 00000000     0  5109      1
Mar 22 15:38:45 ubuntu kernel: [ 1529.012047]        e82ffca4 00000082 c01bff15 00000000 e82ffc54 ffffffea 00000000 e82fffa0 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012052]        c01c00df e82fffa8 f6ddb240 0009dbd0 00000000 00000001 00000000 00000000 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012057]        c0512080 f786e000 e82fe000 f6ddb4b8 c187bd00 00000000 00100100 c187bd00 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012062] Call Trace:
Mar 22 15:38:45 ubuntu kernel: [ 1529.012064]  [<c01bff15>] ? poll_freewait+0x45/0xb0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012071]  [<c01c00df>] ? do_sys_poll+0x15f/0x1c0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012076]  [<c037ea76>] __mutex_lock_slowpath+0x76/0xb0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012080]  [<c037e88c>] mutex_lock+0x1c/0x20
Mar 22 15:38:45 ubuntu kernel: [ 1529.012083]  [<c02fd2f5>] rtnetlink_rcv+0x15/0x30
Mar 22 15:38:45 ubuntu kernel: [ 1529.012087]  [<c030e625>] netlink_unicast+0x265/0x290
Mar 22 15:38:45 ubuntu kernel: [ 1529.012091]  [<c030f6a3>] netlink_sendmsg+0x1d3/0x2c0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012094]  [<c02e775f>] sock_sendmsg+0xef/0x120
Mar 22 15:38:45 ubuntu kernel: [ 1529.012097]  [<c0234ee5>] ? apparmor_socket_recvmsg+0x15/0x20
Mar 22 15:38:45 ubuntu kernel: [ 1529.012102]  [<c01475c0>] ? autoremove_wake_function+0x0/0x50
Mar 22 15:38:45 ubuntu kernel: [ 1529.012106]  [<c01475c0>] ? autoremove_wake_function+0x0/0x50
Mar 22 15:38:45 ubuntu kernel: [ 1529.012109]  [<c025517a>] ? copy_from_user+0x3a/0x130
Mar 22 15:38:45 ubuntu kernel: [ 1529.012113]  [<c02eedd5>] ? verify_iovec+0x35/0xb0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012117]  [<c02e78a1>] sys_sendmsg+0x111/0x230
Mar 22 15:38:45 ubuntu kernel: [ 1529.012120]  [<c025203d>] ? rb_erase+0xcd/0x150
Mar 22 15:38:45 ubuntu kernel: [ 1529.012123]  [<c01230aa>] ? __dequeue_entity+0x2a/0xb0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012127]  [<c012859b>] ? finish_task_switch+0x2b/0xe0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012131]  [<c037ddc9>] ? schedule+0x429/0x790
Mar 22 15:38:45 ubuntu kernel: [ 1529.012134]  [<c02e808b>] sys_socketcall+0xeb/0x2d0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012137]  [<c02552ab>] ? copy_to_user+0x3b/0x130
Mar 22 15:38:45 ubuntu kernel: [ 1529.012140]  [<c0137080>] ? sys_gettimeofday+0x30/0x70
Mar 22 15:38:45 ubuntu kernel: [ 1529.012144]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar 22 15:38:45 ubuntu kernel: [ 1529.012148]  =======================
Mar 22 15:38:45 ubuntu kernel: [ 1529.012155] wpa_supplican D f6dba5dc     0  5113      1
Mar 22 15:38:45 ubuntu kernel: [ 1529.012158]        e8235cf8 00200082 0000008d f6dba5dc 081764e9 c187bd3c e8235cb8 c0124b8a 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012163]        ffffffff ffffffff e81abed0 00967865 00000000 c0516d00 00000000 e93b7180 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012168]        c0512080 f53fe000 e8234000 e81ac148 c187bd00 00000000 00001e7f c187bd00 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012173] Call Trace:
Mar 22 15:38:45 ubuntu kernel: [ 1529.012174]  [<c0124b8a>] ? enqueue_entity+0xda/0x2f0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012178]  [<c037ea76>] __mutex_lock_slowpath+0x76/0xb0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012181]  [<c037e88c>] mutex_lock+0x1c/0x20
Mar 22 15:38:45 ubuntu kernel: [ 1529.012183]  [<c02fd2f5>] rtnetlink_rcv+0x15/0x30
Mar 22 15:38:45 ubuntu kernel: [ 1529.012187]  [<c030e625>] netlink_unicast+0x265/0x290
Mar 22 15:38:45 ubuntu kernel: [ 1529.012190]  [<c030f6a3>] netlink_sendmsg+0x1d3/0x2c0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012193]  [<c02e775f>] sock_sendmsg+0xef/0x120
Mar 22 15:38:45 ubuntu kernel: [ 1529.012196]  [<c01475c0>] ? autoremove_wake_function+0x0/0x50
Mar 22 15:38:45 ubuntu kernel: [ 1529.012200]  [<c02e612a>] ? sock_aio_write+0xda/0x130
Mar 22 15:38:45 ubuntu kernel: [ 1529.012203]  [<c01b3234>] ? fget_light+0x14/0xc0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012207]  [<c01b208d>] ? do_sync_readv_writev+0xbd/0x100
Mar 22 15:38:45 ubuntu kernel: [ 1529.012210]  [<c02e7ab7>] sys_sendto+0xa7/0xd0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012213]  [<c01230aa>] ? __dequeue_entity+0x2a/0xb0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012216]  [<c0123256>] ? set_next_entity+0x126/0x160
Mar 22 15:38:45 ubuntu kernel: [ 1529.012219]  [<c0102df6>] ? __switch_to+0xa6/0x160
Mar 22 15:38:45 ubuntu kernel: [ 1529.012222]  [<c012859b>] ? finish_task_switch+0x2b/0xe0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012226]  [<c02e7b1b>] sys_send+0x3b/0x40
Mar 22 15:38:45 ubuntu kernel: [ 1529.012229]  [<c02e818e>] sys_socketcall+0x1ee/0x2d0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012232]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar 22 15:38:45 ubuntu kernel: [ 1529.012235]  =======================
Mar 22 15:38:45 ubuntu kernel: [ 1529.012247] multiload-app D ca691e30     0  5664      1
Mar 22 15:38:45 ubuntu kernel: [ 1529.012249]        ca691e5c 00000086 ca691f04 ca691e30 ca691df4 c01bafee 00000246 ca691e1c 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012254]        ca691e44 000000d0 cd993ed0 000ac115 00000000 c014a298 00000000 00000000 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012259]        c0512080 f786e000 ca690000 cd994148 c187bd00 00000000 00000002 c187bd00 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012264] Call Trace:
Mar 22 15:38:45 ubuntu kernel: [ 1529.012265]  [<c01bafee>] ? path_to_nameidata+0x1e/0x50
Mar 22 15:38:45 ubuntu kernel: [ 1529.012269]  [<c014a298>] ? __mutex_init+0x8/0x20
Mar 22 15:38:45 ubuntu kernel: [ 1529.012273]  [<c037ea76>] __mutex_lock_slowpath+0x76/0xb0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012276]  [<c037e88c>] mutex_lock+0x1c/0x20
Mar 22 15:38:45 ubuntu kernel: [ 1529.012278]  [<c02fd2d2>] rtnl_lock+0x12/0x20
Mar 22 15:38:45 ubuntu kernel: [ 1529.012282]  [<c036ab5e>] wext_handle_ioctl+0x4e/0xe0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012285]  [<c0254ae2>] ? strncmp+0x12/0x40
Mar 22 15:38:45 ubuntu kernel: [ 1529.012289]  [<c02f57ff>] dev_ioctl+0x45f/0x520
Mar 22 15:38:45 ubuntu kernel: [ 1529.012292]  [<c0232c84>] ? aa_revalidate_sk+0x14/0xb0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012295]  [<c037fa7d>] ? _spin_lock+0xd/0x10
Mar 22 15:38:45 ubuntu kernel: [ 1529.012298]  [<c02153d8>] ? cap_d_instantiate+0x8/0x10
Mar 22 15:38:45 ubuntu kernel: [ 1529.012301]  [<c0214598>] ? security_d_instantiate+0x18/0x30
Mar 22 15:38:45 ubuntu kernel: [ 1529.012305]  [<c01c60b7>] ? d_instantiate+0x57/0x60
Mar 22 15:38:45 ubuntu kernel: [ 1529.012309]  [<c01b34ca>] ? init_file+0xa/0xa0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012312]  [<c02e5d00>] ? sock_ioctl+0x0/0x250
Mar 22 15:38:45 ubuntu kernel: [ 1529.012315]  [<c02e5df5>] sock_ioctl+0xf5/0x250
Mar 22 15:38:45 ubuntu kernel: [ 1529.012318]  [<c02e5d00>] ? sock_ioctl+0x0/0x250
Mar 22 15:38:45 ubuntu kernel: [ 1529.012320]  [<c01bf28d>] vfs_ioctl+0x2d/0x90
Mar 22 15:38:45 ubuntu kernel: [ 1529.012323]  [<c01bf476>] do_vfs_ioctl+0x66/0x200
Mar 22 15:38:45 ubuntu kernel: [ 1529.012326]  [<c0214f48>] ? cap_file_ioctl+0x8/0x10
Mar 22 15:38:45 ubuntu kernel: [ 1529.012330]  [<c01bf67b>] sys_ioctl+0x6b/0x70
Mar 22 15:38:45 ubuntu kernel: [ 1529.012333]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar 22 15:38:45 ubuntu kernel: [ 1529.012336]  =======================
Mar 22 15:38:45 ubuntu kernel: [ 1529.012345] sudo          D f7720338     0  6710   6675
Mar 22 15:38:45 ubuntu kernel: [ 1529.012347]        ebb93d18 00000086 00000013 f7720338 c16b7774 ebb93d54 f7720334 00000013 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012352]        ebb93cc4 c01849ce e5ca1920 002a402d 00000000 ebb93d0c 00000000 00000000 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012357]        c0512080 f786e000 ebb92000 e5ca1b98 c187bd00 00000000 ebb93d04 c187bd00 
Mar 22 15:38:45 ubuntu kernel: [ 1529.012362] Call Trace:
Mar 22 15:38:45 ubuntu kernel: [ 1529.012363]  [<c01849ce>] ? find_lock_page+0x2e/0x70
Mar 22 15:38:45 ubuntu kernel: [ 1529.012368]  [<c01ac9cd>] ? unfreeze_slab+0x7d/0xc0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012372]  [<c037ea76>] __mutex_lock_slowpath+0x76/0xb0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012375]  [<c037e88c>] mutex_lock+0x1c/0x20
Mar 22 15:38:45 ubuntu kernel: [ 1529.012378]  [<c02fd2f5>] rtnetlink_rcv+0x15/0x30
Mar 22 15:38:45 ubuntu kernel: [ 1529.012381]  [<c030e625>] netlink_unicast+0x265/0x290
Mar 22 15:38:45 ubuntu kernel: [ 1529.012384]  [<c030f6a3>] netlink_sendmsg+0x1d3/0x2c0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012388]  [<c02e775f>] sock_sendmsg+0xef/0x120
Mar 22 15:38:45 ubuntu kernel: [ 1529.012391]  [<c01475c0>] ? autoremove_wake_function+0x0/0x50
Mar 22 15:38:45 ubuntu kernel: [ 1529.012394]  [<c01baf85>] ? path_put+0x25/0x30
Mar 22 15:38:45 ubuntu kernel: [ 1529.012397]  [<c014bbb8>] ? up_read+0x8/0x20
Mar 22 15:38:45 ubuntu kernel: [ 1529.012400]  [<c0382122>] ? do_page_fault+0x432/0x760
Mar 22 15:38:45 ubuntu kernel: [ 1529.012404]  [<c01702e4>] ? audit_sockaddr+0x14/0xa0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012407]  [<c025517a>] ? copy_from_user+0x3a/0x130
Mar 22 15:38:45 ubuntu kernel: [ 1529.012411]  [<c02e7ab7>] sys_sendto+0xa7/0xd0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012414]  [<c02e7444>] ? sys_getsockname+0x94/0xa0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012417]  [<c037fa7d>] ? _spin_lock+0xd/0x10
Mar 22 15:38:45 ubuntu kernel: [ 1529.012420]  [<c02153d8>] ? cap_d_instantiate+0x8/0x10
Mar 22 15:38:45 ubuntu kernel: [ 1529.012423]  [<c0214598>] ? security_d_instantiate+0x18/0x30
Mar 22 15:38:45 ubuntu kernel: [ 1529.012426]  [<c01c60b7>] ? d_instantiate+0x57/0x60
Mar 22 15:38:45 ubuntu kernel: [ 1529.012429]  [<c01b34ca>] ? init_file+0xa/0xa0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012432]  [<c02e66b3>] ? sock_attach_fd+0x93/0xd0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012435]  [<c037fa7d>] ? _spin_lock+0xd/0x10
Mar 22 15:38:45 ubuntu kernel: [ 1529.012438]  [<c01b0179>] ? fd_install+0x49/0x60
Mar 22 15:38:45 ubuntu kernel: [ 1529.012441]  [<c02e814c>] sys_socketcall+0x1ac/0x2d0
Mar 22 15:38:45 ubuntu kernel: [ 1529.012445]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Mar 22 15:38:45 ubuntu kernel: [ 1529.012448]  =======================
Mar 22 15:39:30 ubuntu bonobo-activation-server (dave-6768): could not associate with desktop session: Failed to connect to socket /tmp/dbus-2SDuJlbBGL: Connection refused
Mar 22 15:39:31 ubuntu kernel: [ 1575.304113] apm: BIOS not found.
Mar 22 15:39:36 ubuntu kernel: [ 1579.609053] Bluetooth: Core ver 2.13
Mar 22 15:39:36 ubuntu kernel: [ 1579.609465] NET: Registered protocol family 31
Mar 22 15:39:36 ubuntu kernel: [ 1579.609469] Bluetooth: HCI device and connection manager initialized
Mar 22 15:39:36 ubuntu kernel: [ 1579.609472] Bluetooth: HCI socket layer initialized
Mar 22 15:39:36 ubuntu kernel: [ 1579.648096] Bluetooth: L2CAP ver 2.11
Mar 22 15:39:36 ubuntu kernel: [ 1579.648101] Bluetooth: L2CAP socket layer initialized
Mar 22 15:39:36 ubuntu kernel: [ 1579.680037] Bluetooth: RFCOMM socket layer initialized
Mar 22 15:39:36 ubuntu kernel: [ 1579.680245] Bluetooth: RFCOMM TTY layer initialized
Mar 22 15:39:36 ubuntu kernel: [ 1579.680249] Bluetooth: RFCOMM ver 1.10
Mar 22 15:39:40 ubuntu exiting on signal 15

---

### Post by davidamcl on 2009-03-23
One more strange thing:  
If I reboot, suspend and resume seem to work properly the first time after the reboot.  It's the second time that things start to fall apart.

I have done quite a bit of searching the Web and tried a couple of things but nothing has helped so far.

Is it unreasonable to expect suspend and resume to work on a desktop machine with a wireless connection?

---

### Post by davidamcl on 2009-03-27
Problem solved, thanks to this bug record:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274734](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274734)

A good answer (work-around) was apparently posted Oct. 8, 2008.  It does work on my computer with the generic 32-bit OS; I plan to try 64-bit later.

Everything about it makes sense and is consistent with what I have observed.  I have done quite a bit of searching and testing, and I'm a little surprised that it took so long to find a good solution.  It seems like this would be a common problem and should be documented as a known issue.

The problem is related to network processes/drivers, not the video driver.

Thanks to everyone who read this thread and thought about my problem.

---

