---
title: "ASUS N552VW problems with ubuntu"
date: 2017-05-31
forum: Hardware
---

### Post by Mohamad_Fadavi on 2017-05-31
Hello there. I've installed Ubuntu on my new laptop ([ASUS N552VW-A]("https://www.asus.com/Laptops/VivoBook-Pro-N552VW/")).
I've got some problems in Ubuntu:

[LIST=1]
[*]Sometimes, my laptop immediately freezes after unplugging the AC adapter. 
[*]Fan speed get high with free drivers. 
[*]After installing propietary drivers (Intel microcode & Nvidia Driver v381.22), fan speed is OK, but now, I can't switch to Intel using prime. 
[*]Battery usage is too high against same situation on Windows. 
[*]There's many boot errors in systemd journal (see below). 
[/LIST]
 Please help me to solve these problems. :( [HR][/HR]**Distro:** Ubuntu 17.04 zesty zapus (but migrated from Unity to GNOME Shell)
**Kernel:** x86_64 Linux 4.10.0-21-generic
**Desktop Environment:** GNOME Shell + GDM3 as DM
**CPU:** Intel Core i7-6700HQ CPU @ 3.5GHz
**GPU:** GeForce GTX 960M

```
$ **journalctl -p 3**

-- Logs begin at Wed 2017-05-31 11:07:36 +0430, end at Wed 2017-05-31 11:41:50 +0430. --
&#1605;&#1607; 31 11:07:37 rexxar kernel: tpm_crb MSFT0101:00: can't request region for resource [mem 0xfed40080-0xfed40fff]
&#1605;&#1607; 31 11:07:37 rexxar kernel: iwlwifi 0000:02:00.0: pci_enable_msi failed - -22
&#1605;&#1607; 31 11:07:38 rexxar bluetoothd[1164]: Failed to obtain handles for "Service Changed" characteristic
&#1605;&#1607; 31 11:07:38 rexxar bluetoothd[1164]: Sap driver initialization failed.
&#1605;&#1607; 31 11:07:38 rexxar bluetoothd[1164]: sap-server: Operation not permitted (1)
&#1605;&#1607; 31 11:07:39 rexxar ofonod[1246]: get_property_value: ERROR reply to Get
&#1605;&#1607; 31 11:07:39 rexxar ofonod[1246]: get_property_value: ERROR reply to Get
&#1605;&#1607; 31 11:07:39 rexxar NetworkManager[1278]: ((devices/nm-device.c:970)): assertion '<dropped>' failed
&#1605;&#1607; 31 11:07:39 rexxar wpa_supplicant[1618]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
&#1605;&#1607; 31 11:07:39 rexxar wpa_supplicant[1618]: dbus: Failed to construct signal
&#1605;&#1607; 31 11:07:39 rexxar wpa_supplicant[1618]: Could not read interface p2p-dev-wlp2s0 flags: No such device
&#1605;&#1607; 31 11:07:45 rexxar spice-vdagent[3795]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
&#1605;&#1607; 31 11:07:49 rexxar ofonod[1246]: get_property_value: ERROR reply to Get
&#1605;&#1607; 31 11:07:55 rexxar bluetoothd[1164]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
&#1605;&#1607; 31 11:07:55 rexxar pulseaudio[4117]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.ofono.Error.InUse: The resource is currently in use
&#1605;&#1607; 31 11:07:57 rexxar spice-vdagent[4279]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
```

```
$ **journalctl -p 4**

[[output here]]("http://paste.ubuntu.com/24723936/")
```

```
$ **lspci**

00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Skylake PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-H Serial IO I2C Controller #0 (rev 31)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-H Serial IO I2C Controller #1 (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1)
00:1c.3 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #4 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
03:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
04:00.0 USB controller: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller
```

```
$ **lsusb**

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 003: ID 04f2:b3fd Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 062a:4102 Creative Labs 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Mohamad_Fadavi on 2017-06-02
Any idea / solution?!

---

