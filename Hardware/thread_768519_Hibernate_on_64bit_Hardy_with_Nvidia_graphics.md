---
title: "Hibernate on 64bit Hardy with Nvidia graphics"
date: 2008-04-26
forum: Hardware
---

### Post by lamborghiniwang on 2008-04-26
I did a clean installation of Hardy 64bit on my Thinkpad T61p(Nvidia Quadro FX 570M video card), the suspend works out of the box(:)), but the hibernate is still broken. 

Every time after the resuming from hibernate, I can see the login console(not gdm, the command line interface), but couldn't type in anything with my keyboard, and then it will show the following error msg, if I wait long enough the screen will turn into black and all I can do is to reboot the machine with Alt-Ctrl-Delete.

```

Apr 25 18:57:21 Bumble kernel: [   34.801005] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:7281]
Apr 25 18:57:21 Bumble kernel: [   46.605812] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:7281]
Apr 25 18:57:21 Bumble kernel: [   58.406623] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:7281]
Apr 25 18:57:21 Bumble kernel: [   70.211432] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:7281]
Apr 25 18:57:21 Bumble kernel: [   82.016240] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:7281]

```

Any suggestions?
PS: I have 4GB RAM installed, and 6GB of swap partition is available.

---

### Post by berutten on 2008-04-26
Interesting, I have the exact same machine, same OS, and only 4 days out of the box, and I am having very similar problems.  Instead when mine wakes up I just get a solid gray screen.  I can swap to another console and restart GDM, but its highly annoying.

I can't seem to find anything online other than this bug report, which I am not even sure is the exact same problem.

[https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/205547](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/205547)

I have no ideas either, but will start looking into it more.

---

### Post by enchantedsky on 2008-04-26
I've used Ubuntu since 6.06 (64-bit), and now I'm using 8.04 (64-bit) with Nvidia restricted driver graphics........and the hibernation has never worked!

I think it's because of lack of drivers for ACPI, because people who do not get ACPI errors when booting up tend to say their hibernation works. Newer computers have a newer type of motherboard which Linux needs better drivers for.......that's my theory why hibernation does not work for certain people, and won't until there is a driver for everything in your computer.

---

### Post by lamborghiniwang on 2008-04-27
Someone in the [**_Nvidia Forum_**]("http://www.nvnews.net/vbulletin/showthread.php?t=109199&page=2#17") reported that hibernate works with the new 173.08 driver.

---

### Post by enchantedsky on 2008-04-27
> **lamborghiniwang said:**
> Someone in the [**_Nvidia Forum_**]("http://www.nvnews.net/vbulletin/showthread.php?t=109199&page=2#17") reported that hibernate works with the new 173.08 driver.

That's awesome! How do you get the newer Nvidia driver?

Edit: [http://www.nvidia.com/object/linux_display_amd64_173.08.html](http://www.nvidia.com/object/linux_display_amd64_173.08.html)

---

### Post by lamborghiniwang on 2008-06-14
huh..., tried the new Nvidia driver 173.14.05 using EnvyNG, the hibernate is still broken.

---

### Post by dvo on 2008-07-20
For Asus M2NPV-VM, nVidia GeForce 6150, I finally found the solution - hooray :-)
Simply update the BIOS (from revision 0504 to revision 1301) as recommended at
[http://fixunix.com/kernel/337502-swsusp-amd-x2-64-2-6-24-regression.html](http://fixunix.com/kernel/337502-swsusp-amd-x2-64-2-6-24-regression.html)
So the problem was some incompatibility of the newer kernels with the older BIOS revisions. 
This made both suspend to ram and hibernate work.

BTW, I still have problems with pm-utils, therefore I use acpi-support:
In /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
replace /usr/sbin/pm-hibernate $QUIRKS
by /etc/acpi/hibernate.sh force
In /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
replace /usr/sbin/pm-suspend $QUIRKS
by /etc/acpi/sleep.sh force

I use these settings in /etc/defaul/acpi-support:
ACPI_SLEEP=true
ACPI_SLEEP_MODE=mem
SAVE_VBE_STATE=false
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=true
USE_DPMS=false

---

### Post by aquarat on 2008-08-17
Herrro

I've got the same problem... but I can hibernate :) .

I'm running Hardy 64 on a Thinpad T61 (Nvidia Quadro GFX). I have 4GBs of RAM and a swap of 4.2GB.

I changed a few options to do with power management (text file somewhere) based on a tutorial, but can't remember off-hand what I changed.

The point is, the machine hibernates. If I start it up after hibernation it runs through the boot process normally and then begins reading the session from the swap. When it finishes, the screen goes black, a beep is heard... and then after about 20 seconds four lines appear on screen.

In syslog, this appears :

```

Aug 17 13:27:30 thinkrat kernel: [   77.688608] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:12474]
Aug 17 13:27:30 thinkrat kernel: [   77.688610] CPU 1:
Aug 17 13:27:30 thinkrat kernel: [   77.688611] Modules linked in: af_packet isofs udf binfmt_misc rfcomm l2cap vboxdrv ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table container sbs bay sbshc dock ipv6 coretemp uinput sbp2 parport_pc lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep arc4 ecb snd_seq_dummy blkcipher snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia snd_timer thinkpad_acpi snd_seq_device hci_usb snd nvram bluetooth pcspkr evdev yenta_socket rsrc_nonstatic pcmcia_core psmouse serio_raw iTCO_wdt iTCO_vendor_support nvidia(P) soundcore battery i2c_core ac shpchp pci_hotplug video output wmi_acer button intel_agp iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack iptable_mangle iptable_filter ip_tables x_tables reiserfs sr_mod cdrom sg ata_piix sd_mod ata_generic ahci ohci1394 ieee1394 pata_acpi ehci_hcd uhci_hcd libata usbcore scsi_mod thermal processor fan fbcon tileblit 
Aug 17 13:27:30 thinkrat kernel: ont bitblit softcursor fuse
Aug 17 13:27:30 thinkrat kernel: [   77.688665] Pid: 12474, comm: pm-hibernate Tainted: P        2.6.24-19-generic #1
Aug 17 13:27:37 thinkrat kernel: [   77.688666] RIP: 0010:[nvidia:os_io_read_byte+0x3/0x10]  [nvidia:os_io_read_byte+0x3/0x10] :nvidia:os_io_read_byte+0x3/0x10
Aug 17 13:27:37 thinkrat kernel: [   77.688801] RSP: 0018:ffff8100a4259c40  EFLAGS: 00000296
Aug 17 13:27:37 thinkrat kernel: [   77.688803] RAX: 0000000000000078 RBX: ffff810108d4af30 RCX: ffffffff889dfba0
Aug 17 13:27:37 thinkrat kernel: [   77.688804] RDX: 00000000000003d5 RSI: 00000000000003d5 RDI: ffff810135598000
Aug 17 13:27:37 thinkrat kernel: [   77.688806] RBP: 0000000000000001 R08: 0000000000000000 R09: 0000000000000001
Aug 17 13:27:37 thinkrat kernel: [   77.688807] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000001
Aug 17 13:27:37 thinkrat kernel: [   77.688809] R13: 0000000000000000 R14: ffff810108d4af30 R15: 0000000000000000
Aug 17 13:27:37 thinkrat kernel: [   77.688811] FS:  00007f81161f96e0(0000) GS:ffff810137401800(0000) knlGS:0000000000000000
Aug 17 13:27:37 thinkrat kernel: [   77.688812] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 17 13:27:37 thinkrat kernel: [   77.688814] CR2: 0000000000000000 CR3: 00000000a4c5e000 CR4: 00000000000006a0
Aug 17 13:27:37 thinkrat kernel: [   77.688815] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 17 13:27:37 thinkrat kernel: [   77.688817] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 17 13:27:37 thinkrat kernel: [   77.688818] 
Aug 17 13:27:37 thinkrat kernel: [   77.688818] Call Trace:
Aug 17 13:27:37 thinkrat kernel: [   77.688919]  [nvidia:_nv000016rm+0x13/0x1b] :nvidia:_nv000016rm+0x13/0x1b
Aug 17 13:27:37 thinkrat kernel: [   77.689040]  [nvidia:_nv000217rm+0x11/0x26] :nvidia:_nv000217rm+0x11/0x26
Aug 17 13:27:37 thinkrat kernel: [   77.689143]  [nvidia:_nv000310rm+0x83/0xa4] :nvidia:_nv000310rm+0x83/0xa4
Aug 17 13:27:37 thinkrat kernel: [   77.689245]  [nvidia:_nv004714rm+0x1cb/0x214] :nvidia:_nv004714rm+0x1cb/0x214
Aug 17 13:27:37 thinkrat kernel: [   77.689367]  [nvidia:_nv004041rm+0xc7/0x365] :nvidia:_nv004041rm+0xc7/0x365
Aug 17 13:27:37 thinkrat kernel: [   77.689488]  [nvidia:_nv002969rm+0x317/0x5b1] :nvidia:_nv002969rm+0x317/0x5b1
Aug 17 13:27:37 thinkrat kernel: [   77.689606]  [nvidia:_nv002969rm+0x2d3/0x5b1] :nvidia:_nv002969rm+0x2d3/0x5b1
Aug 17 13:27:37 thinkrat kernel: [   77.689727]  [nvidia:_nv003107rm+0x46f/0x702] :nvidia:_nv003107rm+0x46f/0x702
Aug 17 13:27:37 thinkrat kernel: [   77.689847]  [nvidia:_nv002964rm+0x71/0x79] :nvidia:_nv002964rm+0x71/0x79
Aug 17 13:27:37 thinkrat kernel: [   77.689967]  [nvidia:_nv002976rm+0x22e/0x24a] :nvidia:_nv002976rm+0x22e/0x24a
Aug 17 13:27:37 thinkrat kernel: [   77.690088]  [nvidia:rm_power_management+0x1cd/0x269] :nvidia:rm_power_management+0x1cd/0x269
Aug 17 13:27:37 thinkrat kernel: [   77.690189]  [nvidia:nv_power_management+0x164/0x200] :nvidia:nv_power_management+0x164/0x200
Aug 17 13:27:38 thinkrat kernel: [   77.690198]  [dpm_resume+0x6a/0x1a0] dpm_resume+0x6a/0x1a0
Aug 17 13:27:38 thinkrat kernel: [   77.690202]  [device_resume+0x1a/0x30] device_resume+0x1a/0x30
Aug 17 13:27:38 thinkrat kernel: [   77.690207]  [hibernation_snapshot+0x9d/0x120] hibernation_snapshot+0x9d/0x120
Aug 17 13:27:38 thinkrat kernel: [   77.690211]  [hibernate+0xe8/0x1e0] hibernate+0xe8/0x1e0
Aug 17 13:27:38 thinkrat kernel: [   77.690216]  [state_store+0xe0/0xf0] state_store+0xe0/0xf0
Aug 17 13:27:38 thinkrat kernel: [   77.690223]  [sysfs_write_file+0xfe/0x160] sysfs_write_file+0xfe/0x160
Aug 17 13:27:38 thinkrat kernel: [   77.690232]  [vfs_write+0xed/0x190] vfs_write+0xed/0x190
Aug 17 13:27:38 thinkrat kernel: [   77.690237]  [sys_write+0x53/0x90] sys_write+0x53/0x90
Aug 17 13:27:38 thinkrat kernel: [   77.690244]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug 17 13:27:38 thinkrat kernel: [   77.690255] 
Aug 17 13:27:38 thinkrat kernel: [   89.493969] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:12474]
Aug 17 13:27:38 thinkrat kernel: [   89.493970] CPU 1:
Aug 17 13:27:38 thinkrat kernel: [   89.493971] Modules linked in: af_packet isofs udf binfmt_misc rfcomm l2cap vboxdrv ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table container sbs bay sbshc dock ipv6 coretemp uinput sbp2 parport_pc lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep arc4 ecb snd_seq_dummy blkcipher snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia snd_timer thinkpad_acpi snd_seq_device hci_usb snd nvram bluetooth pcspkr evdev yenta_socket rsrc_nonstatic pcmcia_core psmouse serio_raw iTCO_wdt iTCO_vendor_support nvidia(P) soundcore battery i2c_core ac shpchp pci_hotplug video output wmi_acer button intel_agp iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack iptable_mangle iptable_filter ip_tables x_tables reiserfs sr_mod cdrom sg ata_piix sd_mod ata_generic ahci ohci1394 ieee1394 pata_acpi ehci_hcd uhci_hcd libata usbcore scsi_mod thermal processor fan fbcon tileblit 
Aug 17 13:27:38 thinkrat kernel: ont bitblit softcursor fuse
Aug 17 13:27:38 thinkrat kernel: [   89.494009] Pid: 12474, comm: pm-hibernate Tainted: P        2.6.24-19-generic #1
Aug 17 13:27:38 thinkrat kernel: [   89.494010] RIP: 0010:[nvidia:os_io_read_byte+0x3/0x10]  [nvidia:os_io_read_byte+0x3/0x10] :nvidia:os_io_read_byte+0x3/0x10
Aug 17 13:27:38 thinkrat kernel: [   89.494108] RSP: 0018:ffff8100a4259c40  EFLAGS: 00000296
Aug 17 13:27:38 thinkrat kernel: [   89.494110] RAX: 0000000000000033 RBX: ffff810108d4af30 RCX: ffffffff889dfba0
Aug 17 13:27:38 thinkrat kernel: [   89.494111] RDX: 00000000000003d5 RSI: 00000000000003d5 RDI: ffff810135598000
Aug 17 13:27:38 thinkrat kernel: [   89.494113] RBP: 0000000000000000 R08: 0000000000000000 R09: 0000000000000001
Aug 17 13:27:38 thinkrat kernel: [   89.494114] R10: 0000000000000001 R11: 0000000000000000 R12: ffff810108d4af20
Aug 17 13:27:38 thinkrat kernel: [   89.494116] R13: 0000000000000001 R14: 0000000000000001 R15: 0000000000000000
Aug 17 13:27:38 thinkrat kernel: [   89.494117] FS:  00007f81161f96e0(0000) GS:ffff810137401800(0000) knlGS:0000000000000000
Aug 17 13:27:38 thinkrat kernel: [   89.494119] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 17 13:27:38 thinkrat kernel: [   89.494120] CR2: 0000000000000000 CR3: 00000000a4c5e000 CR4: 00000000000006a0
Aug 17 13:27:38 thinkrat kernel: [   89.494122] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 17 13:27:38 thinkrat kernel: [   89.494123] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 17 13:27:38 thinkrat kernel: [   89.494124] 
Aug 17 13:27:38 thinkrat kernel: [   89.494125] Call Trace:
Aug 17 13:27:38 thinkrat kernel: [   89.494225]  [nvidia:_nv000016rm+0x13/0x1b] :nvidia:_nv000016rm+0x13/0x1b
Aug 17 13:27:38 thinkrat kernel: [   89.494344]  [nvidia:_nv000217rm+0x11/0x26] :nvidia:_nv000217rm+0x11/0x26
Aug 17 13:27:38 thinkrat kernel: [   89.494447]  [nvidia:_nv000310rm+0x83/0xa4] :nvidia:_nv000310rm+0x83/0xa4
Aug 17 13:27:38 thinkrat kernel: [   89.494548]  [nvidia:_nv004714rm+0x1cb/0x214] :nvidia:_nv004714rm+0x1cb/0x214
Aug 17 13:27:38 thinkrat kernel: [   89.494670]  [nvidia:_nv004041rm+0xc7/0x365] :nvidia:_nv004041rm+0xc7/0x365
Aug 17 13:27:38 thinkrat kernel: [   89.494790]  [nvidia:_nv002969rm+0x317/0x5b1] :nvidia:_nv002969rm+0x317/0x5b1
Aug 17 13:27:38 thinkrat kernel: [   89.494909]  [nvidia:_nv002969rm+0x2d3/0x5b1] :nvidia:_nv002969rm+0x2d3/0x5b1
Aug 17 13:27:38 thinkrat kernel: [   89.495029]  [nvidia:_nv003107rm+0x46f/0x702] :nvidia:_nv003107rm+0x46f/0x702
Aug 17 13:27:38 thinkrat kernel: [   89.495150]  [nvidia:_nv002964rm+0x71/0x79] :nvidia:_nv002964rm+0x71/0x79
Aug 17 13:27:38 thinkrat kernel: [   89.495269]  [nvidia:_nv002976rm+0x22e/0x24a] :nvidia:_nv002976rm+0x22e/0x24a
Aug 17 13:27:38 thinkrat kernel: [   89.495390]  [nvidia:rm_power_management+0x1cd/0x269] :nvidia:rm_power_management+0x1cd/0x269
Aug 17 13:27:38 thinkrat kernel: [   89.495491]  [nvidia:nv_power_management+0x164/0x200] :nvidia:nv_power_management+0x164/0x200
Aug 17 13:27:38 thinkrat kernel: [   89.495498]  [dpm_resume+0x6a/0x1a0] dpm_resume+0x6a/0x1a0
Aug 17 13:27:38 thinkrat kernel: [   89.495502]  [device_resume+0x1a/0x30] device_resume+0x1a/0x30
Aug 17 13:27:38 thinkrat kernel: [   89.495505]  [hibernation_snapshot+0x9d/0x120] hibernation_snapshot+0x9d/0x120
Aug 17 13:27:38 thinkrat kernel: [   89.495509]  [hibernate+0xe8/0x1e0] hibernate+0xe8/0x1e0
Aug 17 13:27:38 thinkrat kernel: [   89.495513]  [state_store+0xe0/0xf0] state_store+0xe0/0xf0
Aug 17 13:27:38 thinkrat kernel: [   89.495520]  [sysfs_write_file+0xfe/0x160] sysfs_write_file+0xfe/0x160
Aug 17 13:27:38 thinkrat kernel: [   89.495528]  [vfs_write+0xed/0x190] vfs_write+0xed/0x190
Aug 17 13:27:38 thinkrat kernel: [   89.495533]  [sys_write+0x53/0x90] sys_write+0x53/0x90
Aug 17 13:27:38 thinkrat kernel: [   89.495539]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug 17 13:27:38 thinkrat kernel: [   89.495549] 
Aug 17 13:27:38 thinkrat kernel: [  101.295332] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:12474]
Aug 17 13:27:38 thinkrat kernel: [  101.295333] CPU 1:
Aug 17 13:27:38 thinkrat kernel: [  101.295334] Modules linked in: af_packet isofs udf binfmt_misc rfcomm l2cap vboxdrv ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table container sbs bay sbshc dock ipv6 coretemp uinput sbp2 parport_pc lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep arc4 ecb snd_seq_dummy blkcipher snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia snd_timer thinkpad_acpi snd_seq_device hci_usb snd nvram bluetooth pcspkr evdev yenta_socket rsrc_nonstatic pcmcia_core psmouse serio_raw iTCO_wdt iTCO_vendor_support nvidia(P) soundcore battery i2c_core ac shpchp pci_hotplug video output wmi_acer button intel_agp iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack iptable_mangle iptable_filter ip_tables x_tables reiserfs sr_mod cdrom sg ata_piix sd_mod ata_generic ahci ohci1394 ieee1394 pata_acpi ehci_hcd uhci_hcd libata usbcore scsi_mod thermal processor fan fbcon tileblit 
Aug 17 13:27:38 thinkrat kernel: ont bitblit softcursor fuse
Aug 17 13:27:38 thinkrat kernel: [  101.295371] Pid: 12474, comm: pm-hibernate Tainted: P        2.6.24-19-generic #1
Aug 17 13:27:38 thinkrat kernel: [  101.295372] RIP: 0010:[nvidia:os_io_read_byte+0x3/0x10]  [nvidia:os_io_read_byte+0x3/0x10] :nvidia:os_io_read_byte+0x3/0x10
Aug 17 13:27:38 thinkrat kernel: [  101.295470] RSP: 0018:ffff8100a4259c40  EFLAGS: 00000296
Aug 17 13:27:38 thinkrat kernel: [  101.295471] RAX: 0000000000000066 RBX: ffff810108d4af30 RCX: ffffffff889dfba0
Aug 17 13:27:38 thinkrat kernel: [  101.295473] RDX: 00000000000003d5 RSI: 00000000000003d5 RDI: ffff810135598000
Aug 17 13:27:38 thinkrat kernel: [  101.295474] RBP: 0000000000000000 R08: 0000000000000000 R09: 0000000000000001
Aug 17 13:27:38 thinkrat kernel: [  101.295476] R10: 0000000000000001 R11: 0000000000000000 R12: ffff810108d4af20
Aug 17 13:27:38 thinkrat kernel: [  101.295477] R13: 0000000000000001 R14: 0000000000000001 R15: 0000000000000000
Aug 17 13:27:38 thinkrat kernel: [  101.295479] FS:  00007f81161f96e0(0000) GS:ffff810137401800(0000) knlGS:0000000000000000
Aug 17 13:27:38 thinkrat kernel: [  101.295481] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 17 13:27:38 thinkrat kernel: [  101.295482] CR2: 0000000000000000 CR3: 00000000a4c5e000 CR4: 00000000000006a0
Aug 17 13:27:38 thinkrat kernel: [  101.295484] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 17 13:27:38 thinkrat kernel: [  101.295485] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 17 13:27:38 thinkrat kernel: [  101.295487] 
Aug 17 13:27:38 thinkrat kernel: [  101.295487] Call Trace:
Aug 17 13:27:38 thinkrat kernel: [  101.295587]  [nvidia:_nv000016rm+0x13/0x1b] :nvidia:_nv000016rm+0x13/0x1b
Aug 17 13:27:38 thinkrat kernel: [  101.295707]  [nvidia:_nv000217rm+0x11/0x26] :nvidia:_nv000217rm+0x11/0x26
Aug 17 13:27:38 thinkrat kernel: [  101.295810]  [nvidia:_nv000310rm+0x83/0xa4] :nvidia:_nv000310rm+0x83/0xa4
Aug 17 13:27:38 thinkrat kernel: [  101.295911]  [nvidia:_nv004714rm+0x1cb/0x214] :nvidia:_nv004714rm+0x1cb/0x214
Aug 17 13:27:38 thinkrat kernel: [  101.296032]  [nvidia:_nv004041rm+0xc7/0x365] :nvidia:_nv004041rm+0xc7/0x365
Aug 17 13:27:38 thinkrat kernel: [  101.296153]  [nvidia:_nv002969rm+0x317/0x5b1] :nvidia:_nv002969rm+0x317/0x5b1
Aug 17 13:27:38 thinkrat kernel: [  101.296271]  [nvidia:_nv002969rm+0x2d3/0x5b1] :nvidia:_nv002969rm+0x2d3/0x5b1
Aug 17 13:27:38 thinkrat kernel: [  101.296392]  [nvidia:_nv003107rm+0x46f/0x702] :nvidia:_nv003107rm+0x46f/0x702
Aug 17 13:27:38 thinkrat kernel: [  101.296513]  [nvidia:_nv002964rm+0x71/0x79] :nvidia:_nv002964rm+0x71/0x79
Aug 17 13:27:38 thinkrat kernel: [  101.296632]  [nvidia:_nv002976rm+0x22e/0x24a] :nvidia:_nv002976rm+0x22e/0x24a
Aug 17 13:27:38 thinkrat kernel: [  101.296753]  [nvidia:rm_power_management+0x1cd/0x269] :nvidia:rm_power_management+0x1cd/0x269
Aug 17 13:27:38 thinkrat kernel: [  101.296854]  [nvidia:nv_power_management+0x164/0x200] :nvidia:nv_power_management+0x164/0x200
Aug 17 13:27:38 thinkrat kernel: [  101.296860]  [dpm_resume+0x6a/0x1a0] dpm_resume+0x6a/0x1a0
Aug 17 13:27:38 thinkrat kernel: [  101.296864]  [device_resume+0x1a/0x30] device_resume+0x1a/0x30
Aug 17 13:27:38 thinkrat kernel: [  101.296868]  [hibernation_snapshot+0x9d/0x120] hibernation_snapshot+0x9d/0x120
Aug 17 13:27:38 thinkrat kernel: [  101.296872]  [hibernate+0xe8/0x1e0] hibernate+0xe8/0x1e0
Aug 17 13:27:38 thinkrat kernel: [  101.296876]  [state_store+0xe0/0xf0] state_store+0xe0/0xf0
Aug 17 13:27:38 thinkrat kernel: [  101.296883]  [sysfs_write_file+0xfe/0x160] sysfs_write_file+0xfe/0x160
Aug 17 13:27:38 thinkrat kernel: [  101.296891]  [vfs_write+0xed/0x190] vfs_write+0xed/0x190
Aug 17 13:27:38 thinkrat kernel: [  101.296896]  [sys_write+0x53/0x90] sys_write+0x53/0x90
Aug 17 13:27:38 thinkrat kernel: [  101.296902]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug 17 13:27:38 thinkrat kernel: [  101.296912] 
Aug 17 13:27:38 thinkrat kernel: [  113.100691] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:12474]
Aug 17 13:27:38 thinkrat kernel: [  113.100693] CPU 1:
Aug 17 13:27:38 thinkrat kernel: [  113.100694] Modules linked in: af_packet isofs udf binfmt_misc rfcomm l2cap vboxdrv ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table container sbs bay sbshc dock ipv6 coretemp uinput sbp2 parport_pc lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep arc4 ecb snd_seq_dummy blkcipher snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia snd_timer thinkpad_acpi snd_seq_device hci_usb snd nvram bluetooth pcspkr evdev yenta_socket rsrc_nonstatic pcmcia_core psmouse serio_raw iTCO_wdt iTCO_vendor_support nvidia(P) soundcore battery i2c_core ac shpchp pci_hotplug video output wmi_acer button intel_agp iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack iptable_mangle iptable_filter ip_tables x_tables reiserfs sr_mod cdrom sg ata_piix sd_mod ata_generic ahci ohci1394 ieee1394 pata_acpi ehci_hcd uhci_hcd libata usbcore scsi_mod thermal processor fan fbcon tileblit 
Aug 17 13:27:38 thinkrat kernel: ont bitblit softcursor fuse
Aug 17 13:27:38 thinkrat kernel: [  113.100730] Pid: 12474, comm: pm-hibernate Tainted: P        2.6.24-19-generic #1
Aug 17 13:27:38 thinkrat kernel: [  113.100731] RIP: 0010:[nvidia:os_io_read_byte+0x3/0x10]  [nvidia:os_io_read_byte+0x3/0x10] :nvidia:os_io_read_byte+0x3/0x10
Aug 17 13:27:38 thinkrat kernel: [  113.100828] RSP: 0018:ffff8100a4259c40  EFLAGS: 00000296
Aug 17 13:27:38 thinkrat kernel: [  113.100830] RAX: 0000000000000094 RBX: ffff810108d4af30 RCX: ffffffff889dfba0
Aug 17 13:27:38 thinkrat kernel: [  113.100831] RDX: 00000000000003d5 RSI: 00000000000003d5 RDI: ffff810135598000
Aug 17 13:27:38 thinkrat kernel: [  113.100833] RBP: 0000000000000000 R08: 0000000000000000 R09: 0000000000000001
Aug 17 13:27:38 thinkrat kernel: [  113.100834] R10: 0000000000000001 R11: 0000000000000000 R12: ffff810108d4af30
Aug 17 13:27:38 thinkrat kernel: [  113.100836] R13: 0000000000000001 R14: 0000000000000001 R15: 0000000000000000
Aug 17 13:27:38 thinkrat kernel: [  113.100838] FS:  00007f81161f96e0(0000) GS:ffff810137401800(0000) knlGS:0000000000000000
Aug 17 13:27:38 thinkrat kernel: [  113.100839] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 17 13:27:38 thinkrat kernel: [  113.100841] CR2: 0000000000000000 CR3: 00000000a4c5e000 CR4: 00000000000006a0
Aug 17 13:27:38 thinkrat kernel: [  113.100842] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 17 13:27:38 thinkrat kernel: [  113.100844] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 17 13:27:38 thinkrat kernel: [  113.100845] 
Aug 17 13:27:38 thinkrat kernel: [  113.100845] Call Trace:
Aug 17 13:27:38 thinkrat kernel: [  113.100945]  [nvidia:_nv000016rm+0x13/0x1b] :nvidia:_nv000016rm+0x13/0x1b
Aug 17 13:27:38 thinkrat kernel: [  113.101065]  [nvidia:_nv000217rm+0x11/0x26] :nvidia:_nv000217rm+0x11/0x26
Aug 17 13:27:38 thinkrat kernel: [  113.101167]  [nvidia:_nv000310rm+0x83/0xa4] :nvidia:_nv000310rm+0x83/0xa4
Aug 17 13:27:38 thinkrat kernel: [  113.101268]  [nvidia:_nv004714rm+0x1cb/0x214] :nvidia:_nv004714rm+0x1cb/0x214
Aug 17 13:27:38 thinkrat kernel: [  113.101390]  [nvidia:_nv004041rm+0xc7/0x365] :nvidia:_nv004041rm+0xc7/0x365
Aug 17 13:27:38 thinkrat kernel: [  113.101510]  [nvidia:_nv002969rm+0x317/0x5b1] :nvidia:_nv002969rm+0x317/0x5b1
Aug 17 13:27:38 thinkrat kernel: [  113.101629]  [nvidia:_nv002969rm+0x2d3/0x5b1] :nvidia:_nv002969rm+0x2d3/0x5b1
Aug 17 13:27:38 thinkrat kernel: [  113.101749]  [nvidia:_nv003107rm+0x46f/0x702] :nvidia:_nv003107rm+0x46f/0x702
Aug 17 13:27:38 thinkrat kernel: [  113.101870]  [nvidia:_nv002964rm+0x71/0x79] :nvidia:_nv002964rm+0x71/0x79
Aug 17 13:27:38 thinkrat kernel: [  113.101989]  [nvidia:_nv002976rm+0x22e/0x24a] :nvidia:_nv002976rm+0x22e/0x24a
Aug 17 13:27:38 thinkrat kernel: [  113.102110]  [nvidia:rm_power_management+0x1cd/0x269] :nvidia:rm_power_management+0x1cd/0x269
Aug 17 13:27:38 thinkrat kernel: [  113.102211]  [nvidia:nv_power_management+0x164/0x200] :nvidia:nv_power_management+0x164/0x200
Aug 17 13:27:38 thinkrat kernel: [  113.102218]  [dpm_resume+0x6a/0x1a0] dpm_resume+0x6a/0x1a0
Aug 17 13:27:38 thinkrat kernel: [  113.102222]  [device_resume+0x1a/0x30] device_resume+0x1a/0x30
Aug 17 13:27:38 thinkrat kernel: [  113.102225]  [hibernation_snapshot+0x9d/0x120] hibernation_snapshot+0x9d/0x120
Aug 17 13:27:38 thinkrat kernel: [  113.102229]  [hibernate+0xe8/0x1e0] hibernate+0xe8/0x1e0
Aug 17 13:27:38 thinkrat kernel: [  113.102234]  [state_store+0xe0/0xf0] state_store+0xe0/0xf0
Aug 17 13:27:38 thinkrat kernel: [  113.102240]  [sysfs_write_file+0xfe/0x160] sysfs_write_file+0xfe/0x160
Aug 17 13:27:38 thinkrat kernel: [  113.102248]  [vfs_write+0xed/0x190] vfs_write+0xed/0x190
Aug 17 13:27:38 thinkrat kernel: [  113.102253]  [sys_write+0x53/0x90] sys_write+0x53/0x90
Aug 17 13:27:38 thinkrat kernel: [  113.102259]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug 17 13:27:38 thinkrat kernel: [  113.102270] 
Aug 17 13:27:38 thinkrat kernel: [  124.902055] BUG: soft lockup - CPU#1 stuck for 11s! [pm-hibernate:12474]
Aug 17 13:27:38 thinkrat kernel: [  124.902057] CPU 1:
Aug 17 13:27:38 thinkrat kernel: [  124.902057] Modules linked in: af_packet isofs udf binfmt_misc rfcomm l2cap vboxdrv ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table container sbs bay sbshc dock ipv6 coretemp uinput sbp2 parport_pc lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep arc4 ecb snd_seq_dummy blkcipher snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia snd_timer thinkpad_acpi snd_seq_device hci_usb snd nvram bluetooth pcspkr evdev yenta_socket rsrc_nonstatic pcmcia_core psmouse serio_raw iTCO_wdt iTCO_vendor_support nvidia(P) soundcore battery i2c_core ac shpchp pci_hotplug video output wmi_acer button intel_agp iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack iptable_mangle iptable_filter ip_tables x_tables reiserfs sr_mod cdrom sg ata_piix sd_mod ata_generic ahci ohci1394 ieee1394 pata_acpi ehci_hcd uhci_hcd libata usbcore scsi_mod thermal processor fan fbcon tileblit 
Aug 17 13:27:38 thinkrat kernel: ont bitblit softcursor fuse
Aug 17 13:27:38 thinkrat kernel: [  124.902094] Pid: 12474, comm: pm-hibernate Tainted: P        2.6.24-19-generic #1
Aug 17 13:27:38 thinkrat kernel: [  124.902095] RIP: 0010:[nvidia:os_io_read_byte+0x3/0x10]  [nvidia:os_io_read_byte+0x3/0x10] :nvidia:os_io_read_byte+0x3/0x10
Aug 17 13:27:38 thinkrat kernel: [  124.902192] RSP: 0018:ffff8100a4259c40  EFLAGS: 00000296
Aug 17 13:27:38 thinkrat kernel: [  124.902193] RAX: 000000000000005a RBX: ffff810108d4af30 RCX: ffffffff889dfba0
Aug 17 13:27:38 thinkrat kernel: [  124.902195] RDX: 00000000000003d5 RSI: 00000000000003d5 RDI: ffff810135598000
Aug 17 13:27:38 thinkrat kernel: [  124.902196] RBP: 0000000000000001 R08: 0000000000000000 R09: 0000000000000001
Aug 17 13:27:38 thinkrat kernel: [  124.902198] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000001
Aug 17 13:27:38 thinkrat kernel: [  124.902199] R13: 0000000000000000 R14: ffff810108d4af30 R15: 0000000000000000
Aug 17 13:27:38 thinkrat kernel: [  124.902201] FS:  00007f81161f96e0(0000) GS:ffff810137401800(0000) knlGS:0000000000000000
Aug 17 13:27:38 thinkrat kernel: [  124.902203] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 17 13:27:38 thinkrat kernel: [  124.902204] CR2: 0000000000000000 CR3: 00000000a4c5e000 CR4: 00000000000006a0
Aug 17 13:27:38 thinkrat kernel: [  124.902206] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 17 13:27:38 thinkrat kernel: [  124.902207] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 17 13:27:38 thinkrat kernel: [  124.902208] 
Aug 17 13:27:38 thinkrat kernel: [  124.902209] Call Trace:
Aug 17 13:27:38 thinkrat kernel: [  124.902309]  [nvidia:_nv000016rm+0x13/0x1b] :nvidia:_nv000016rm+0x13/0x1b
Aug 17 13:27:38 thinkrat kernel: [  124.902428]  [nvidia:_nv000217rm+0x11/0x26] :nvidia:_nv000217rm+0x11/0x26
Aug 17 13:27:38 thinkrat kernel: [  124.902531]  [nvidia:_nv000310rm+0x83/0xa4] :nvidia:_nv000310rm+0x83/0xa4
Aug 17 13:27:38 thinkrat kernel: [  124.902632]  [nvidia:_nv004714rm+0x1cb/0x214] :nvidia:_nv004714rm+0x1cb/0x214
Aug 17 13:27:38 thinkrat kernel: [  124.902753]  [nvidia:_nv004041rm+0xc7/0x365] :nvidia:_nv004041rm+0xc7/0x365
Aug 17 13:27:38 thinkrat kernel: [  124.902874]  [nvidia:_nv002969rm+0x317/0x5b1] :nvidia:_nv002969rm+0x317/0x5b1
Aug 17 13:27:38 thinkrat kernel: [  124.902992]  [nvidia:_nv002969rm+0x2d3/0x5b1] :nvidia:_nv002969rm+0x2d3/0x5b1
Aug 17 13:27:38 thinkrat kernel: [  124.903113]  [nvidia:_nv003107rm+0x46f/0x702] :nvidia:_nv003107rm+0x46f/0x702
Aug 17 13:27:38 thinkrat kernel: [  124.903234]  [nvidia:_nv002964rm+0x71/0x79] :nvidia:_nv002964rm+0x71/0x79
Aug 17 13:27:38 thinkrat kernel: [  124.903353]  [nvidia:_nv002976rm+0x22e/0x24a] :nvidia:_nv002976rm+0x22e/0x24a
Aug 17 13:27:38 thinkrat kernel: [  124.903474]  [nvidia:rm_power_management+0x1cd/0x269] :nvidia:rm_power_management+0x1cd/0x269
Aug 17 13:27:38 thinkrat kernel: [  124.903575]  [nvidia:nv_power_management+0x164/0x200] :nvidia:nv_power_management+0x164/0x200
Aug 17 13:27:38 thinkrat kernel: [  124.903581]  [dpm_resume+0x6a/0x1a0] dpm_resume+0x6a/0x1a0
Aug 17 13:27:38 thinkrat kernel: [  124.903585]  [device_resume+0x1a/0x30] device_resume+0x1a/0x30
Aug 17 13:27:38 thinkrat kernel: [  124.903589]  [hibernation_snapshot+0x9d/0x120] hibernation_snapshot+0x9d/0x120
Aug 17 13:27:38 thinkrat kernel: [  124.903593]  [hibernate+0xe8/0x1e0] hibernate+0xe8/0x1e0
Aug 17 13:27:38 thinkrat kernel: [  124.903597]  [state_store+0xe0/0xf0] state_store+0xe0/0xf0
Aug 17 13:27:38 thinkrat kernel: [  124.903604]  [sysfs_write_file+0xfe/0x160] sysfs_write_file+0xfe/0x160
Aug 17 13:27:38 thinkrat kernel: [  124.903612]  [vfs_write+0xed/0x190] vfs_write+0xed/0x190
Aug 17 13:27:38 thinkrat kernel: [  124.903617]  [sys_write+0x53/0x90] sys_write+0x53/0x90
Aug 17 13:27:38 thinkrat kernel: [  124.903623]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug 17 13:27:38 thinkrat kernel: [  124.903633] 
Aug 17 13:27:38 thinkrat kernel: [  131.012754] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 40100106, writing 100102)
Aug 17 13:27:38 thinkrat kernel: [  131.012844] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Aug 17 13:27:38 thinkrat kernel: [  131.012874] PM: Writing back config space on device 0000:15:00.0 at offset f (was 780010a, writing 580010a)
Aug 17 13:27:38 thinkrat kernel: [  131.012916] PM: Writing back config space on device 0000:15:00.0 at offset 3 (was 822000, writing 82a800)
Aug 17 13:27:38 thinkrat kernel: [  131.026663] PM: Writing back config space on device 0000:15:00.1 at offset 4 (was 0, writing f8101000)
Aug 17 13:27:38 thinkrat kernel: [  131.026670] PM: Writing back config space on device 0000:15:00.1 at offset 3 (was 800000, writing 802000)
Aug 17 13:27:38 thinkrat kernel: [  131.026682] PM: Writing back config space on device 0000:15:00.1 at offset 1 (was 2100000, writing 2100006)
Aug 17 13:27:38 thinkrat kernel: [  131.079723] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Aug 17 13:27:38 thinkrat kernel: [  132.005911] sd 0:0:0:0: [sda] Starting disk
Aug 17 13:27:38 thinkrat kernel: [  132.708992] PM: Image restored successfully.
Aug 17 13:27:38 thinkrat kernel: [  132.786561] Restarting tasks ... <6>usb 1-2: USB disconnect, address 4
Aug 17 13:27:38 thinkrat kernel: [  132.788647] done.
Aug 17 13:27:38 thinkrat kernel: [  132.788674] swsusp: Basic memory bitmaps freed

```

It recovers though... yay... it hibernates :D

oh! One of the options I changed was "PLATFORM = true" or someting like that. In Vista, the sleep LED (moon shape) flashes during hibernate, before I set the platform option in Ubuntu, the moon LED didn't flash, now it does. I would guess the moon LED indicates that the hibernate is being handled more by hardware than software? ...

---

### Post by aquarat on 2008-08-17
The file I changed : /etc/default/acpi-support
(minus comments)
```

ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES="iwl4965 iwlwifi_mac80211 cfg80211"
MODULES_WHITELIST=""
SAVE_VBE_STATE=false
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=false
USE_DPMS=true
HIBERNATE_MODE=platform
LOCK_SCREEN=true
STOP_SERVICES=""
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=false
SPINDOWN_TIME=12

```

---

