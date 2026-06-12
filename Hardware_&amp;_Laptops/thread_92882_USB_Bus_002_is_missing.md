---
title: "USB Bus 002 is missing"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by Helix_2648 on 2005-11-20
Hello,

I really need help from you because the people in the german forum couldn't help me.

I installed Ubuntu Breezer on a external USB Driver and it seems to be, that Ubuntu can't find my second USB Bus Controller.

I tried Knoppix Live DVD and there I saw (with lsusb) that it shows me a second USB Bus which Ubuntu don't shows.

Here ist my lsusb:

```

Bus 001 Device 006: ID 05dc:0300 Lexar Media, Inc. Jumpdrive Geysr
Bus 001 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 001 Device 001: ID 0000:0000

```

Here is my dmesg:

```

17 chip Yukon-Lite rev 7
[4294686.423000] skge eth2: addr 00:11:d8:70:3d:39
[4294688.814000] ACPI: Fan [FAN] (on)
[4294688.816000] ACPI: CPU0 (power states: C1[C1])
[4294688.816000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294688.817000] ACPI: Thermal Zone [THRM] (40 C)
[4294688.891000] Attempting manual resume
[4294688.914000] swsusp: Suspend partition has wrong signature?
[4294688.938000] kjournald starting.  Commit interval 5 seconds
[4294688.938000] EXT3-fs: mounted filesystem with ordered data mode.
[4294690.490000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294693.167000] Adding 1614492k swap on /dev/sda5.  Priority:-1 extents:1
[4294693.314000] EXT3 FS on sda1, internal journal
[4294701.349000] parport: PnPBIOS parport detected.
[4294701.349000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTA TE,COMPAT,ECP,DMA]
[4294701.435000] lp0: using parport0 (interrupt-driven).
[4294701.456000] mice: PS/2 mouse device common for all mice
[4294701.782000] input: PS2++ Logitech MX Mouse on isa0060/serio1
[4294702.093000] ts: Compaq touchscreen protocol output
[4294704.064000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294704.742000] cdrom: open failed.
[4294706.274000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[4294706.285000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[4294706.565000] nvnet: module license 'NVIDIA' taints kernel.
[4294706.639000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294706.650000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294706.926000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF24 13)
[4294706.945000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294706.949000] ath_rate_sample: 1.2
[4294706.954000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294706.957000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[4294706.957000] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC1] -> GSI 16 (l evel, low) -> IRQ 16
[4294707.372000] Build date: Nov 18 2005
[4294707.372000] Debugging version (IEEE80211)
[4294707.372000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294707.372000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294707.372000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48M bps 54Mbps
[4294707.372000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294707.372000] ath0: mac 5.9 phy 4.3 radio 4.6
[4294707.372000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294707.372000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294707.372000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294707.372000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294707.372000] ath0: Use hw queue 8 for CAB traffic
[4294707.372000] ath0: Use hw queue 9 for beacons
[4294707.372000] Debugging version (ATH)
[4294707.372000] ath0: Atheros 5212: mem=0xd1400000, irq=16
[4294709.390000] Real Time Clock Driver v1.12
[4294709.455000] input: PC Speaker
[4294709.533000] Floppy drive(s): fd0 is 1.44M
[4294709.548000] FDC 0 is a post-1991 82077
[4294713.598000] ACPI: Power Button (FF) [PWRF]
[4294713.598000] ACPI: Power Button (CM) [PWRB]
[4294713.681000] ibm_acpi: ec object not found
[4294725.450000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294725.450000] apm: overridden by ACPI.
[4294726.150000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (versio n 1.40.4)
[4294726.153000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[4294726.688000] Bluetooth: Core ver 2.7
[4294726.688000] NET: Registered protocol family 31
[4294726.688000] Bluetooth: HCI device and connection manager initialized
[4294726.688000] Bluetooth: HCI socket layer initialized
[4294726.804000] Bluetooth: L2CAP ver 2.7
[4294726.804000] Bluetooth: L2CAP socket layer initialized
[4294726.820000] Bluetooth: RFCOMM ver 1.5
[4294726.820000] Bluetooth: RFCOMM socket layer initialized
[4294726.820000] Bluetooth: RFCOMM TTY layer initialized
[4294729.735000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4294729.735000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4294734.316000] NET: Registered protocol family 10
[4294734.316000] Disabled Privacy Extensions on device c02eb280(lo)
[4294734.316000] IPv6 over IPv4 tunneling driver
[4294740.530000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294744.822000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294744.890000] ISO 9660 Extensions: RRIP_1991A
[4294744.971000] ath0: no IPv6 routers present
[4294772.143000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4294772.143000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4294773.833000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4294773.833000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4294779.983000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4294779.983000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4294786.526000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4294786.526000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4294831.839000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4294831.839000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4294866.008000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4294866.008000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4294891.472000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4294891.472000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4294967.966000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4294967.966000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4294968.235000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4294968.235000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4294991.250000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4294991.250000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295010.209000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295010.209000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295045.967000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4295045.967000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295048.308000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295048.308000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295114.514000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4295114.514000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295126.456000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295126.456000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295234.063000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4295234.063000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295234.209000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295234.209000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295265.564000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295265.564000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295471.690000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4295471.690000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295498.001000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295498.001000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295511.142000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295511.142000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295562.434000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4295562.434000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295563.150000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295563.150000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295569.602000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295569.602000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295578.003000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295578.003000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295584.419000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295584.419000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295589.590000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295589.590000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295599.161000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295599.161000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295648.259000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4295648.259000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295649.981000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295649.981000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295655.004000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295655.004000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295660.174000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295660.174000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295666.534000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295666.534000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295670.543000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295670.543000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295675.940000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295675.940000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295680.554000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295680.554000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295684.971000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295684.971000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295689.988000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295689.988000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295693.333000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295693.333000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295698.865000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295698.865000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295707.345000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295707.345000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295707.751000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4295707.751000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295711.919000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295711.919000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295716.737000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295716.737000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295722.855000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295722.855000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295732.242000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295732.242000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295738.921000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295738.921000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295743.615000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295743.615000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295746.727000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295746.727000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295753.126000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295753.126000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295757.791000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295757.791000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295764.886000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295764.886000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295767.585000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4295767.585000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295771.302000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295771.302000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295780.006000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295780.006000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295784.645000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295784.645000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295799.006000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295799.006000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295805.198000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295805.198000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295812.134000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295812.134000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295821.439000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295821.439000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295827.429000] atkbd.c: Unknown key released (translated set 2, code 0x81 on i sa0060/serio0).
[4295827.429000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4295830.581000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4295830.581000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295830.685000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4295830.685000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295835.925000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295835.925000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4295844.769000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on is a0060/serio0).
[4295844.769000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

```

And lsmod shows me:

```

Module                  Size  Used by
nls_utf8                2176  1
nls_cp437               5888  2
vfat                   12288  1
fat                    46492  1 vfat
isofs                  32824  1
udf                    75524  0
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
wlan_wep                5760  1
analog                 10528  0
gameport               14472  1 analog
snd_mpu401              6344  1
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
snd                    48644  6 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
ath_pci                69148  0
ath_rate_sample        14088  1 ath_pci
wlan                  122140  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148176  3 ath_pci,ath_rate_sample
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
nvnet                  69284  0
i2c_nforce2             6528  0
i2c_core               19728  2 i2c_acpi_ec,i2c_nforce2
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
skge                   33040  0
sata_sil                9476  0

via_rhine              20356  0
mii                     5248  1 via_rhine
forcedeth              19072  0
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_generic             1664  0
amd74xx                12828  1
sata_nv                 9092  0
libata                 47876  2 sata_sil,sata_nv
unix                   24624  603
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
usb_storage            64704  6
ide_core              125268  4 ide_cd,ide_generic,amd74xx,usb_storage
uhci_hcd               28048  0
ohci_hcd               18564  0
ehci_hcd               29448  0
usbcore               104188  5 usb_storage,uhci_hcd,ohci_hcd,ehci_hcd
sd_mod                 17424  5
scsi_mod              124872  3 libata,usb_storage,sd_mod
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

Is there a missing module or something like that?

Maybe it's important for you... It's funny because I can use my USB Stick on one Port but I can't use my mouse if I try it on the same port. I also can't use my printer.. :( 

For your information... I have a Asus A8N-SLI Board.

Regrads,

Helix

... sorry for my bad english.. ;)

---

