---
title: "Still Realtek 8192 Driver Problems"
date: 2010-08-08
forum: Hardware
---

### Post by ubuntopoly on 2010-08-08
Hi - I bought a Samsung N220 netbook a good month ago and am still having wireless adapter problems.  Initially the Realtek 8192 card was working under Windows 7 and not Linux.

Now Windows 7 is falling over on startup and Linux is working initially but my box dies after a day or so.  I'm running Ubuntu Netbook 10.04/2.6.32-24-generic.

root@bonobo:~# lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
0b:00.0 Multimedia controller: Broadcom Corporation Device 1615
root@bonobo:~# 

I'm not quite sure what version of Realtek 8192 I'm having but this is what I did:  I downloaded the rtl8192se_linux_2.6.0017.0507.2010 driver from Realtek and did a make; make install. I then rebooted the kernel and my system was hanging during startup - I suppose upon loading the new r8192se_pci.ko. My first idea was to check card version details under windows and tried to boot windows 7. Not working, windows 7 is now falling over and my best explanation for this is that it doesn't like the new firmware the driver comes with. I then booted the older kernel 2.6.32-21 and - magically - the wireless card was working. Kind of. Again, I think this is because of the new firmware.  I now reinstalled the original 2.6.32-24-generic modules and can boot the newest kernel with wireless adapter up but I think there are still stability problems.

Aug  9 00:05:39 bonobo kernel: [ 1910.862264] ========>ieee80211_parse_info_param(): athros AP is exist
Aug  9 00:05:39 bonobo kernel: [ 1910.875320] ========>ieee80211_parse_info_param(): athros AP is exist
Aug  9 00:05:39 bonobo kernel: [ 1910.875332] ========>ieee80211_parse_info_param(): athros AP is exist


My kernel messages get flooded with the above spam and probably some incompatibility with old 8192 drivers and new firmware causes the little netbook to die after a day or so.     :sad: Has anyone any advice or does anyone even know how one can get this Realtek wireless card to run properly? I wish I had bought a netbook with atheros chipset...

---

