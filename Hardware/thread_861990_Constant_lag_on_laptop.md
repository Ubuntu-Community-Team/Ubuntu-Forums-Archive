---
title: "Constant lag on laptop"
date: 2008-07-17
forum: Hardware
---

### Post by Zipolite on 2008-07-17
First I'll say that I'm very new to Linux.  I have a acer aspire 5100. I use to have windows vista but i kept getting terrible lag about every 20 seconds or so when I watched videos and what not. So i had a copy of ubuntu and installed it thinking that with less system memory used the lag would go away. Well it didn't. I've looked through the web to find a fix and well alot of people have ideas but nothings worked yet. The best I found was a windows user with the same problem. [http://forum.notebookreview.com/showthread.php?t=204245](http://forum.notebookreview.com/showthread.php?t=204245) I couldn't find an update for my bios in Ubuntu, but he said that didn't fix the problem. Overclocking was the cure. It took a little bit but I found rovclock. I'm not sure what he's talking about 1800mhz mine was set at 300mhz and I changed it 400mhz. Maybe somethings wrong but I certainly have AMD Turion64 x2 1.6ghz with means I should be running at 3.2 ghz total speed I've had way slower pc's in my life and this has never happen. I'm going to include all my hardware info plus the rovclock info. Please someone help I'm gonna throw the laptop away soon if I can't fix it. The only other thing I can think of is if its in a Infinite loop. suggestions would be great.

                                 Here's my info
Kernel Modules
--------------

-Loaded Modules-
ipv6		: IPv6 protocol stack for Linux
af_packet
rfcomm		: Bluetooth RFCOMM ver 1.8
l2cap		: Bluetooth L2CAP ver 2.9
bluetooth		: Bluetooth Core ver 2.11
rfkill_input		: Input layer to RF switch connector
ppdev
powernow_k8		: AMD Athlon 64 and Opteron processor frequency driver.
cpufreq_powersave		: CPUfreq policy governor &apos;powersave&apos;
cpufreq_ondemand		: &apos;cpufreq_ondemand&apos; - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors
cpufreq_userspace		: CPUfreq policy governor &apos;userspace&apos;
cpufreq_stats		: &apos;cpufreq_stats&apos; - A driver to export cpufreq stats through sysfs filesystem
freq_table		: CPUfreq frequency table helpers
cpufreq_conservative		: &apos;cpufreq_conservative&apos; - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors optimised for use in a battery environment
sbs		: Smart Battery System ACPI interface driver
dock		: ACPI Dock Station Driver
sbshc		: ACPI SMBus HC driver
iptable_filter		: iptables filter table
ip_tables		: IPv4 packet filter
x_tables		: [ip,ip6,arp]_tables backend module
parport_pc		: PC-style parallel port driver
lp
parport
joydev		: Joystick device interfaces
pcmcia		: PCMCIA Driver Services
arc4		: ARC4 Cipher Algorithm
ecb		: ECB block cipher algorithm
blkcipher		: Generic block chaining cipher type
b43		: Broadcom B43 wireless driver
rfkill		: RF switch support
snd_hda_intel		: Intel HDA driver
mac80211		: IEEE 802.11 subsystem
snd_pcm_oss		: PCM OSS emulation for ALSA.
snd_mixer_oss		: Mixer OSS emulation for ALSA.
cfg80211		: wireless configuration support
snd_pcm		: Midlevel PCM code for ALSA.
fglrx		: ATI Fire GL
snd_page_alloc		: Memory allocator for ALSA system.
snd_hwdep		: Hardware dependent layer
input_polldev		: Generic implementation of a polled input device
snd_seq_dummy		: ALSA sequencer MIDI-through client
video		: ACPI Video Driver
output		: Display Output Switcher Lowlevel Control Abstraction
snd_seq_oss		: OSS-compatible sequencer module
snd_seq_midi		: Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi		: Midlevel RawMidi code for ALSA.
snd_seq_midi_event		: MIDI byte &lt;-&gt; sequencer event coder
battery		: ACPI Battery Driver
snd_seq		: Advanced Linux Sound Architecture sequencer.
container		: ACPI container driver
ac		: ACPI AC Adapter Driver
snd_timer		: ALSA timer interface
snd_seq_device		: ALSA sequencer device management
psmouse		: PS/2 mouse driver
sdhci		: Secure Digital Host Controller Interface driver
acer_acpi		: Acer Laptop ACPI Extras Driver
led_class		: LED Class Interface
serio_raw		: Raw serio driver
snd		: Advanced Linux Sound Architecture driver for soundcards.
mmc_core
yenta_socket
rsrc_nonstatic
pcmcia_core		: Linux Kernel Card Services
ati_agp
wmi_acer		: ACPI-WMI Mapping Driver - acer_acpi port
k8temp		: AMD K8 core temperature monitor
button		: ACPI Button Driver
i2c_piix4		: PIIX4 SMBus driver
agpgart		: AGP GART driver
soundcore		: Core sound module
shpchp		: Standard Hot Plug PCI Controller Driver
pci_hotplug		: PCI Hot Plug PCI Core
i2c_core		: I2C-Bus main module
evdev		: Input driver event char devices
pcspkr		: PC Speaker beeper driver
ext3		: Second Extended Filesystem with journaling extensions
jbd
mbcache		: Meta block cache (for extended attributes)
sg		: SCSI generic (sg) driver
sr_mod		: SCSI cdrom (sr) driver
cdrom
sd_mod		: SCSI disk (sd) driver
atiixp		: PCI driver module for ATI IXP IDE
ide_core
pata_atiixp		: low-level driver for ATI IXP200/300/400
ata_generic		: low-level driver for generic ATA
8139too		: RealTek RTL-8139 Fast Ethernet driver
pata_acpi		: SCSI low-level driver for ATA in ACPI mode
8139cp		: RealTek RTL-8139C+ series 10/100 PCI Ethernet driver
mii		: MII hardware support library
ssb		: Sonics Silicon Backplane driver
ehci_hcd		: 10 Dec 2004 USB 2.0 &apos;Enhanced&apos; Host Controller (EHCI) Driver
libata		: Library module for ATA devices
ohci_hcd		: 2006 August 04 USB 1.1 &apos;Open&apos; Host Controller (OHCI) Driver
scsi_mod		: SCSI core
usbcore
thermal		: ACPI Thermal Zone Driver
processor		: ACPI Processor Driver
fan		: ACPI Fan Driver
fbcon
tileblit		: Tile Blitting Operation
font		: Console Fonts
bitblit		: Bit Blitting Operation
softcursor		: Generic software cursor
fuse		: Filesystem in Userspace

Boots
-----

-Boots-
Thu Jul 17 03:29 - 03:32 (00:02)		: Kernel 2.6.24-19-generi
Wed Jul 16 09:26 - 03:28 (18:01)		: Kernel 2.6.24-19-generi
Wed Jul 16 08:48 - 03:28 (18:40)		: Kernel 2.6.24-19-generi
Wed Jul 16 08:11 - 03:28 (19:16)		: Kernel 2.6.24-19-generi
Wed Jul 16 07:25 - 03:28 (20:03)		: Kernel 2.6.24-19-generi
Wed Jul 16 05:57 - 07:24 (01:26)		: Kernel 2.6.24-19-generi
Wed Jul 16 05:34 - 05:55 (00:21)		: Kernel 2.6.24-19-generi
Wed Jul 16 04:52 - 05:33 (00:40)		: Kernel 2.6.24-19-generi
Wed Jul 16 03:30 - 04:50 (01:19)		: Kernel 2.6.24-19-generi
Sun Jul 13 03:49 - 03:29 (2+23:40)		: Kernel 2.6.24-19-generi
Sun Jul 13 03:15 - 03:47 (00:32)		: Kernel 2.6.24-19-generi
Sun Jul 13 02:11 - 03:14 (01:03)		: Kernel 2.6.24-19-generi
Sun Jul 13 01:56 - 02:10 (00:13)		: Kernel 2.6.24-19-generi
Sat Jul 12 04:40 - 01:54 (21:14)		: Kernel 2.6.24-19-generi
Sat Jul 12 03:06 - 03:48 (00:42)		: Kernel 2.6.24-19-generi
Fri Jul 11 15:34 - 02:56 (11:22)		: Kernel 2.6.24-19-generi
Fri Jul 11 15:16 - 15:33 (00:17)		: Kernel 2.6.24-19-generi
Fri Jul 11 15:11 - 15:15 (00:03)		: Kernel 2.6.24-19-generi
Fri Jul 11 12:35 - 15:10 (02:34)		: Kernel 2.6.24-19-generi
Fri Jul 11 12:33 - 15:10 (02:36)		: Kernel 2.6.24-19-generi
Fri Jul 11 12:31 - 15:10 (02:38)		: Kernel 2.6.24-19-generi
Fri Jul 11 04:23 - 12:30 (08:06)		: Kernel 2.6.24-19-generi
Fri Jul 11 02:30 - 04:21 (01:51)		: Kernel 2.6.24-19-generi
Fri Jul 11 01:53 - 02:28 (00:35)		: Kernel 2.6.24-19-generi
Fri Jul 11 00:52 - 01:52 (01:00)		: Kernel 2.6.24-19-generi
Fri Jul 11 00:47 - 00:51 (00:04)		: Kernel 2.6.24-19-generi
Thu Jul 10 18:31 - 00:06 (05:35)		: Kernel 2.6.24-19-generi
Thu Jul 10 17:53 - 18:29 (00:36)		: Kernel 2.6.24-19-generi
Thu Jul 10 16:36 - 16:57 (00:20)		: Kernel 2.6.24-19-generi
Wed Jul 9 22:48 - 15:38 (16:49)		: Kernel 2.6.24-19-generi
Wed Jul 9 22:34 - 22:47 (00:12)		: Kernel 2.6.24-19-generi
Wed Jul 9 22:00 - 22:33 (00:33)		: Kernel 2.6.24-19-generi
Wed Jul 9 21:20 - 21:59 (00:38)		: Kernel 2.6.24-19-generi
Wed Jul 9 10:14 - 21:19 (11:05)		: Kernel 2.6.24-19-generi
Wed Jul 9 04:23 - 05:52 (01:28)		: Kernel 2.6.24-19-generi
Tue Jul 8 23:02 - 03:48 (04:46)		: Kernel 2.6.24-19-generi
Tue Jul 8 22:03 - 22:17 (00:14)		: Kernel 2.6.24-19-generi
Tue Jul 8 21:17 - 21:26 (00:09)		: Kernel 2.6.24-19-generi
Tue Jul 8 21:15 - 21:26 (00:10)		: Kernel 2.6.24-19-generi
Tue Jul 8 17:32 - 17:52 (00:19)		: Kernel 2.6.24-19-generi
Tue Jul 8 15:37 - 17:28 (01:50)		: Kernel 2.6.24-19-generi
Tue Jul 8 13:38 - 14:01 (00:23)		: Kernel 2.6.24-19-generi
Tue Jul 8 02:54 - 12:09 (09:14)		: Kernel 2.6.24-19-generi
Mon Jul 7 15:57 - 01:59 (10:01)		: Kernel 2.6.24-19-generi
Mon Jul 7 15:08 - 15:49 (00:41)		: Kernel 2.6.24-19-generi
Sat Jul 5 10:13 - 14:27 (2+04:14)		: Kernel 2.6.24-19-generi
Sat Jul 5 05:35 - 14:27 (2+08:52)		: Kernel 2.6.24-19-generi
Sat Jul 5 03:17 - 04:49 (01:32)		: Kernel 2.6.24-19-generi
Sat Jul 5 02:19 - 03:16 (00:57)		: Kernel 2.6.24-19-generi
Fri Jul 4 02:59 - 02:15 (23:15)		: Kernel 2.6.24-19-generi

Languages
---------

-Available Languages-
en_AU.utf8		: English locale for Australia
en_BW.utf8		: English locale for Botswana
en_CA.utf8		: English locale for Canada
en_DK.utf8		: English locale for Denmark
en_GB.utf8		: English locale for Britain
en_HK.utf8		: English locale for Hong Kong
en_IE.utf8		: English locale for Ireland
en_IN		: English language locale for India
en_NZ.utf8		: English locale for New Zealand
en_PH.utf8		: English language locale for Philippines
en_SG.utf8		: English language locale for Singapore
en_US.utf8		: English locale for the USA
en_ZA.utf8		: English locale for South Africa

Filesystems
-----------

-Mounted File Systems-
/dev/sda3		: 43.8 GiB total, 36.1 GiB free
proc		: 0.0 B total, 0.0 B free
/sys		: 0.0 B total, 0.0 B free
varrun		: 441.3 MiB total, 441.2 MiB free
varlock		: 441.3 MiB total, 441.3 MiB free
udev		: 441.3 MiB total, 441.3 MiB free
devshm		: 441.3 MiB total, 441.3 MiB free
devpts		: 0.0 B total, 0.0 B free
lrm		: 441.3 MiB total, 402.5 MiB free
securityfs		: 0.0 B total, 0.0 B free
gvfs-fuse-daemon		: 43.8 GiB total, 36.1 GiB free

Shared Directories
------------------

-SAMBA-
-NFS-

Display
-------

-Display-
Resolution		: 0x0 pixels
Vendor		: The X.Org Foundation
Version		: 1.4.0.90
-Monitors-
-Extensions-
ATIFGLEXTENSION
ATIFGLRXDRI
ATITVOUT
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
Extended-Visual-Information
GLX
MIT-SCREEN-SAVER
MIT-SHM
MIT-SUNDRY-NONSTANDARD
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
TOG-CUP
X-Resource
XAccessControlExtension
XC-APPGROUP
XC-MISC
XFIXES
XFree86-Bigfont
XFree86-DGA
XFree86-DRI
XFree86-Misc
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor		: ATI Technologies Inc.
Renderer		: ATI Radeon Xpress Series
Version		: 2.1.7412 Release
Direct Rendering		: Yes

Network Interfaces
------------------

-Network Interfaces-
lo		: Sent 0.01MiB, received 0.01MiB (127.0.0.1)
eth0		: Sent 0.00MiB, received 0.00MiB
wmaster0		: Sent 0.00MiB, received 0.00MiB
eth1		: Sent 0.01MiB, received 0.01MiB (192.168.2.101)

Users
-----

-Human Users-
zip		: zip
guest
-System Users-
root		: root
daemon		: daemon
bin		: bin
sys		: sys
sync		: sync
games		: games
man		: man
lp		: lp
mail		: mail
news		: news
uucp		: uucp
proxy		: proxy
www-data		: www-data
backup		: backup
list		: Mailing List Manager
irc		: ircd
gnats		: Gnats Bug-Reporting System (admin)
nobody		: nobody
dhcp
syslog
klog
messagebus
hplip		: HPLIP system user
avahi-autoipd		: Avahi autoip daemon
avahi		: Avahi mDNS daemon
haldaemon		: Hardware abstraction layer
gdm		: Gnome Display Manager
libuuid
pulse		: PulseAudio daemon
polkituser		: PolicyKit

Devices
*******


Processor
---------

-Processors-
AMD Turion(tm) 64 X2 Mobile Technology TL-50		: 1600.00MHz
AMD Turion(tm) 64 X2 Mobile Technology TL-50		: 1600.00MHz

Memory
------

-Memory-
Total Memory		: 903864 kB
Free Memory		: 299052 kB
Buffers		: 14008 kB
Cached		: 297612 kB
Cached Swap		: 0 kB
Active		: 311220 kB
Inactive		: 211292 kB
High Memory		: 0 kB
Free High Memory		: 0 kB
Low Memory		: 903864 kB
Free Low Memory		: 299052 kB
Virtual Memory		: 2040184 kB
Free Virtual Memory		: 2040184 kB
Dirty		: 0 kB
Writeback		: 0 kB
AnonPages		: 210880 kB
Mapped		: 71340 kB
Slab		: 18884 kB
SReclaimable		: 10868 kB
SUnreclaim		: 8016 kB
PageTables		: 2200 kB
NFS_Unstable		: 0 kB
Bounce		: 0 kB
CommitLimit		: 2492116 kB
Committed_AS		: 654580 kB
VmallocTotal		: 114680 kB
VmallocUsed		: 19412 kB
VmallocChunk		: 94804 kB

PCI Devices
-----------

-PCI Devices-
Host bridge		: ATI Technologies Inc RS480 Host Bridge 
PCI bridge		: ATI Technologies Inc RS480 PCI Bridge 
PCI bridge		: ATI Technologies Inc RS480 PCI Bridge 
PCI bridge		: ATI Technologies Inc RS480 PCI Bridge 
USB Controller		: ATI Technologies Inc IXP SB400 USB Host Controller 
USB Controller		: ATI Technologies Inc IXP SB400 USB Host Controller 
USB Controller		: ATI Technologies Inc IXP SB400 USB2 Host Controller 
SMBus		: ATI Technologies Inc IXP SB400 SMBus Controller 
IDE interface		: ATI Technologies Inc IXP SB400 IDE Controller 
Audio device		: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller 
ISA bridge		: ATI Technologies Inc IXP SB400 PCI-ISA Bridge 
PCI bridge		: ATI Technologies Inc IXP SB400 PCI-PCI Bridge 
Host bridge		: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Host bridge		: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
Host bridge		: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
Host bridge		: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
VGA compatible controller		: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] 
Ethernet controller		: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ 
Network controller		: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
CardBus bridge		: ENE Technology Inc CB-712/4 Cardbus Controller 
FLASH memory		: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller 
SD Host controller		: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller 
FLASH memory		: ENE Technology Inc FLASH memory: ENE Technology Inc: 
FLASH memory		: ENE Technology Inc SD/MMC Card Reader Controller 

USB Devices
-----------


Printers
--------

-Printers (CUPS)-
PDF

Battery
-------

-Battery: BAT1-
State		: charged (load: 0 mA)
Capacity		: 3809 mAh / 4000 mAh (95.23%)
Battery Technology		: rechargeable (Lion)
Model Number		: Primary
Serial Number

Sensors
-------

-Cooling Fans-
-Temperatures-
temp1		: 50.00?C
-Voltage Values-
-ACPI Thermal Zone-
THRM		: 48?C

Input Devices
-------------

-Input Devices-
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 PC Speaker
 Power Button (FF)
 Lid Switch
 Power Button (CM)
 Sleep Button (CM)
 SynPS/2 Synaptics TouchPad
 Video Bus
 Video Bus
 b43-phy0

Storage
-------

-IDE Disks-
-SCSI Disks-
ATA HTS541010G9AT00
HL-DT-ST DVDRAM GSA-T10N

Benchmarks
**********


CPU ZLib
--------

-CPU ZLib-
<i>This Machine</i>		: 0.000
PowerPC 740/750 (280.00MHz)		: 2150.597408
Intel(R) Celeron(R) M processor         1.50GHz		: 8761.604561

CPU Fibonacci
-------------

-CPU Fibonacci-
<i>This Machine</i>		: 4.687
Intel(R) Celeron(R) M processor         1.50GHz		: 8.1375674
PowerPC 740/750 (280.00MHz)		: 58.07682

CPU MD5
-------

-CPU MD5-
<i>This Machine</i>		: 42.815
PowerPC 740/750 (280.00MHz)		: 7.115258
Intel(R) Celeron(R) M processor         1.50GHz		: 38.6607998

CPU SHA1
--------

-CPU SHA1-
<i>This Machine</i>		: 51.701
PowerPC 740/750 (280.00MHz)		: 6.761451
Intel(R) Celeron(R) M processor         1.50GHz		: 49.6752776

CPU Blowfish
------------

-CPU Blowfish-
<i>This Machine</i>		: 22.069
Intel(R) Celeron(R) M processor         1.50GHz		: 26.1876862
PowerPC 740/750 (280.00MHz)		: 172.816713

FPU Raytracing
--------------

-FPU Raytracing-
<i>This Machine</i>		: 30.288
Intel(R) Celeron(R) M processor         1.50GHz		: 40.8816714
PowerPC 740/750 (280.00MHz)		: 161.312647
zip@HAL:~$ an A

                            and here the proc info
root@HAL:~# rovclock -i
Radeon overclock 0.6e by Hasw (hasw@hasw.net)

Found ATI card on 01:05, device id: 0x5975
I/O base address: 0x9000
Video BIOS shadow found @ 0xc0000
Reference clock from BIOS: 14.32 MHz
Memory size: 31744 kB
Memory channels: 0, CD,CH only: 0
tRcdRD:   3
tRcdWR:   1
tRP:      3
tRAS:     6
tRRD:     1
tR2W-CL:  1
tWR:      1
tW2R:     0
tW2Rsb:   0
tR2R:     1
tRFC:     13
tWL(0.5): 0
tCAS:     0
tCMD:     0
tSTR:     0
XTAL: 14.32 MHz, RefDiv: 6

Core: 400.96 MHz, Mem: 0.0 MHz
root@HAL:~#

Right there where it says Core: I changed it from 300 MHz to 400 Mhz

---

### Post by Sam Lars on 2008-07-17
Why do all the CPU tests say Celeron M?  Or is this not related?

---

### Post by Zipolite on 2008-07-18
I was wondering that myself....hoping to get a better response then this though

---

### Post by Sam Lars on 2008-08-16
Does it lag even if you're just sitting there moving the mouse, or is it more during videos or something like that?  Is it using full processor (or all of one core) at the time?
It seems like ATI cards aren't as well supported as Nvidia... are you using default or proprietary drivers?
What happened when you changed the core setting?  Did it get better?  Overclocking usually introduces issues like this rather than taking them away, but whatever works...

---

