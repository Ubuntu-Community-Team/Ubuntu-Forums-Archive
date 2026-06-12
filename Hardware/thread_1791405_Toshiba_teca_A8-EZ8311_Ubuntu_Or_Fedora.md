---
title: "Toshiba teca A8-EZ8311 Ubuntu Or Fedora"
date: 2011-06-26
forum: Hardware
---

### Post by snafu006 on 2011-06-26
Helllo i got this a Toshiba form a yard sell and i know its old but it still works. But here the thing The ATi Xpress 200m 128mb sucks. its running ubuntu 10.10 just fine with 3d Acceleration. But glxgears is only giving me 60+ frames and i was see if there is better drivers or try a differnt os.

```
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

```
snafu-tecra-a8            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1380MiB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts aperfmperf pni monitor tm2 xtpr pdcm
     *-pci
          description: Host bridge
          product: ATI Technologies Inc
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:ffd00000-ffdfffff memory:d0000000-dfffffff
           *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:17 memory:d0000000-dfffffff ioport:ce00(size=256) memory:ffdf0000-ffdfffff memory:ffd00000-ffd1ffff
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:ffc00000-ffcfffff
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:16:e3:60:ee:b1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A ip=192.168.2.100 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 memory:ffcf0000-ffcfffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:bff8(size=8) ioport:bff4(size=4) ioport:bfe8(size=8) ioport:bfe4(size=4) ioport:bfa0(size=16) memory:ffaffe00-ffafffff memory:ffa00000-ffa7ffff
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:ffafe000-ffafefff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:ffafd000-ffafdfff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:ffafc000-ffafcfff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 82
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:d880(size=16) memory:64000000-640003ff
        *-ide:1
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bf70(size=16)
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:41 memory:ffaf8000-ffafbfff
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:a000(size=4096) memory:ff900000-ff9fffff memory:60000000-63ffffff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:03:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:23 memory:ff900000-ff900fff ioport:a000(size=256) ioport:a400(size=256) memory:60000000-63ffffff memory:68000000-6bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:03:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:22 memory:ff9ff800-ff9fffff memory:ff9f8000-ff9fbfff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:03:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7
                resources: irq:18 memory:ff9ff700-ff9ff7ff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:03:07.0
                logical name: eth0
                version: 10
                serial: 00:0e:7b:fe:42:f1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes

```

```
Module                  Size  Used by
binfmt_misc             6599  1 
joydev                  8767  0 
snd_hda_codec_si3054     3440  1 
snd_hda_codec_realtek   218492  1 
tpm_infineon            7937  0 
snd_hda_intel          22235  5 
snd_hda_codec          87552  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
arc4                    1165  2 
snd_pcm                71475  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
radeon                829223  4 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
ath5k                 130083  0 
snd_seq_midi_event      6047  1 snd_seq_midi
pcmcia                 35973  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
mac80211              231959  1 ath5k
ttm                    56633  1 radeon
snd_timer              19067  2 snd_pcm,snd_seq
drm_kms_helper         30200  1 radeon
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
ath                     8153  1 ath5k
drm                   168060  6 radeon,ttm,drm_kms_helper
tpm_tis                 7658  0 
yenta_socket           21518  0 
video                  18712  0 
parport_pc             26058  1 
cfg80211              144694  3 ath5k,mac80211,ath
psmouse                59033  0 
pcmcia_rsrc            10566  1 yenta_socket
tpm                    13741  2 tpm_infineon,tpm_tis
ati_agp                 5202  0 
snd                    49038  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  1883  1 video
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
tpm_bios                5310  1 tpm
toshiba_acpi            8454  0 
serio_raw               4022  0 
i2c_algo_bit            5168  1 radeon
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
coretemp                5326  0 
shpchp                 29886  0 
agpgart                32011  3 ttm,drm,ati_agp
i2c_piix4               8635  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
firewire_ohci          21234  0 
sdhci_pci               6633  0 
8139too                19581  0 
firewire_core          46643  1 firewire_ohci
8139cp                 16934  0 
sdhci                  15922  1 sdhci_pci
led_class               2633  2 ath5k,sdhci
pata_atiixp             3288  0 
sata_sil                7035  2 
mii                     4425  2 8139too,8139cp
crc_itu_t               1383  1 firewire_core

```

---

