---
title: "Coolbox CR600 not reading SD cards in Ubuntu 12.04 64 bits"
date: 2012-10-17
forum: Hardware
---

### Post by Jason Pierce on 2012-10-17
Hi. I'd appreciate any kind of help :)

I've been using this card reader (Coolbox CR600) in Ubuntu 11.04 without problems but now, after a clean installation of 12.04 version, the card reader capabilities (SD, MMC, and so on) stopped working, although I can work with smart cards (spanish ID e.g.) First of all, this reader uses **RT5161** chip and Ubuntu recognises it as a remote control, so I've had to blacklist *mceusb* module. I've also installed *pcscd* and *pcsc-tools* and smart card reading is working fine.

IMHO, the problem arises because Ubuntu isn't loading any appropriated drivers to manage SD or MMC cards, at least *lsmod* doesn't output anything related to *tifm_core*, *tifm_7xx1*, *tifm_sd*, *mmc_core* or *mmc_block*. Another clue could be this syslog entry just after I plugged a microSD. Obviously something is going wrong:

```
Oct 17 23:37:09 altair pcscd: ccid_usb.c:1026:ControlUSB() control failed (1/3): -9 Success
Oct 17 23:37:10 altair pcscd: ifdhandler.c:102:IFDHCreateChannelByName() failed
Oct 17 23:37:10 altair pcscd: readerfactory.c:965:RFInitializeReader() Open Port 0x200001 Failed (usb:0bda/0161:libudev:1:/dev/bus/usb/001/003)
Oct 17 23:37:10 altair pcscd: readerfactory.c:275:RFAddReader() MSI StarReader SMART [Bulk-In, Bulk-Out, Interface] (20070818000000000) init failed.
```




_Just for the records_:


**lsusb**

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0161 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 003: ID 046d:c52e Logitech, Inc.
``` 



**lsmod**

```
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
xt_limit               12711  12 
xt_tcpudp              12603  23 
snd_hda_codec_hdmi     32474  5 
xt_addrtype            12713  4 
snd_hda_codec_realtek   224173  1 
xt_state               12578  14 
nvidia              12336440  50 
joydev                 17693  0 
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
usbhid                 47199  0 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
snd_pcm                97188  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
hid                    99559  1 usbhid
uas                    18180  0 
rt2800pci              18715  0 
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
rt2800lib              58925  1 rt2800pci
snd_seq_midi           13324  0 
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55279  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
iptable_filter         12810  1 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              27473  1 iptable_filter
x_tables               29846  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
i915                  473298  1 
cfg80211              205544  2 rt2x00lib,mac80211
snd                    78855  22 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
drm                   241921  2 i915,drm_kms_helper
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
r8169                  62099  0 
psmouse                97443  0 
eeprom_93cx6           12725  1 rt2800pci
mac_hid                13253  0 
video                  19596  1 i915
mei                    41616  0 
serio_raw              13211  0 
w83627ehf              38805  0 
hwmon_vid              12827  1 w83627ehf
coretemp               13525  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
```



**lshw**

```
     *-pci
          descripción: Host bridge
          producto: 2nd Generation Core Processor Family DRAM Controller
          fabricante: Intel Corporation
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 09
          anchura: 32 bits
          reloj: 33MHz
          configuración: driver=agpgart-intel
          recursos: irq:0
        *-pci:0
             descripción: PCI bridge
             producto: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             fabricante: Intel Corporation
             id físico: 1
             información del bus: pci@0000:00:01.0
             versión: 09
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pm msi pciexpress normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:40 ioport:e000(size=4096) memoria:f4000000-f60fffff ioport:e0000000(size=201326592)
           *-display
                descripción: VGA compatible controller
                producto: GF106 [GeForce GTS 450]
                fabricante: NVIDIA Corporation
                id físico: 0
                información del bus: pci@0000:01:00.0
                versión: a1
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress vga_controller bus_master cap_list rom
                configuración: driver=nvidia latency=0
                recursos: irq:16 memoria:f4000000-f4ffffff memoria:e0000000-e7ffffff memoria:e8000000-e9ffffff ioport:e000(size=128) memoria:f6000000-f607ffff
           *-multimedia
                descripción: Audio device
                producto: GF106 High Definition Audio Controller
                fabricante: NVIDIA Corporation
                id físico: 0.1
                información del bus: pci@0000:01:00.1
                versión: a1
                anchura: 32 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list
                configuración: driver=snd_hda_intel latency=0
                recursos: irq:17 memoria:f6080000-f6083fff
        *-display
             descripción: Display controller
             producto: 2nd Generation Core Processor Family Integrated Graphics Controller
             fabricante: Intel Corporation
             id físico: 2
             información del bus: pci@0000:00:02.0
             versión: 09
             anchura: 64 bits
             reloj: 33MHz
             capacidades: msi pm bus_master cap_list
             configuración: driver=i915 latency=0
             recursos: irq:48 memoria:f6400000-f67fffff memoria:d0000000-dfffffff ioport:f000(size=64)
        *-communication
             descripción: Communication controller
             producto: 6 Series/C200 Series Chipset Family MEI Controller #1
             fabricante: Intel Corporation
             id físico: 16
             información del bus: pci@0000:00:16.0
             versión: 04
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi bus_master cap_list
             configuración: driver=mei latency=0
             recursos: irq:46 memoria:f6a0b000-f6a0b00f
        *-usb:0
             descripción: USB controller
             producto: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             fabricante: Intel Corporation
             id físico: 1a
             información del bus: pci@0000:00:1a.0
             versión: 05
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci_hcd latency=0
             recursos: irq:16 memoria:f6a08000-f6a083ff
        *-multimedia
             descripción: Audio device
             producto: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             fabricante: Intel Corporation
             id físico: 1b
             información del bus: pci@0000:00:1b.0
             versión: 05
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuración: driver=snd_hda_intel latency=0
             recursos: irq:49 memoria:f6a00000-f6a03fff
        *-pci:1
             descripción: PCI bridge
             producto: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             fabricante: Intel Corporation
             id físico: 1c
             información del bus: pci@0000:00:1c.0
             versión: b5
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:41 ioport:2000(size=4096) memoria:cfb00000-cfcfffff ioport:cfd00000(size=2097152)
        *-pci:2
             descripción: PCI bridge
             producto: 82801 PCI Bridge
             fabricante: Intel Corporation
             id físico: 1c.4
             información del bus: pci@0000:00:1c.4
             versión: b5
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm subtractive_decode bus_master cap_list
             recursos: memoria:f6900000-f69fffff
           *-pci
                descripción: PCI bridge
                producto: ASM1083/1085 PCIe to PCI Bridge
                fabricante: ASMedia Technology Inc.
                id físico: 0
                información del bus: pci@0000:03:00.0
                versión: 01
                anchura: 32 bits
                reloj: 33MHz
                capacidades: pci subtractive_decode bus_master cap_list
                recursos: memoria:f6900000-f69fffff
              *-network
                   descripción: Interfaz inalámbrica
                   producto: RT3062 Wireless 802.11n 2T/2R
                   fabricante: Ralink corp.
                   id físico: 0
                   información del bus: pci@0000:04:00.0
                   nombre lógico: wlan0
                   versión: 00
                   serie: 00:22:f7:29:25:e7
                   anchura: 32 bits
                   reloj: 33MHz
                   capacidades: pm bus_master cap_list ethernet physical wireless
                   configuración: broadcast=yes driver=rt2800pci driverversion=3.2.0-32-generic firmware=0.34 ip=192.168.2.4 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
                   recursos: irq:16 memoria:f6900000-f690ffff
        *-pci:3
             descripción: PCI bridge
             producto: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             fabricante: Intel Corporation
             id físico: 1c.5
             información del bus: pci@0000:00:1c.5
             versión: b5
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:42 ioport:d000(size=4096) ioport:ec100000(size=1048576)
           *-network
                descripción: Ethernet interface
                producto: RTL8111/8168B PCI Express Gigabit Ethernet controller
                fabricante: Realtek Semiconductor Co., Ltd.
                id físico: 0
                información del bus: pci@0000:05:00.0
                nombre lógico: eth0
                versión: 06
                serie: 00:25:22:c3:00:dc
                tamaño: 10Mbit/s
                capacidad: 1Gbit/s
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                recursos: irq:47 ioport:d000(size=256) memoria:ec104000-ec104fff memoria:ec100000-ec103fff
        *-pci:4
             descripción: PCI bridge
             producto: 6 Series/C200 Series Chipset Family PCI Express Root Port 7
             fabricante: Intel Corporation
             id físico: 1c.6
             información del bus: pci@0000:00:1c.6
             versión: b5
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:43 memoria:f6800000-f68fffff
           *-usb
                descripción: USB controller
                producto: EJ168 USB 3.0 Host Controller
                fabricante: Etron Technology, Inc.
                id físico: 0
                información del bus: pci@0000:06:00.0
                versión: 01
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress xhci bus_master cap_list
                configuración: driver=xhci_hcd latency=0
                recursos: irq:45 memoria:f6800000-f6807fff
        *-usb:1
             descripción: USB controller
             producto: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             fabricante: Intel Corporation
             id físico: 1d
             información del bus: pci@0000:00:1d.0
             versión: 05
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci_hcd latency=0
             recursos: irq:23 memoria:f6a07000-f6a073ff
        *-isa
             descripción: ISA bridge
             producto: Z68 Express Chipset Family LPC Controller
             fabricante: Intel Corporation
             id físico: 1f
             información del bus: pci@0000:00:1f.0
             versión: 05
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa bus_master cap_list
             configuración: latency=0
        *-storage
             descripción: SATA controller
             producto: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             fabricante: Intel Corporation
             id físico: 1f.2
             información del bus: pci@0000:00:1f.2
             nombre lógico: scsi0
             nombre lógico: scsi2
             versión: 05
             anchura: 32 bits
             reloj: 66MHz
             capacidades: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuración: driver=ahci latency=0
             recursos: irq:44 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memoria:f6a06000-f6a067ff
           *-disk
                descripción: ATA Disk
                producto: WDC WD5000AAKX-0
                fabricante: Western Digital
                id físico: 0
                información del bus: scsi@0:0.0.0
                nombre lógico: /dev/sda
                versión: 15.0
                serie: WD-WCAYUH644811
                tamaño: 465GiB (500GB)
                capacidades: partitioned partitioned:dos
                configuración: ansiversion=5 signature=000e583c
              *-volume
                   descripción: Linux LVM Physical Volume partition
                   id físico: 1
                   información del bus: scsi@0:0.0.0,1
                   nombre lógico: /dev/sda1
                   serie: q24tFj-QxsH-77Jx-xrIg-S4mk-Qw3I-09CqDi
                   tamaño: 372GiB
                   capacidad: 372GiB
                   capacidades: primary bootable multi lvm2
           *-cdrom
                descripción: DVD-RAM writer
                producto: DVDRAM GH22NS50
                fabricante: HL-DT-ST
                id físico: 1
                información del bus: scsi@2:0.0.0
                nombre lógico: /dev/cdrom
                nombre lógico: /dev/cdrw
                nombre lógico: /dev/dvd
                nombre lógico: /dev/dvdrw
                nombre lógico: /dev/sr0
                versión: TN04
                capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuración: ansiversion=5 status=nodisc
        *-serial NO RECLAMADO
             descripción: SMBus
             producto: 6 Series/C200 Series Chipset Family SMBus Controller
             fabricante: Intel Corporation
             id físico: 1f.3
             información del bus: pci@0000:00:1f.3
             versión: 05
             anchura: 64 bits
             reloj: 33MHz
             configuración: latency=0
             recursos: memoria:f6a05000-f6a050ff ioport:f040(size=32)
```




Thanks in advance!

---

### Post by Jason Pierce on 2012-10-18
I've forgot to mention **lspci**:


```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GTS 450] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF106 High Definition Audio Controller (rev a1)
03:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
04:00.0 Network controller: Ralink corp. RT3062 Wireless 802.11n 2T/2R
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
06:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
```

---

