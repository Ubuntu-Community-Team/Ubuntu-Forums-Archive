---
title: "Wireless suddenly lost"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by eexpress on 2007-10-10
suddenly, wireless device lost all signal. I use wicd now, and NetworkManager also like this. **It seems from the last update of kernel version**.  

&#9679;  dmesg |tail -n 60
[   24.800000] ReiserFS: sda2: checking transaction log (sda2)
[   24.868000] ReiserFS: sda2: Using r5 hash to sort names
[   25.160000] **ipw3945**: Detected geography ABG (13 802.11bg channels, 4 802.11a channels)
[   26.008000] **Asus Laptop** ACPI Extras version 0.30
[   26.008000]   unsupported model A8J, trying default values
[   26.008000]   send /proc/acpi/dsdt to the developers
[   26.028000] ACPI: AC Adapter [AC0] (on-line)
[   26.108000] ACPI: Battery Slot [BAT0] (battery present)
[   26.140000] input: Power Button (FF) as /class/input/input5
[   26.140000] ACPI: Power Button (FF) [PWRF]
[   26.140000] input: Lid Switch as /class/input/input6
[   26.140000] ACPI: Lid Switch [LID]
[   26.140000] input: Power Button (CM) as /class/input/input7
[   26.140000] ACPI: Power Button (CM) [PWRB]
[   26.140000] input: Sleep Button (CM) as /class/input/input8
[   26.140000] ACPI: Sleep Button (CM) [SLPB]
[   26.168000] Using specific hotkey driver
[   26.264000] No dock devices found.
[   26.312000] ibm_acpi: ec object not found
[   26.428000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   26.456000] pcc_acpi: loading...
[   26.544000] NET: Registered protocol family 17
[   31.952000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   31.952000] vboxdrv: Successfully done.
[   32.920000] ppdev: user-space parallel port driver
[   37.296000] r8169: eth0: link down
[29030.296000] **NVRM**: Xid (0001:00): 13, 0000 01013900 00000039 00000328 00000000 00000080
[29034.352000] NVRM: Xid (0001:00): 13, 0000 01013900 00000039 00000328 00000000 00000080
[29240.948000] NVRM: Xid (0001:00): 13, 0000 01013900 00000039 00000328 00000000 00000080
[29244.948000] **ipw3945: Microcode SW error detected.  Restarting.**
[29244.948000] ipw3945: request scan called when driver not ready.
[29245.452000] ipw3945: Error sending ADD_STA: time out after 500ms.
[29245.452000] ipw3945: Can't stop Rx DMA.
[29245.464000] ------------[ cut here ]------------
[29245.464000] **kernel BUG** at kernel/workqueue.c:323!
[29245.464000] invalid opcode: 0000 [#1]
[29245.464000] SMP 
[29245.464000] Modules linked in: binfmt_misc ppdev vboxdrv af_packet tc1100_wmi pcc_acpi dev_acpi sony_acpi video sbs i2c_ec dock acpi_cpufreq button battery container cpufreq_userspace ac cpufreq_stats asus_acpi backlight cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative nls_iso8859_1 nls_cp437 vfat fat reiserfs fuse sbp2 parport_pc lp parport snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss joydev snd_seq_midi snd_rawmidi gspca snd_seq_midi_event videodev v4l2_common v4l1_compat ipw3945 snd_seq snd_timer nvidia(P) ieee80211 snd_seq_device irda ieee80211_crypt i2c_core crc_ccitt snd soundcore sdhci mmc_core iTCO_wdt iTCO_vendor_support psmouse intel_agp agpgart serio_raw snd_page_alloc shpchp pci_hotplug evdev tsdev pcspkr ext3 jbd mbcache usbhid hid sg sr_mod cdrom sd_mod ata_piix ata_generic libata scsi_mod ohci1394 ieee1394 r8169 ehci_hcd generic uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb
[29245.464000] CPU:    0
[29245.464000] EIP:    0060:[<c013736e>]    Tainted: P      VLI
[29245.464000] EFLAGS: 00010296   (2.6.20-16-generic #2)
[29245.464000] EIP is at run_workqueue+0xee/0x140
[29245.464000] eax: 0000c5a8   ebx: f7533dcc   ecx: 00000246   edx: 00000000
[29245.464000] esi: f7533dc0   edi: f7533dc8   ebp: 00000246   esp: f78fbf58
[29245.464000] ds: 007b   es: 007b   ss: 0068
[29245.464000] Process ipw3945/0 (pid: 3773, ti=f78fa000 task=df895a90 task.ti=f78fa000)
[29245.464000] Stack: 00000000 f7533dd4 f78fbf9c df895a90 f7533dcb f7533de0 00000001 f7533dc0 
[29245.464000]        f7533dcc f7533dd4 f78fbf9c c0137d97 00000001 00000000 c1806940 00010000 
[29245.464000]        00000000 00000000 df895a90 c0120b40 00100100 00200200 ffffffff ffffffff 
[29245.464000] Call Trace:
[29245.464000]  [<c0137d97>] worker_thread+0x147/0x170
[29245.464000]  [<c0120b40>] default_wake_function+0x0/0x10
[29245.464000]  [<c0137c50>] worker_thread+0x0/0x170
[29245.464000]  [<c013ac4a>] kthread+0xba/0xf0
[29245.464000]  [<c013ab90>] kthread+0x0/0xf0
[29245.464000]  [<c01044c7>] kernel_thread_helper+0x7/0x10
[29245.464000]  =======================
[29245.464000] Code: 24 00 00 00 00 e8 f3 72 fe ff 8b 44 24 10 3b 46 0c 0f 85 78 ff ff ff 83 6e 34 01 89 ea 83 c4 1c 89 f0 5b 5e 5f 5d e9 a2 76 1b 00 <0f> 0b eb fe 65 a1 08 00 00 00 8b 90 a4 00 00 00 05 94 01 00 00 
[29245.464000] EIP: [<c013736e>] run_workqueue+0xee/0x140 SS:ESP 0068:f78fbf58
[29245.464000]  <3>NVRM: Xid (0001:00): 13, 0000 01013900 00000039 00000328 00000000 00000080


&#9679;  sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                             There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:6b:13:24
Sending on   LPF/eth1/00:13:02:6b:13:24
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
/etc/network/if-up.d/avahi-daemon: 15: /usr/sbin/avahi-daemon: not found
                                                                                            [ OK ]

&#9679;  lsmod |grep ipw3945
ipw3945               118816  1 
ieee80211              34760  1 ipw3945

&#9679;  uname -r
**2.6.20-16-generic**

---

