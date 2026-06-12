---
title: "Wireless is dead on Asus UL30Vt laptop new install ubuntu 11.10"
date: 2011-12-03
forum: Hardware
---

### Post by torryto on 2011-12-03
Hi guys,
I have spent the past two days trying to figure out why the wireless on my asus ul30vt is not working. Perhaps my completely uninstalling windows has something to do with it?

Here are results of my diagnostics. Thanks for all help, If I don't resolve this issue I am practically tied to my cable box.

**uname -mr**
3.0.0-13-generic x86_64


**ndiswrapper -l**
netw5s64 : driver installed


**lshw -C Network**
  *-network UNCLAIMED     
       description: Network controller
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:feafe000-feafffff
       
Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]


** lsmod | grep asus**asus_laptop            19722  0 
sparse_keymap          13890  1 asus_laptop


**modinfo asus_laptop**
filename:       /lib/modules/3.0.0-13-generic/kernel/drivers/platform/x86/asus-laptop.ko
license:        GPL
description:    Asus Laptop Support
author:         Julien Lerouge, Karol Kozimor, Corentin Chary
srcversion:     47A5AFED1B968C9FFEEE47F
alias:          acpi*:ATK0101:*
alias:          acpi*:ATK0100:*
depends:        sparse-keymap
vermagic:       3.0.0-13-generic SMP mod_unload modversions 
parm:           wapf:WAPF value (uint)
parm:            wlan_status:Set the wireless status on boot (0 = disabled, 1 = enabled,  -1 = don't do anything). default is 1 (int)
parm:            bluetooth_status:Set the wireless status on boot (0 = disabled, 1 =  enabled, -1 = don't do anything). default is 1 (int)
parm:            wimax_status:Set the wireless status on boot (0 = disabled, 1 =  enabled, -1 = don't do anything). default is 1 (int)
parm:            wwan_status:Set the wireless status on boot (0 = disabled, 1 = enabled,  -1 = don't do anything). default is 1 (int)




**dmesg | grep iwl**
[   11.356334] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   11.356339] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   11.356469] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.356480] iwlagn 0000:03:00.0: setting latency timer to 64
[   11.356515] iwlagn 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   11.379957] iwlagn 0000:03:00.0: Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x3 < 0x4
[   11.388621] iwlagn 0000:03:00.0: PCI INT A disabled
[   11.388639] iwlagn: probe of 0000:03:00.0 failed with error -22
[  961.843426] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  961.843431] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  1462.816151] Modules linked in: iwl3945 iwl_legacy bnep rfcomm  parport_pc ppdev dm_crypt nvidia(P) binfmt_misc snd_hda_codec_hdmi  joydev mxm_wmi uvcvideo videodev v4l2_compat_ioctl32  snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm  snd_seq_midi psmouse snd_rawmidi serio_raw btusb snd_seq_midi_event  snd_seq bluetooth wmi snd_timer snd_seq_device iwlagn mac80211 snd  asus_laptop cfg80211 sparse_keymap soundcore snd_page_alloc lp parport  ahci libahci i915 atl1c drm_kms_helper drm i2c_algo_bit video




**lspci -v**
Network controller: Intel Corporation Ultimate N WiFi Link 5300
    Subsystem: Intel Corporation Device 1101
    Flags: fast devsel, IRQ 17
    Memory at feafe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-16-ea-ff-ff-02-37-50
    Kernel modules: iwlagn


**iwconfig**
    lo        no wireless extensions.


eth0      no wireless extensions.


**dmesg | grep iwl**
iwlagn 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[    12.739505] type=1400 audit(1322948504.417:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=702  comm="apparmor_parser"
[    12.740090] type=1400 audit(1322948504.421:3): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=702  comm="apparmor_parser"
[    12.740397] type=1400 audit(1322948504.421:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=702 comm="apparmor_parser"
[   12.748344] iwlagn 0000:03:00.0: Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x3 < 0x4
[   12.770778] iwlagn 0000:03:00.0: PCI INT A disabled
[   12.770797] iwlagn: probe of 0000:03:00.0 failed with error -22
[   12.772171] nvidia: module license 'NVIDIA' taints kernel.
[   12.772177] Disabling lock debugging due to kernel taint




**rfkill list**
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

