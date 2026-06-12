---
title: "Belkin Model f7d4101 V1 play wireless usb adapter"
date: 2011-10-09
forum: Hardware
---

### Post by Crimminalhaze on 2011-10-09
ok the windows wireless driver says its present  but can't pick up my router wen i do iwconfig it says no extension ill post the other commands below

============ lspci ============
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 04)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation 82915G Integrated Graphics Controller [8086:2782] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
    Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
    Kernel modules: i2c-i801
03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 03)
    Kernel driver in use: e100
    Kernel modules: e100

============ lsusb ============
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:615a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

============ lsmod ============
Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
fbcon                  35102  71 
snd_pcm_oss            35308  0 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
snd_mixer_oss          13746  1 snd_pcm_oss
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
vga16fb                11385  0 
snd_seq_dummy           1338  0 
vgastate                8961  1 vga16fb
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i915                  288963  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29329  1 i915
snd_timer              19098  2 snd_pcm,snd_seq
drm                   163651  4 i915,drm_kms_helper
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit            5028  1 i915
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
video                  17375  1 i915
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24375  2 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
dell_wmi                1793  0 
ppdev                   5259  0 
lp                      7028  0 
ndiswrapper           184677  0 
parport_pc             25962  1 
dcdbas                  5422  0 
parport                32635  3 ppdev,lp,parport_pc
usbhid                 36110  0 
hid                    67288  1 usbhid
e100                   28211  0 
mii                     4381  1 e100

============ dmesg-firmware ============
[    6.291602] intel_rng: don't want to disable this in firmware setup, and if

============ kernel version ============
2.6.32-34-generic

============ ifconfig ============
eth0      Link encap:Ethernet  HWaddr 00:13:20:0e:2e:27  
          inet addr:74.78.164.3  Bcast:74.78.191.255  Mask:255.255.224.0
          inet6 addr: fe80::213:20ff:fe0e:2e27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6925597 (6.9 MB)  TX bytes:2363415 (2.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


============ iwconfig ============
lo        no wireless extensions.

eth0      no wireless extensions.

---

