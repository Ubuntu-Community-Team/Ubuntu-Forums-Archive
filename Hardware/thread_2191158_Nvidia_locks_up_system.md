---
title: "Nvidia locks up system"
date: 2013-12-01
forum: Hardware
---

### Post by chris1379 on 2013-12-01
I just installed Mint 13 Cinnamon and keep getting hard lockups. The error in syslog is ```
NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
``` I'm using the onboard NVS 210 / Geforce 6150 video with the Nvidia 304 driver. I wanted to try the 295.20 driver but I couldn't get it to run even when it installed with no errors. The 173 driver sets my CRT monitor at 60 HZ and Nvidia settings don't work. I've tried every fix that I've found with Google and so far nothing has worked.

---

### Post by chris1379 on 2013-12-01
Wow, with 160 views I can't be the only one with this problem. So far I have found one thing that helps. My video uses shared system memory which is DDR2-533. I should be using DDR2-800 for this chip. I slowed the memory down to 200 MHz (DDR2-400 speed) and I have had some flickering and hesitation but no hard lockups so far. The syslog now shows ```
NVRM: Xid (0000:00:05): 9, Channel 00000020 Instance 00000000 Intr 00100000
```.

---

### Post by chris1379 on 2013-12-02
Looks like it still is locking up so I'm writing this from XP. I even tried the recommended Nvidia-173 driver. The one thing I haven't tried yet is removing the WinTV HVR-1600 card. It never gave me a problem in XP with the onboard video but Windows won't boot with it and a PCIe Nvidia card. I had a custom BIOS to fix that on the original motherboard. I may also try Ubuntu 12.04 but it uses the same drivers.

---

### Post by necromonger on 2013-12-02
go to driver manager and tell me what it says. also some system specs would be nice to see.

---

### Post by chris1379 on 2013-12-03
I don't see a driver manager but this is from hardware info.
Computer
********


Summary
-------

-Computer-
Processor        : 2x AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
Memory        : 1997MB (501MB used)
Operating System        : Linux Mint 13 Maya
Date/Time        : Tue 03 Dec 2013 02:01:43 AM EST
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : Quadro NVS 210S / GeForce 6150LE/integrated/SSE2/3DNOW!
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA NVidia
Audio Adapter        : CX23418 - CX18-0
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Logitech USB Trackball
 HDA NVidia Line
 HDA NVidia Front Mic
 HDA NVidia Rear Mic
 HDA NVidia Front Headphone
 HDA NVidia Line-Out Side
 HDA NVidia Line-Out CLFE
 HDA NVidia Line-Out Surround
 HDA NVidia Line-Out Front
-Printers-
No printers found
-SCSI Disks-
ATA ST3320620AS
ATA ST3500320AS
ATA ST3120814A
ATA ST3120026A
TSSTcorp CDDVDW SH-S222L

Kernel Modules
--------------

-Loaded Modules-
xt_conntrack        : Xtables: connection tracking state match
iptable_filter        : iptables filter table
ipt_MASQUERADE        : Xtables: automatic-address SNAT
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_conntrack
nf_defrag_ipv4
ip_tables        : IPv4 packet filter
x_tables        : {ip,ip6,arp,eb}_tables backend module
vesafb
rfcomm        : Bluetooth RFCOMM ver 1.11
bnep        : Bluetooth BNEP ver 1.3
bluetooth        : Bluetooth Core ver 2.16
binfmt_misc
snd_hda_codec_realtek        : Realtek HD-audio codec
arc4        : ARC4 Cipher Algorithm
cx18_alsa        : CX23418 ALSA Interface
mxl5005s        : MaxLinear MXL5005S silicon tuner driver
s5h1409        : Samsung S5H1409 QAM-B/ATSC Demodulator driver
tuner_simple        : Simple 4-control-bytes style tuner driver
tuner_types        : Simple tuner device type database
cs5345        : i2c device driver for cs5345 Audio ADC
tuner        : device driver for various TV and TV+FM radio tuners
ppdev
rt2500pci        : Ralink RT2500 PCI &amp; PCMCIA Wireless LAN driver.
rt2x00pci        : rt2x00 pci library
rt2x00lib        : rt2x00 library
mac80211        : IEEE 802.11 subsystem
snd_hda_intel        : Intel HDA driver
snd_hda_codec        : HDA codec core
snd_hwdep        : Hardware dependent layer
snd_pcm        : Midlevel PCM code for ALSA.
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi        : Midlevel RawMidi code for ALSA.
nvidia
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
snd_seq        : Advanced Linux Sound Architecture sequencer.
cx18        : CX23418 driver
dvb_core        : DVB Core Driver
serio_raw        : Raw serio driver
cfg80211        : wireless configuration support
eeprom_93cx6        : EEPROM 93cx6 chip driver
cx2341x        : cx23415/6/8 driver
i2c_algo_bit        : I2C-Bus bit-banging algorithm
videobuf_vmalloc        : helper module to manage video4linux vmalloc buffers
videobuf_core        : helper module to manage video4linux buffers
tveeprom        : i2c Hauppauge eeprom decoder driver
v4l2_common        : misc helper functions for v4l2 device drivers
videodev        : Device registrar for Video4Linux drivers v2
k8temp        : AMD K8 core temperature monitor
snd_timer        : ALSA timer interface
snd_seq_device        : ALSA sequencer device management
snd        : Advanced Linux Sound Architecture driver for soundcards.
parport_pc        : PC-style parallel port driver
soundcore        : Core sound module
snd_page_alloc        : Memory allocator for ALSA system.
mac_hid
nv_tco        : TCO timer driver for NV chipsets
i2c_nforce2        : nForce2/3/4/5xx SMBus driver
lp
parport
firewire_ohci        : Driver for PCI OHCI IEEE1394 controllers
firewire_core        : Core IEEE1394 transaction logic
usbhid        : USB HID core driver
hid
floppy
crc_itu_t        : CRC ITU-T V.41 calculations
forcedeth        : Reverse Engineered nForce ethernet driver
pata_amd        : low-level driver for AMD and Nvidia PATA IDE
sata_nv        : low-level driver for NVIDIA nForce SATA controller

Display
-------

-Display-
Resolution        : 1024x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.11.3
-Monitors-
Monitor 0        : 1024x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
NV-CONTROL
NV-GLX
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
-OpenGL-
Vendor        : NVIDIA Corporation
Renderer        : Quadro NVS 210S / GeForce 6150LE/integrated/SSE2/3DNOW!
Version        : 2.1.2 NVIDIA 304.88
Direct Rendering        : Yes

Devices
*******


Processor
---------

-Processors-
AMD Athlon(tm) 64 X2 Dual Core Processor 6000+        : 3000.00MHz
AMD Athlon(tm) 64 X2 Dual Core Processor 6000+        : 3000.00MHz

Memory
------

-Memory-
Total Memory        : 1997004 kB
Free Memory        : 1104252 kB
Buffers        : 79588 kB
Cached        : 391404 kB
Cached Swap        : 0 kB
Active        : 435008 kB
Inactive        : 341692 kB
Active(anon)        : 306560 kB
Inactive(anon)        : 1408 kB
Active(file)        : 128448 kB
Inactive(file)        : 340284 kB
Unevictable        : 0 kB
Mlocked        : 0 kB
High Memory        : 1261512 kB
Free High Memory        : 543924 kB
Low Memory        : 735492 kB
Free Low Memory        : 560328 kB
Virtual Memory        : 2096444 kB
Free Virtual Memory        : 2096444 kB
Dirty        : 272 kB
Writeback        : 0 kB
AnonPages        : 305668 kB
Mapped        : 103284 kB
Shmem        : 2264 kB
Slab        : 42576 kB
SReclaimable        : 28160 kB
SUnreclaim        : 14416 kB
KernelStack        : 2216 kB
PageTables        : 4960 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 3094944 kB
Committed_AS        : 1422416 kB
VmallocTotal        : 262144 kB
VmallocUsed        : 127512 kB
VmallocChunk        : 123896 kB
HardwareCorrupted        : 0 kB
AnonHugePages        : 0 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 4096 kB
DirectMap4k        : 81912 kB
DirectMap4M        : 688128 kB

PCI Devices
-----------

-PCI Devices-
RAM memory        : NVIDIA Corporation C51 Host Bridge (rev a2)
RAM memory        : NVIDIA Corporation C51 Memory Controller 0 (rev a2)
RAM memory        : NVIDIA Corporation C51 Memory Controller 1 (rev a2)
RAM memory        : NVIDIA Corporation C51 Memory Controller 5 (rev a2)
RAM memory        : NVIDIA Corporation C51 Memory Controller 4 (rev a2)
RAM memory        : NVIDIA Corporation C51 Host Bridge (rev a2)
RAM memory        : NVIDIA Corporation C51 Memory Controller 3 (rev a2)
RAM memory        : NVIDIA Corporation C51 Memory Controller 2 (rev a2)
VGA compatible controller        : NVIDIA Corporation C51 [Quadro NVS 210S/GeForce 6150LE] (rev a2) (prog-if 00 [VGA controller])
RAM memory        : NVIDIA Corporation MCP51 Host Bridge (rev a2)
ISA bridge        : NVIDIA Corporation MCP51 LPC Bridge (rev a3)
SMBus        : NVIDIA Corporation MCP51 SMBus (rev a3)
RAM memory        : NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
USB controller        : NVIDIA Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
USB controller        : NVIDIA Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
IDE interface        : NVIDIA Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
IDE interface        : NVIDIA Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
IDE interface        : NVIDIA Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
PCI bridge        : NVIDIA Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
Audio device        : NVIDIA Corporation MCP51 High Definition Audio (rev a2)
Bridge        : NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
Host bridge        : Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Host bridge        : Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
Host bridge        : Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
Host bridge        : Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
Multimedia video controller        : Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
Network controller        : Ralink corp. RT2500 Wireless 802.11bg (rev 01)
FireWire (IEEE 1394)        : Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])

lspci -v
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [Quadro NVS 210S/GeForce 6150LE] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device d000
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: nvidia
    Kernel modules: nvidia_304, nvidia_173_updates, nvidia, nouveau, nvidiaf

---

### Post by chris1379 on 2013-12-08
Installed Ubuntu 12.04 32-bit and it's working fine. I also tried Mint 13 64-bit and it locks up just like 32-bit. I even tried updating the kernel and x-server versions with no luck. What could be different between Ubuntu and Mint that causes the lockups? I also found that Glmark2 has much higher benchmarks in Ubuntu.

---

