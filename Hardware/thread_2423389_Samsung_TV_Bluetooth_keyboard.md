---
title: "Samsung TV Bluetooth keyboard"
date: 2019-07-22
forum: Hardware
---

### Post by Alexander_Lilljebj on 2019-07-22
Hi,
I'm trying to connect my Samsung VG-KBD1500 to my media PC running Lubuntu 18.10. I am however unsuccessful. I can pair with both blueman and bluetoothctl and sometimes connect, but neither the keyboard or integrated mouse pad works. A few times blueman has given me a authorization popup which I'm unable to click ok on, it doesn't matter which option I choose.

```

media@media-lubuntu:~$ lsusb                                                        
Bus 002 Device 004: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2001:3318 D-Link Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

```

media@media-lubuntu:~$ dmesg | egrep -i 'blue|firm'                                 
[    4.050420] Bluetooth: Core ver 2.22                                           
[    4.050443] Bluetooth: HCI device and connection manager initialized             
[    4.050447] Bluetooth: HCI socket layer initialized                              
[    4.050449] Bluetooth: L2CAP socket layer initialized                            
[    4.050454] Bluetooth: SCO socket layer initialized                             
[    4.058579] Bluetooth: HIDP (Human Interface Emulation) ver 1.2                  
[    4.058584] Bluetooth: HIDP socket layer initialized                             
[    6.513474] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                         
[    6.513476] Bluetooth: BNEP filters: protocol multicast                          
[    6.513480] Bluetooth: BNEP socket layer initialized                             
[    6.696127] Bluetooth: RFCOMM TTY layer initialized                              
[    6.696134] Bluetooth: RFCOMM socket layer initialized                           
[    6.696138] Bluetooth: RFCOMM ver 1.11                                           
[   70.035258] input: Samsung Wireless Keyboard Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:70/0005:04E8:2080.0002/input/input18
[   70.035362] input: Samsung Wireless Keyboard Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:70/0005:04E8:2080.0002/input/input19
[   70.035476] input: Samsung Wireless Keyboard Consumer Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:70/0005:04E8:2080.0002/input/input20
[   70.035549] input: Samsung Wireless Keyboard System Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:70/0005:04E8:2080.0002/input/input21
[   70.035622] hid-generic 0005:04E8:2080.0002: input,hidraw1: BLUETOOTH HID v19.01 Keyboard [Samsung Wireless Keyboard] on 00:1a:7d:da:71:05
[   94.594346] input: Samsung Wireless Keyboard Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:69/0005:04E8:2080.0003/input/input22
[   94.594608] input: Samsung Wireless Keyboard Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:69/0005:04E8:2080.0003/input/input23
[   94.594740] input: Samsung Wireless Keyboard Consumer Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:69/0005:04E8:2080.0003/input/input24
[   94.594822] input: Samsung Wireless Keyboard System Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:69/0005:04E8:2080.0003/input/input25
[   94.594904] hid-generic 0005:04E8:2080.0003: input,hidraw1: BLUETOOTH HID v19.01 Keyboard [Samsung Wireless Keyboard] on 00:1a:7d:da:71:05
[  118.147009] input: Samsung Wireless Keyboard Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:70/0005:04E8:2080.0004/input/input26
[  118.147289] input: Samsung Wireless Keyboard Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:70/0005:04E8:2080.0004/input/input27
[  118.147424] input: Samsung Wireless Keyboard Consumer Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:70/0005:04E8:2080.0004/input/input28
[  118.149644] input: Samsung Wireless Keyboard System Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:70/0005:04E8:2080.0004/input/input29
[  118.149749] hid-generic 0005:04E8:2080.0004: input,hidraw1: BLUETOOTH HID v19.01 Keyboard [Samsung Wireless Keyboard] on 00:1a:7d:da:71:05
[  142.979863] input: Samsung Wireless Keyboard Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/bluetooth/hci0/hci0:69/0005:04E8:2080.0005/input/input30


```

I'm unsure what other commands are prudent to supply. 
Any help would be much appreciated!
Thanks!

Edit: tried everything I can find by googling, haven't helped. Can connect via bluetoothctl but gets disconnected directly. 

[ATTACH=CONFIG]283666[/ATTACH]

More output:

```

hci0:Type: Primary  Bus: USB
BD Address: 00:1A:7D:DA:71:05  ACL MTU: 310:10  SCO MTU: 64:8
UP RUNNING PSCAN ISCAN 
RX bytes:17864 acl:90 sco:0 events:691 errors:0
TX bytes:9155 acl:110 sco:0 commands:457 errors:0
Features: 0xff 0xff 0x8f 0xfe 0xdb 0xff 0x5b 0x87
Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
Link policy: RSWITCH HOLD SNIFF PARK 
Link mode: SLAVE ACCEPT 
Name: 'media-lubuntu'
Class: 0x3c0104
Service Classes: Rendering, Capturing, Object Transfer, Audio
Device Class: Computer, Desktop workstation
HCI Version: 4.0 (0x6)  Revision: 0x22bb
LMP Version: 4.0 (0x6)  Subversion: 0x22bb
Manufacturer: Cambridge Silicon Radio (10)


```

```

media@media-lubuntu:~$ lspci -nnk                                            00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
Subsystem: ASUSTeK Computer Inc. P8P67/P8H67 Series Motherboard [1043:844d]
Kernel driver in use: snb_uncore
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
Kernel driver in use: pcieport
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
Subsystem: ASUSTeK Computer Inc. 2nd Generation Core Processor Family Integrated Graphics Controller [1043:844d]
Kernel driver in use: i915
Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:844d]
Kernel driver in use: mei_me
Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:844d]
Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
Subsystem: ASUSTeK Computer Inc. P8H67 Series Motherboard [1043:841b]Kernel driver in use: snd_hda_intel
Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
Kernel driver in use: pcieport
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
Kernel driver in use: pcieport
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b5)
Kernel driver in use: pcieport
00:1c.7 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b5)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:844d]
Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation H67 Express Chipset LPC Controller [8086:1c4a] (rev 05)
Subsystem: ASUSTeK Computer Inc. P8H67 Series Motherboard [1043:844d]Kernel driver in use: lpc_ich
Kernel modules: lpc_ich
00:1f.2 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 0-3) [8086:1c00] (rev 05)
Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 0-3) [1043:844d]
Kernel driver in use: ata_piix
Kernel modules: pata_acpi
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:844d]
Kernel modules: i2c_i801
00:1f.5 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 4-5) [8086:1c08] (rev 05)
Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family Desktop SATA Controller (IDE mode, ports 4-5) [1043:844d]
Kernel driver in use: ata_piix
Kernel modules: pata_acpi
03:00.0 IDE interface [0101]: VIA Technologies, Inc. VT6415 PATA IDE Host Controller [1106:0415]
Subsystem: ASUSTeK Computer Inc. Motherboard [1043:838f]
Kernel driver in use: pata_via
Kernel modules: pata_via, pata_acpi
04:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
Subsystem: ASUSTeK Computer Inc. P8B WS Motherboard [1043:8488]
Kernel driver in use: xhci_hcd
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
Kernel driver in use: r8169
Kernel modules: r8169
06:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 01)


```

```

media@media-lubuntu:~$ usb-devices                                           
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.18
S:  Manufacturer=Linux 4.18.0-11-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a12 ProdID=0001 Rev=88.91
S:  Product=CSR8510 A10
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.18
S:  Manufacturer=Linux 4.18.0-11-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=0609 ProdID=031d Rev=00.00
S:  Manufacturer=SMK
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=SM005EBT
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=mceusb

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.18
S:  Manufacturer=Linux 4.18.0-11-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:04:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2001 ProdID=3318 Rev=02.00
S:  Manufacturer=D-Link Corporation
S:  Product=11ac adapter
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtl8812au

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.18
S:  Manufacturer=Linux 4.18.0-11-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:04:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


```

```

media@media-lubuntu:~$ lsmod                                                 Module                  Size  Used by
joydev                 20480  0
input_leds             16384  0
hid_generic            16384  0
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
xt_conntrack           16384  1
cmac                   16384  1
rfcomm                 77824  16
bnep                   20480  2
iptable_filter         16384  1
ipt_MASQUERADE         16384  1
iptable_nat            16384  1
nf_nat_ipv4            16384  2 ipt_MASQUERADE,iptable_nat
nf_nat                 32768  1 nf_nat_ipv4
xt_tcpudp              16384  2
nf_conntrack_ipv4      16384  5
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_mark                16384  4
xt_owner               16384  5
xt_connmark            16384  2
nf_conntrack          126976  6 xt_conntrack,nf_conntrack_ipv4,nf_nat,ipt_MASQUERADE,nf_nat_ipv4,xt_connmark
iptable_mangle         16384  1
bpfilter               16384  0
binfmt_misc            20480  1
snd_hda_codec_hdmi     49152  1
eeepc_wmi              16384  0
snd_hda_codec_realtek   106496  1
asus_wmi               28672  1 eeepc_wmi
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_hda_intel          40960  3
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
coretemp               16384  0
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
kvm_intel             208896  0
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
kvm                   622592  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
rtl8812au            1359872  0
i915                 1740800  8
ir_rc6_decoder         16384  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
serio_raw              16384  0
rc_rc6_mce             16384  0
cfg80211              663552  1 rtl8812au
mceusb                 36864  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
drm_kms_helper        172032  1 i915
btusb                  45056  0
rc_core                45056  4 mceusb,ir_rc6_decoder,rc_rc6_mce
snd_timer              32768  2 snd_seq,snd_pcm
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                20480  1 btusb
drm                   458752  9 drm_kms_helper,i915
snd                    81920  17 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
i2c_algo_bit           16384  1 i915
mei_me                 40960  0
fb_sys_fops            16384  1 drm_kms_helper
soundcore              16384  1 snd
syscopyarea            16384  1 drm_kms_helper
mei                    98304  1 mei_me
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
wmi                    24576  2 asus_wmi,wmi_bmof
video                  45056  2 asus_wmi,i915
mac_hid                16384  0
sch_fq_codel           20480  7
hidp                   24576  0
hid                   126976  2 hidp,hid_generic
bluetooth             548864  44 btrtl,hidp,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           24576  2 bluetooth
parport_pc             36864  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              24576  3 iptable_filter,iptable_nat,iptable_mangle
x_tables               40960  10 xt_conntrack,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_owner,ipt_REJECT,xt_connmark,ip_tables,iptable_mangle,xt_mark
autofs4                40960  2
btrfs                1163264  0
xor                    24576  1 btrfs
zstd_compress         159744  1 btrfs
raid6_pq              114688  1 btrfs
libcrc32c              16384  3 nf_conntrack,nf_nat,btrfs
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
gpio_ich               16384  0
psmouse               151552  0
pata_acpi              16384  0
lpc_ich                24576  0
r8169                  86016  0
mii                    16384  1 r8169
pata_via               16384  0


```

```

[bluetooth]# info E4:E0:C5:9B:FC:E7 
Device E4:E0:C5:9B:FC:E7 (public)
Name: Samsung Wireless Keyboard
Alias: Samsung Wireless Keyboard
Class: 0x000025cc
Paired: yes
Trusted: yes
Blocked: no
Connected: no
LegacyPairing: no
UUID: Human Interface Device... (00001124-0000-1000-8000-00805f9b34fb)
UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
Modalias: bluetooth:v04E8p2080d1901
RSSI: -66


```

---

### Post by Alexander_Lilljebj on 2019-07-26
Ok, so this helped a bit
"create /etc/bluetooth/input.conf with the line UserspaceHID=true."
From here: [https://www.reddit.com/r/archlinux/comments/8ywe3q/bluetooth_mouse_cannot_reconnect_after_disconnect/](https://www.reddit.com/r/archlinux/comments/8ywe3q/bluetooth_mouse_cannot_reconnect_after_disconnect/)

Now the keyboard and mouse works, but to and from.

---

