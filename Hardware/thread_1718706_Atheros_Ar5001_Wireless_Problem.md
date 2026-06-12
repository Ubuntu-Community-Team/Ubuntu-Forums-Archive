---
title: "Atheros Ar5001 Wireless Problem"
date: 2011-03-31
forum: Hardware
---

### Post by upshutdown on 2011-03-31
So I have searched just about everywhere I can think of searching, and have been unable to properly setup the Atheros AR5001 Wireless card. All I seem to get is Wireless is disabled under the Network Manager. 

here is some info:

lspci -v returns: 
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602 (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d2300000-d24fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00006fff
	Memory behind bridge: d1300000-d22fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1200000-d12fffff
	Prefetchable memory behind bridge: 00000000d2600000-00000000d26fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: d1100000-d11fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2700000-d27fffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at d2508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d2508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at d2400000 (32-bit, non-prefetchable) [size=64K]
	Memory at d2300000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1200300 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at d2600000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: fast devsel, IRQ 17
	Memory at d1200200 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1200100 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d1200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d1100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at 2000 [size=256]
	Memory at d1010000 (64-bit, prefetchable) [size=4K]
	Memory at d1000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


```

lsmod returns:
```
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  197 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
snd_hda_codec_atihdmi     3079  1 
arc4                    1497  2 
fglrx                2523725  33 
snd_hda_codec_idt      64699  1 
ath5k                 145307  0 
snd_hda_intel          26147  2 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_hda_codec         100951  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq_midi_event      7291  1 snd_seq_midi
snd_hwdep               6660  1 snd_hda_codec
ath                    16173  1 ath5k
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
mac80211              276208  1 ath5k
snd_timer              23850  2 snd_seq,snd_pcm
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              10047  0 
edac_core              46822  0 
cfg80211              166185  3 ath5k,ath,mac80211
snd                    64181  13 snd_hda_codec_idt,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_timer,snd_seq_device
shpchp                 34910  0 
k10temp                 3535  0 
compat                  4984  1 cfg80211
soundcore               1240  1 snd
edac_mce_amd            9387  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
jmb38x_ms               8667  0 
memstick               10185  1 jmb38x_ms
joydev                 11395  0 
pcspkr                  2022  0 
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
psmouse                62080  0 
v4l2_compat_ioctl32    12614  1 videodev
serio_raw               4910  0 
lirc_ene0100            7819  0 
hp_accel               14304  0 
lirc_dev               11209  1 lirc_ene0100
lis3lv02d              10384  1 hp_accel
input_polldev           4527  1 lis3lv02d
hp_wmi                  6467  0 
lp                     10201  0 
evbug                   2269  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22210  2 
pata_atiixp             4405  0 
sdhci_pci               8083  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  3 ath5k,hp_accel,sdhci
libahci                26148  1 ahci
r8169                  42254  0 
mii                     5261  1 r8169
video                  22176  0 
output                  2527  1 video

```

sudo iwconfig returns:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

If you guys need anymore information I would be happy to give it our, ive been having trouble dealing with this for quite a while now, so anything input would be greatly appreciated!!

---

### Post by upshutdown on 2011-03-31
sorry to bumb, It's somewhat pressing

---

