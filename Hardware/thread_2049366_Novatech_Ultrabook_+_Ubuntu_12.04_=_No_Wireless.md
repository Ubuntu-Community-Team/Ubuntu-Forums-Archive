---
title: "Novatech Ultrabook + Ubuntu 12.04 = No Wireless"
date: 2012-08-28
forum: Hardware
---

### Post by Jedwinjim on 2012-08-28
Hi, I just bought a Novatech Ultrabook n1403 today & put Ubuntu 12.04 straight on. I have 2 major problems (which after some google searching I see other people have also had with Novatech. 1 is the trackpad & mouse buttons don't work: at all. I can live without that for the moment though. The other is much more important, no wireless!

I followed this thread in the hope that it would help me but no joy:

[http://ubuntuforums.org/showthread.php?t=2035902](http://ubuntuforums.org/showthread.php?t=2035902)

my lspci:


00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Network controller: Ralink corp. Device 3290
01:00.1 Bluetooth: Ralink corp. Device 3298
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


Any help much appreciated!

joe.

---

### Post by alexmoon on 2012-10-05
Hi Joe,

I notice that you have this down as solved. I also have a Ralink 3290, was wondering if you'd share how you fixed it?

Thanks,
sky.

---

### Post by bruce247 on 2012-10-28
This is how I got it to work:

Download from Ralink website the 3290 linux driver and extract.
([http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501), under RT3290 PCIe)

"Go into /os/linux/config.mk in the unpacked drivers and set:

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Manager
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Recompile and reinstall drivers with "sudo make && sudo make install". After that reboot.
ra0 should now be picked up by NetworkManager."

This is info is copied from: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/202082](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/202082) , thanks to Felix Engemann.

---

