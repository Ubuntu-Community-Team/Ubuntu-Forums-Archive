---
title: "Thinkpad X200 Wireless Card Not Recognised"
date: 2010-03-20
forum: Hardware
---

### Post by jameshogan on 2010-03-20
Hey World :)

Just brought a Lenovo Thinkpad X200, and did a fresh install of Karmic.  Everything works fine, except the wireless card isn't being recognised.  There's a thread associated with the thinkpad but it doesn't seem to make sense.

So I lspci 'ed and got:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LF Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

Which looks like the thinkpad's Intel wifi link 5100 or 5300 isn't listed anywhere.

And ideas what's the next step I should take to get wireless running?


Cheers,
James

---

### Post by chili555 on 2010-05-04
Are you sure you don't have an X200s? You seem to have this:> 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
[http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II](http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II)

There are many posts here about building the r8192se_pci module. Also, it's included in Lucid. Do you want to try the live CD first?

---

