---
title: "not sure bout the graphic driver"
date: 2008-06-30
forum: Hardware
---

### Post by m3t3ors on 2008-06-30
just installed ubuntu studio on my laptop but im not too sure on the graphic driver. it says its a mobile 945gm but im not sure the drivers are right
anyone help me out

---

### Post by overdrank on 2008-06-30
> **m3t3ors said:**
> just installed ubuntu studio on my laptop but im not too sure on the graphic driver. it says its a mobile 945gm but im not sure the drivers are right
anyone help me out

Hi and intel graphics are usually supported out of the box. What issues are you having?

---

### Post by m3t3ors on 2008-06-30
i was thinking that my graphic card driver was wrong and thats why im having trouble with running games in wine

[http://ubuntuforums.org/showthread.php?t=844228](http://ubuntuforums.org/showthread.php?t=844228)
my other post

---

### Post by ukripper on 2008-06-30
> **m3t3ors said:**
> i was thinking that my graphic card driver was wrong and thats why im having trouble with running games in wine

[http://ubuntuforums.org/showthread.php?t=844228](http://ubuntuforums.org/showthread.php?t=844228)
my other post

Can you post output of the following:
```
lspci
```

---

### Post by overdrank on 2008-06-30
> **m3t3ors said:**
> i was thinking that my graphic card driver was wrong and thats why im having trouble with running games in wine

[http://ubuntuforums.org/showthread.php?t=844228](http://ubuntuforums.org/showthread.php?t=844228)
my other post

Hi and I do not use wine but as I understand it the intel graphics do lack in the 3d acceleration for games. 
**ukripper** maybe able to assist, also How much memory is in the system? because the intel graphics will share that memory and may cause issue :(

---

### Post by m3t3ors on 2008-06-30
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
john@john-laptop:~$

---

### Post by m3t3ors on 2008-07-01
any help guys??

---

### Post by ukripper on 2008-07-01
> **m3t3ors said:**
> any help guys??

Can you post output of the following:
```
lsmod
```

```
sudo lshw
```

```
fglrxinfo
```

---

### Post by m3t3ors on 2008-07-01
Module                  Size  Used by
snd_rtctimer            4384  0
arc4                    2944  2
ecb                     4480  2
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  1
nls_cp437               6784  1
isofs                  36284  1
udf                    85252  0
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
i915                   25472  2
drm                    81044  3 i915
ipv6                  269088  10
cpufreq_stats           7360  0
cpufreq_ondemand        9228  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0
cpufreq_powersave       2688  0
cpufreq_userspace       5408  0
pcc_acpi               13184  0
sony_acpi               6284  0
tc1100_wmi              8068  0
dev_acpi               12292  0
sbs                    15652  0
container               5248  0
asus_acpi              17308  0
backlight               7040  1 asus_acpi
ac                      6020  0
dock                   10268  0
video                  16388  0
button                  8720  0
battery                10756  0
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
sbp2                   23812  0
parport_pc             36388  0
lp                     12452  0
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  1
snd_hda_intel          21912  1
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
usbhid                 26592  0
pcmcia                 39212  0
joydev                 10816  0
hid                    27392  1 usbhid
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw3945               118816  1
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
yenta_socket           27532  1
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
serio_raw               7940  0
pcspkr                  4224  0
psmouse                38920  0
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
intel_agp              26140  1
agpgart                35400  3 drm,intel_agp
af_packet              23816  8
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
evdev                  11008  5
tsdev                   8768  0
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  1
cdrom                  37664  1 sr_mod
sd_mod                 23428  3
generic                 5124  0 [permanent]
ata_generic             9092  0
ohci1394               36528  0
ieee1394              299448  2 sbp2,ohci1394
b44                    28044  0
mii                     6528  1 b44
ata_piix               15492  3
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               34188  0
uhci_hcd               25360  0
usbcore               134280  4 usbhid,ehci_hcd,uhci_hcd
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability
john@john-laptop:~$

---

### Post by m3t3ors on 2008-07-01
john-laptop
    description: Portable Computer
    product: Latitude D520
    vendor: Dell Inc.
    serial: H3HMV2J
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-3300-1048-804D-C8C04F56324A
  *-core
       description: Motherboard
       product: 0PF493
       vendor: Dell Inc.
       physical id: 0
       serial: .H3HMV2J.CN486437162979.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A05 (04/02/2007)
          size: 64KB
          capacity: 512KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: Microprocessor
          size: 1733MHz
          capacity: 2160MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up pni monitor tm2 xtpr
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MB
             capacity: 1MB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM DDR Synchronous [empty]
             physical id: 0
             slot: DIMM_B
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: HYMP564S64CP6-C4
             vendor: AD00000000000000
             physical id: 1
             serial: 00005129
             slot: DIMM_A
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:eff00000-eff7ffff ioport:eff8-efff iomemory:d0000000-dfffffff iomemory:efec0000-efefffff irq:16
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:eff80000-efffffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:efebc000-efebffff irq:20
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0c:00.0
                logical name: eth1
                version: 02
                serial: 00:19:d2:bc:85:f2
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.2.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
                resources: iomemory:efdff000-efdfffff irq:17
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf80-bf9f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-17-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf60-bf7f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-17-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf40-bf5f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-17-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB Mouse
                   physical id: 1
                   bus info: usb@3:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf20-bf3f irq:22
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-17-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ffa80000-ffa803ff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-17-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: USB hub
                   physical id: 2
                   bus info: usb@5:2
                   version: 50.18
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=2mA slots=4 speed=480.0MB/s
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 02
                serial: 00:19:b9:54:33:92
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
                resources: iomemory:efcfe000-efcfffff irq:17
           *-pcmcia
                description: CardBus bridge
                product: Cardbus bridge
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@02:01.0
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:efc00000-efc00fff irq:18
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1.4
                bus info: pci@02:01.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64
                resources: iomemory:efcfd000-efcfdfff iomemory:efcfc800-efcfcfff irq:18
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:bfa0-bfaf irq:17
           *-disk
                description: SCSI Disk
                product: TOSHIBA MK8034GS
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AH30
                serial: 27LGTQ2HT
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 73GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1443MB
                   capacity: 1443MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1443MB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW TS-L632D
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE04
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:10c0-10df irq:11
  *-battery
       product: DELL HD94172
       vendor: Panasonic
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 51000mWh
       configuration: voltage=11.1V
john@john-laptop:~$

---

### Post by m3t3ors on 2008-07-01
john@john-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
Make sure you have the 'restricted' component enabled
bash: fglrxinfo: command not found
john@john-laptop:~$

---

### Post by ukripper on 2008-07-01
> **m3t3ors said:**
> john@john-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
Make sure you have the 'restricted' component enabled
bash: fglrxinfo: command not found
john@john-laptop:~$

I think your driver chipset is blacklisted, it was in gutsy for sure.

If you are not getting compiz then in terminal do following:
```
sudo SKIP_CHECKS=1 compiz
```

and then right click on your desktop and see if you can enable normal effects from there. Otherwise it would mean your chipset drivers don't support 3d and can't run 3d games.

---

### Post by m3t3ors on 2008-07-01
john@john-laptop:~$ sudo SKIP_CHECKS=1 compiz
Password:
sudo: SKIP_CHECKS=1: command not found
john@john-laptop:~$

---

### Post by ukripper on 2008-07-01
> **m3t3ors said:**
> john@john-laptop:~$ sudo SKIP_CHECKS=1 compiz
Password:
sudo: SKIP_CHECKS=1: command not found
john@john-laptop:~$

Try this instead:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by m3t3ors on 2008-07-01
thanx for your help so far. if i right click on gesktop theres no place to enable anything
but i can play torcs car racing with no problem

---

### Post by ukripper on 2008-07-01
> **m3t3ors said:**
> thanx for your help so far. if i right click on gesktop theres no place to enable anything
but i can play torcs car racing with no problem

Right click Desktop then go click on **Visual Effects-**->Then check** Normal**

---

### Post by m3t3ors on 2008-07-01
when i right click on desktop i just have the usual options
new folder , keep alligned etc
no sign of visual effects?

---

### Post by ukripper on 2008-07-02
> **m3t3ors said:**
> when i right click on desktop i just have the usual options
new folder , keep alligned etc
no sign of visual effects?

You don't have to click desktop folder. By desktop i mean the the wallpaper. Right click on your wallpaper --> then visual effects.

Like in windows you do when you right click you get options to change your walpaper. This is the samething you need to do

just right click on your wallpaper-->visual effects and select Normal there see below attached screenshot.

---

### Post by m3t3ors on 2008-07-02
i understand what your saying, but i dont see any visual effects tab

all i see is
create folder
create launcher
create document
clean up by name
keep allinged
change desktop background
theres no visual effects in any of them tabs either?

---

### Post by overdrank on 2008-07-02
> **m3t3ors said:**
> i understand what your saying, but i dont see any visual effects tab

all i see is
create folder
create launcher
create document
clean up by name
keep allinged
change desktop background
theres no visual effects in any of them tabs either?

What version of ubuntu studio are you using?

---

### Post by m3t3ors on 2008-07-02
in the file system it says
ersion: GnuPG v1.4.3 (GNU/Linux)
unsure if this is what you mean
on the dvd it says
DISKNAME  Ubuntu 7.04 "Feisty Fawn" - Release i386

---

### Post by overdrank on 2008-07-02
> **m3t3ors said:**
> in the file system it says
ersion: GnuPG v1.4.3 (GNU/Linux)
unsure if this is what you mean
on the dvd it says
DISKNAME  Ubuntu 7.04 "Feisty Fawn" - Release i386

Ok the reason I was asking is that is why you do not see the screen that 
ukripper is asking. The intel drivers worked well for me in feisty as well as gutsy. As I stated before I do not use wine and the intel drivers are really not equipped for gaming so you may see how much memory is shared with the intel graphics and see if you can increase it. Good luck!

---

### Post by m3t3ors on 2008-07-02
at the minute im just upgrading to see if that helps in anyway?
but thanks for your help

---

### Post by ukripper on 2008-07-02
> **m3t3ors said:**
> at the minute im just upgrading to see if that helps in anyway?
but thanks for your help

As overdrank stated, built in intel cards are not meant to be for gamings. You might want to consider using on your desktop  Ati or nvidia cards

---

### Post by m3t3ors on 2008-07-02
is it easy to change a card on laptops or do you recomend setting up a pc for linux

---

### Post by ukripper on 2008-07-02
> **m3t3ors said:**
> is it easy to change a card on laptops or do you recomend setting up a pc for linux

On laptop you won't be able to change graphics card as it is soldered in laptop's base/motherboard.

Your best bet is to setup ubuntu on desktop/PC with decent graphics card which can handle games Ati or Nvidia.

---

