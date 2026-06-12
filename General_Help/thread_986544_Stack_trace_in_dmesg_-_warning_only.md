---
title: "Stack trace in dmesg - warning only"
date: 2008-11-18
forum: General Help
---

### Post by damien_d on 2008-11-18
Hello all,

I am using 8.10 Intrepid UMPC on my Acer Aspire One, and have installed linux module backports to get the wireless happening.

The unit has been on for several days now and when I have looked at dmesg, I have a bunch of stacktraces separated by several hours.  They are all very similar to the following:

```

[ 7021.346513] ------------[ cut here ]------------
[ 7021.346543] WARNING: at /build/buildd/linux-backports-modules-2.6.27-2.6.27/debian/build/build-generic/compat-wireless-2.6/net/mac80211/rx.c:2200 lbm_cw___lbm_cw_ieee80211_rx+0x19f/0x600 [lbm_cw_mac80211]()
[ 7021.346556] Modules linked in: nls_cp437 cifs aes_i586 aes_generic af_packet i915 drm binfmt_misc rfcomm bridge stp bnep sco l2cap bluetooth ppdev acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative sbs sbshc pci_slot container parport_pc lp parport fuse joydev ath_pci wlan ath_hal(P) arc4 ecb crypto_blkcipher uvcvideo compat_ioctl32 snd_hda_intel acer_wmi videodev snd_pcm_oss snd_mixer_oss v4l1_compat snd_pcm ath5k lbm_cw_mac80211 lbm_cw_cfg80211 video output led_class evdev snd_seq_dummy wmi psmouse serio_raw battery snd_seq_oss snd_seq_midi ac button snd_rawmidi snd_seq_midi_event snd_seq pcspkr snd_timer snd_seq_device iTCO_wdt iTCO_vendor_support snd intel_agp shpchp pci_hotplug agpgart soundcore snd_page_alloc ext2 mbcache sd_mod crc_t10dif sg pata_acpi ata_piix ata_generic libata scsi_mod uhci_hcd dock ehci_hcd usbcore r8169 thermal processor fan fbcon tileblit font bitblit softcursor
[ 7021.346757] Pid: 0, comm: swapper Tainted: P          2.6.27-7-generic #1
[ 7021.346765]  [<c037c406>] ? printk+0x1d/0x1f
[ 7021.346783]  [<c0131de9>] warn_on_slowpath+0x59/0x90
[ 7021.346815]  [<c024d1d5>] ? __next_cpu+0x15/0x30
[ 7021.346826]  [<c012989d>] ? find_busiest_group+0x15d/0x7c0
[ 7021.346840]  [<c014d255>] ? sched_clock_cpu+0xd5/0x170
[ 7021.346860]  [<f8b729af>] lbm_cw___lbm_cw_ieee80211_rx+0x19f/0x600 [lbm_cw_mac80211]
[ 7021.346900]  [<c012658d>] ? update_shares+0x1d/0x70
[ 7021.346911]  [<c02eae1c>] ? skb_put+0xc/0xa0
[ 7021.346931]  [<f8b48c83>] ath5k_tasklet_rx+0x2e3/0x550 [ath5k]
[ 7021.346956]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
[ 7021.346970]  [<c0137258>] tasklet_action+0x78/0x100
[ 7021.346981]  [<c0137682>] __do_softirq+0x92/0x120
[ 7021.346990]  [<c013776d>] do_softirq+0x5d/0x60
[ 7021.347000]  [<c01378e5>] irq_exit+0x55/0x90
[ 7021.347009]  [<c0106c1a>] do_IRQ+0x4a/0x80
[ 7021.347020]  [<c0105003>] common_interrupt+0x23/0x30
[ 7021.347031]  [<c01700d8>] ? __audit_mq_getsetattr+0x68/0xb0
[ 7021.347058]  [<f884c800>] ? acpi_idle_enter_bm+0x268/0x2b7 [processor]
[ 7021.347092]  [<c02dbf7b>] cpuidle_idle_call+0x7b/0xd0
[ 7021.347103]  [<c010288d>] cpu_idle+0x7d/0x140
[ 7021.347112]  [<c036edd3>] rest_init+0x53/0x60
[ 7021.347124]  =======================
[ 7021.347130] ---[ end trace 15d420761db862e3 ]---

```

The full dmesg output is at: [http://www.pastebin.ca/1260886](http://www.pastebin.ca/1260886)

And for information's sake:
```

damien@damien-mini:~$ uname -r
2.6.27-7-generic
damien@damien-mini:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
damien@damien-mini:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


```

I don't have any obvious problems with my wireless connection, so I'm not sure what information people can glean out of this, but surely someone will google it one day :)

---

