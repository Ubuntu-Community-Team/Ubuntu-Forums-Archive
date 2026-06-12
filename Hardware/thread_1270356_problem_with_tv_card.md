---
title: "problem with tv card"
date: 2009-09-19
forum: Hardware
---

### Post by ali313 on 2009-09-19
i have a tv card with saa7134 chipset. but tvtime & xawtv show only a black screen.
lspci command in terminal show:
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
05:01.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
05:02.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

```and dmesg:
```
[   14.792998] saa7130/34: v4l2 driver version 0.2.14 loaded
[   14.793164] saa7134 0000:05:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.793169] saa7130[0]: found at 0000:05:02.0, rev: 1, irq: 17, latency: 64, mmio: 0xfebefc00
[   14.793174] saa7130[0]: subsystem: 1131:0000, board: SKNet Monster TV [card=5,insmod option]
[   14.793212] saa7130[0]: board init: gpio is c04000
[   14.811444] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.811484] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.841924] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   14.896743] saa7130[0]: Huh, no eeprom present (err=-5)?
[   14.964102] tuner' 0-0043: chip found @ 0x86 (saa7130[0])
[   14.969082] tda9887 0-0043: creating new instance
[   14.969085] tda9887 0-0043: tda988[5/6/7] found
[   14.996017] All bytes are equal. It is not a TEA5767
[   14.996107] tuner' 0-0060: chip found @ 0xc0 (saa7130[0])
[   15.012512] tuner-simple 0-0060: creating new instance
[   15.012518] tuner-simple 0-0060: type set to 3 (Philips (SECAM+PAL_BG) (FI1216MF, FM1216MF, FR1216MF))
[   15.036587] saa7130[0]: registered device video0 [v4l2]
[   15.036604] saa7130[0]: registered device vbi0
[   15.036622] saa7130[0]: registered device radio0
[   15.048630] saa7134 ALSA driver for DMA sound loaded
[   15.048655] saa7130[0]/alsa: saa7130[0] at 0xfebefc00 irq 17 registered as card 1
[   15.758247] EXT3 FS on sda9, internal journal
[   17.135146] kjournald starting.  Commit interval 5 seconds
[   17.135383] EXT3 FS on sda10, internal journal
[   17.135390] EXT3-fs: mounted filesystem with ordered data mode.
[   17.383574] type=1505 audit(1253378055.818:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2269
[   17.417469] type=1505 audit(1253378055.854:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2273
[   17.417554] type=1505 audit(1253378055.854:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2273
[   17.417584] type=1505 audit(1253378055.854:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2273
[   17.417616] type=1505 audit(1253378055.854:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2273
[   17.512578] type=1505 audit(1253378055.950:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2278
[   17.512726] type=1505 audit(1253378055.950:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2278
[   17.537576] type=1505 audit(1253378055.974:9): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=2282
[   17.556883] type=1505 audit(1253378055.994:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2286
[   23.317349] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   23.317352] vboxdrv: Successfully done.
[   23.317353] vboxdrv: Found 2 processor cores.
[   23.318049] vboxdrv: fAsync=0 offMin=0x1db offMax=0x16b4
[   23.318086] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   23.318087] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   25.747951] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.747954] Bluetooth: BNEP filters: protocol multicast
[   25.793032] Bridge firewalling registered
[   27.304852] lp0: using parport0 (interrupt-driven).
[   31.562224] r8169: eth0: link up
[   31.562229] r8169: eth0: link up
[   41.844011] eth0: no IPv6 routers present
[ 1007.006084] NET: Registered protocol family 24

```what should i do? i am a beginner

---

### Post by khelben1979 on 2009-09-19
Have you tried [MythTV]("http://en.wikipedia.org/wiki/Mythtv")?

---

### Post by ali313 on 2009-09-19
yes. but is was without result too
i think that my tv card is not installed properly
how i must install its driver?

---

### Post by khelben1979 on 2009-09-19
> **ali313 said:**
> yes. but is was without result too
i think that my tv card is not installed properly
how i must install its driver?

Well, the first thing you can do is to describe the exact model of this TV card so it will be easier to find when doing a Google search on this.

I wouldn't be surprised if the Ubuntu Linux kernel which you're using don't have support for your tv card compiled as default, still, when compiling your own Linux kernel you can see for yourself if it's supported by the kernel or not, but this is not recommended for newbies of course since I fail at this myself sometimes..

(Ooops, I now see from the list that it's there, I'll look into it at a later time, need to get some sleep soon.)

---

### Post by ali313 on 2009-09-20
thank you

---

### Post by Ayuthia on 2009-09-20
You might try this link:
[http://jobinau.googlepages.com/saa7130basedtvtunercardunderlinux](http://jobinau.googlepages.com/saa7130basedtvtunercardunderlinux)

---

