---
title: "SD Card Reader doesn't work"
date: 2013-10-04
forum: Hardware
---

### Post by swedenfox on 2013-10-04
[B]Hi all!

i have a little.... big trouble with my sd card reader on my tablet [/B]

```
lshw
[http://pastebin.com/SLer3tD0](http://pastebin.com/SLer3tD0)

```
```

lsusb


[COLOR="#FF0000"]Bus 001 Device 002: ID 0cf2:6238 ENE Technology, Inc.[/COLOR] 
Bus 001 Device 008: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 005: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 03eb:201c Atmel Corp. at90usbkey sample firmware (HID mouse)
Bus 004 Device 002: ID 0af0:6901 Option 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 001 Device 010: ID 0e8f:0040 GreenAsia Inc. 

```

[B], and i don't know how make it works....

first of all it works pretty well  on puppy lucid  (but there wasn't working the touchscreen )

now i m on xubuntu 13.04 , i configured the touchscreen but i have this big problem with the sd reader .[/B]
```

dmesg


[  743.446473] sd 2:0:0:0: [sdb]  
[  743.446479] Add. Sense: Unrecovered read error
[  743.446486] sd 2:0:0:0: [sdb] CDB: 
[  743.446491] Read(10): 28 00 00 f6 77 f0 00 00 08 00
[  743.446513] blk_update_request: 136 callbacks suppressed
[  743.446519] end_request: I/O error, dev sdb, sector 16152560
[  743.446527] quiet_error: 135 callbacks suppressed
[  743.446533] Buffer I/O error on device sdb, logical block 2019070
[  923.478438] sd 2:0:0:0: timing out command, waited 180s
[  923.478461] sd 2:0:0:0: [sdb] Unhandled sense code
[  923.478469] sd 2:0:0:0: [sdb]  
[  923.478475] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  923.478482] sd 2:0:0:0: [sdb]  
[  923.478487] Sense Key : Hardware Error [current] 
[  923.478496] sd 2:0:0:0: [sdb]  
[  923.478503] Add. Sense: Unrecovered read error
[  923.478510] sd 2:0:0:0: [sdb] CDB: 
[  923.478514] Read(10): 28 00 00 f6 77 f0 00 00 08 00
[  923.478537] end_request: I/O error, dev sdb, sector 16152560
[  923.478546] Buffer I/O error on device sdb, logical block 2019070

```

can you help me ?

---

### Post by swedenfox on 2013-10-11
no one know how help me?
i have still the problem

---

### Post by BlinkinCat on 2013-10-11
> **swedenfox said:**
> no one know how help me?
i have still the problem

Hi,

I am sorry I can't help you with your problem, but I just wish you to know that it is considered perfectly in order in the Forums to bump your thread after 24 hours. You did not need to wait so long.

I hope that someone will help you soon!

Good luck - :)

---

### Post by swedenfox on 2013-10-11
thnx for the Reply

some info more 

**ALL SDHC ** doesn't works , they give some errors on dmesg
normal SD  was reconized immediatly .


so i suppose a problem with some module .

The SD reader get up with **USB_storage** module 


so i m analizing why in puppy precise it works  and in ubuntu /xubuntu it doesn't

Any ideas?

---

### Post by swedenfox on 2013-10-11
ok i did  a stamp of modules in Puppy & in Ubuntu

i have no idea why SDHC doesn't be read

PUPPY 
```
Computer
Summary
Computer
Processor	2x Intel(R) Atom(TM) CPU N455 @ 1.66GHz
Memory	2063MB (89MB used)
Machine Type	Physical machine
Operating System	Precise Puppy - 5.7.1
User Name	root (root)
Date/Time	Fri 11 Oct 2013 12:24:12 PM GMT-8
Display
Resolution	1024x768 pixels
OpenGL Renderer	Mesa DRI Intel(R) IGD x86/MMX/SSE2
X11 Vendor	The X.Org Foundation
Audio Devices
Audio Adapter	HDA-Intel - HDA Intel
Input Devices
AT Translated Set 2 keyboard	
USB Optical Mouse	
GASIA USB Keyboard	
GASIA USB Keyboard	
Sleep Button	
Lid Switch	
Power Button	
Power Button	
CDT 9.75	
PC Speaker	
Video Bus	
Gotek4Tainell	
HDA Intel Mic	
HDA Intel Front Headphone	
Printers (CUPS)
CUPS-PDF	Default
SCSI Disks
ATA SuperSSpeed 32GB	
USB2.0 CardReader COMBO	
USB FLASH DRIVE	
Operating System
Version
Kernel	Linux 3.9.11 (i686)
Version	#1 SMP Sat Jul 27 19:40:54 GMT-8 2013
C Library	GNU C Library version 2.15 (stable)
Distribution	Precise Puppy - 5.7.1
Current Session
Computer Name	puppypc24536
User Name	root (root)
Home Directory	/root
Desktop Environment	Unknown (Window Manager: JWM)
Misc
Uptime	9 minutes
Load Average	0.06, 0.23, 0.21
Kernel Modules
Loaded Modules
cpufreq_ondemand	'cpufreq_ondemand' - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors
option	USB Driver for GSM modems
usb_wwan	USB Driver for GSM modems
usbserial	USB Serial Driver core
fan	ACPI Fan Driver
arc4	ARC4 Cipher Algorithm
snd_hda_codec_via	VIA HD-audio codec
snd_hda_intel	Intel HDA driver
snd_hda_codec	HDA codec core
snd_hwdep	Hardware dependent layer
snd_pcm_oss	PCM OSS emulation for ALSA.
snd_mixer_oss	Mixer OSS emulation for ALSA.
snd_pcm	Midlevel PCM code for ALSA.
uvcvideo	USB Video Class driver
videobuf2_core	Driver helper framework for Video for Linux 2
snd_seq_dummy	ALSA sequencer MIDI-through client
videodev	Device registrar for Video4Linux drivers v2
videobuf2_vmalloc	vmalloc memory handling routines for videobuf2
videobuf2_memops	common memory handling routines for videobuf2
ath5k	Support for 5xxx series of Atheros 802.11 wireless LAN cards.
mac80211	IEEE 802.11 subsystem
ath	Shared library for Atheros wireless LAN cards.
cfg80211	wireless configuration support
rfkill	RF switch support
snd_seq_oss	OSS-compatible sequencer module
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_rawmidi	Midlevel RawMidi code for ALSA.
pcspkr	PC Speaker beeper driver
snd_seq	Advanced Linux Sound Architecture sequencer.
snd_seq_device	ALSA sequencer device management
snd_timer	ALSA timer interface
i2c_i801	I801 SMBus driver
lpc_ich	LPC interface for Intel ICH
mfd_core	
battery	ACPI Battery Driver
snd	Advanced Linux Sound Architecture driver for soundcards.
i915	Intel Graphics
drm_kms_helper	DRM KMS helper
shpchp	Standard Hot Plug PCI Controller Driver
soundcore	Core sound module
snd_page_alloc	Memory allocator for ALSA system.
drm	DRM shared core routines
i2c_algo_bit	I2C-Bus bit-banging algorithm
i2c_core	I2C-Bus main module
intel_agp	
intel_gtt	
agpgart	AGP GART driver
hid_multitouch	HID multitouch panels
evdev	Input driver event char devices
thermal	ACPI Thermal Zone Driver
video	ACPI Video Driver
acpi_cpufreq	ACPI Processor P-States Driver
mperf	
button	ACPI Button Driver
processor	ACPI Processor Driver
thermal_sys	Generic thermal management sysfs support
hwmon	hardware monitoring sysfs/class support
ac	ACPI AC Adapter Driver
fbcon	
font	Console Fonts
bitblit	Bit Blitting Operation
softcursor	Generic software cursor
tileblit	Tile Blitting Operation
fuse	Filesystem in Userspace
aufs	aufs -- Advanced multi layered unification filesystem
squashfs	squashfs 4.0, a compressed read-only filesystem
Boots
Boots
Languages
Available Languages
en_US.utf8	English locale for the USA
Filesystems
Mounted File Systems
rootfs	/	0.50 % (1.2 GiB of 1.2 GiB)
tmpfs	/initrd/pup_rw	0.50 % (1.2 GiB of 1.2 GiB)
tmpfs	/initrd/mnt/tmpfs	99.36 % (1000.0 KiB of 151.9 MiB)
/dev/loop0	/initrd/pup_ro2	100.00 % (0.0 B of 151.0 MiB)
unionfs	/	0.50 % (1.2 GiB of 1.2 GiB)
shmfs	/dev/shm	0.00 % (461.9 MiB of 461.9 MiB)
/dev/sda6	/mnt/sda6	59.32 % (2.1 GiB of 5.2 GiB)
Display
Display
Resolution	1024x768 pixels
Vendor	The X.Org Foundation
Version	1.11.3
Monitors
Monitor 0	1024x768 pixels
Extensions
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
RANDR	
RECORD	
RENDER	
SECURITY	
SGI-GLX	
SHAPE	
SYNC	
X-Resource	
XC-MISC	
XFIXES	
XFree86-VidModeExtension	
XINERAMA	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
OpenGL
Vendor	Tungsten Graphics, Inc
Renderer	Mesa DRI Intel(R) IGD x86/MMX/SSE2
Version	1.4 Mesa 8.0.4
Direct Rendering	Yes
Environment Variables
Environment Variables
HOSTNAME	puppypc24536
XDG_DATA_HOME	/root/.local/share
TERM	xterm
SHELL	/bin/bash
HISTSIZE	1000
QT_XFT	true
GTK2_RC_FILES	/root/.gtkrc-2.0
DEFAULTDRAW	inkscapelite
MOZILLA_FIVE_HOME	/usr/lib/seamonkey
XLIB_SKIP_ARGB_VISUALS	1
USER	root
HISTFILESIZE	2000
LD_LIBRARY_PATH	/lib:/usr/lib:/usr/X11R7/lib:/root/my-applications/lib:/usr/local/lib:/usr/lib/seamonkey
LS_COLORS	bd=33:cd=33
GDK_USE_XFT	1
LANGORG	en_US.UTF-8
RGBDEF	/usr/share/X11/rgb.txt
OOO_FORCE_DESKTOP	gnome
DEFAULTIMAGEVIEWER	viewnior
MOZ_DISABLE_PANGO	1
DEFAULTPAINT	mtpaint
MOZ_PLUGIN_PATH	/usr/lib/mozilla/plugins:/usr/lib/seamonkey/plugins
XDG_CONFIG_DIRS	/etc/xdg
PATH	/bin:/usr/bin:/sbin:/usr/sbin:/usr/local/bin:/usr/X11R7/bin:/root/my-applications/bin:/usr/games
DEFAULTBROWSER	mozstart
DEFAULTMEDIAPLAYER	gnomemplayershell
PWD	/root
INPUTRC	/etc/inputrc
DEFAULTIMAGEEDITOR	mtpaint
EDITOR	mp
LANG	en_US.UTF-8
XFINANSDIR	/root/.xfinans
DEFAULTHTMLEDITOR	mozedit
DEFAULTSPREADSHEET	gnumeric
HISTCONTROL	ignoredups
HOME	/root
SHLVL	3
XDG_CONFIG_HOME	/root/.config
XDG_CACHE_HOME	/root/.cache
LOGNAME	root
G_FILENAME_ENCODING	@locale
PREFIX	/usr
XDG_DATA_DIRS	/usr/share:/usr/local/share
TEXTDOMAIN	xwin
WINDOWPATH	4
DISPLAY	:0
MM_RUNASROOT	1
DEFAULTTEXTEDITOR	geany
DEFAULTWORDPROCESSOR	abiword
OUTPUT_CHARSET	UTF-8
_	/usr/bin/hardinfo
Development
Scripting Languages
CPython	Not found
Perl	5.14.2
PHP	Not found
Ruby	Not found
Bash	4.1.0(1)-release
Compilers
C (GCC)	Not found
Java	Not found
CSharp (Mono, old)	Not found
CSharp (Mono)	Not found
Vala	Not found
Haskell (GHC)	Not found
FreePascal	Not found
Tools
make	Not found
GDB	Not found
strace	Not found
valgrind	Not found
QMake	Not found
Users
Users
root	root
daemon	
nobody	
spot	Linux User
bin	bin
messagebus	Linux User
ftp	Linux User
haldaemon	Hardware abstraction layer
uucp	uucp
sshd	sshd
webuser	Linux User
fido	Linux User
Groups
Groups
root	0
daemon	1
tty	109
ppp	200
users	500
nobody	65534
guest	501
spot	502
bin	2
503	503
ftp	1000
dip	30
uucp	10
lpadmin	112
netdev	113
haldaemon	119
sshd	33
webgroup	504
disk	100
audio	101
lp	102
dialout	103
kmem	104
video	105
floppy	106
cdrom	107
tape	108
tty	109
plugdev	110
Devices
Processor
Processors
Intel(R) Atom(TM) CPU N455 @ 1.66GHz	1000.00MHz
Intel(R) Atom(TM) CPU N455 @ 1.66GHz	1667.00MHz
Memory
Memory
Total Memory	2063340 kB
Free Memory	1688360 kB
Buffers	40388 kB
Cached	285184 kB
Cached Swap	0 kB
Active	52872 kB
Inactive	292160 kB
Active(anon)	23312 kB
Inactive(anon)	174124 kB
Active(file)	29560 kB
Inactive(file)	118036 kB
Unevictable	0 kB
Mlocked	0 kB
High Memory	1173064 kB
Free High Memory	864264 kB
Low Memory	890276 kB
Free Low Memory	824096 kB
Virtual Memory	459772 kB
Free Virtual Memory	459772 kB
Dirty	4 kB
Writeback	0 kB
AnonPages	19672 kB
Mapped	18340 kB
Shmem	177936 kB
Slab	22940 kB
SReclaimable	14464 kB
SUnreclaim	8476 kB
KernelStack	560 kB
PageTables	612 kB
NFS_Unstable	0 kB
Bounce	0 kB
WritebackTmp	0 kB
CommitLimit	1491440 kB
Committed_AS	232460 kB
VmallocTotal	122880 kB
VmallocUsed	5948 kB
VmallocChunk	112952 kB
DirectMap4k	8184 kB
DirectMap2M	905216 kB
PCI Devices
PCI Devices
Host bridge	Intel Corporation N10 Family DMI Bridge
VGA compatible controller	Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
Display controller	Intel Corporation N10 Family Integrated Graphics Controller
Audio device	Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
PCI bridge	Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
USB controller	Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
USB controller	Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
USB controller	Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
USB controller	Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
USB controller	Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
PCI bridge	Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
ISA bridge	Intel Corporation NM10 Family LPC Controller (rev 02)
IDE interface	Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
SMBus	Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
Ethernet controller	Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
USB Devices
USB Devices
	
	
at90usbkey sample firmware (HID mouse)	
2.0 root hub	
1.1 root hub	
1.1 root hub	
	
Printers
Printers (CUPS)
CUPS-PDF	Default
Battery
Battery: BAT0
State	charging (load: 1452 mA)
Capacity	2369 mAh / 3600 mAh (65.81%)
Battery Technology	rechargeable (LION)
Manufacturer	THD(Thread Technology)
Model Number	PX1
Serial Number	
Sensors
Temperature
temp1 (acpitz)	-20.00°C
Input Devices
Input Devices
AT Translated Set 2 keyboard	
USB Optical Mouse	
GASIA USB Keyboard	
GASIA USB Keyboard	
Sleep Button	
Lid Switch	
Power Button	
Power Button	
CDT 9.75	
PC Speaker	
Video Bus	
Gotek4Tainell	
HDA Intel Mic	
HDA Intel Front Headphone	
Storage
SCSI Disks
ATA SuperSSpeed 32GB	
USB2.0 CardReader COMBO	
USB FLASH DRIVE	
DMI
BIOS
Date	05/05/2012
Vendor	American Megatrends Inc. (www.ami.com)
Version	080016
Board
Name	PX1
Vendor	THD(Thread technology)
Memory SPD
SPD
Please load the eeprom module to obtain information about memory SPD	
Resources
I/O Ports
0000-0cf7 	PCI Bus 0000:00
0000-001f 	dma1
0020-0021 	pic1
0040-0043 	timer0
0050-0053 	timer1
0060-0060 	keyboard
0062-0062 	EC data
0064-0064 	keyboard
0066-0066 	EC cmd
0070-0077 	rtc
0080-008f 	dma page reg
00a0-00a1 	pic2
00c0-00df 	dma2
00f0-00ff 	fpu
0170-0177 	PCI Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
0170-0177 	ata_piix
01f0-01f7 	PCI Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
01f0-01f7 	ata_piix
0376-0376 	PCI Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
0376-0376 	ata_piix
03c0-03df 	vga+
03f6-03f6 	PCI Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
03f6-03f6 	ata_piix
0400-041f 	PCI Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
0400-041f 	i801_smbus
0480-04bf 	gpio_ich
0480-04bf 	pnp 00:06
04d0-04d1 	pnp 00:06
0cf8-0cff 	PCI conf1
0d00-ffff 	PCI Bus 0000:00
1000-107f 	pnp 00:06
1000-1003 	ACPI PM1a_EVT_BLK
1004-1005 	ACPI PM1a_CNT_BLK
1008-100b 	ACPI PM_TMR
1010-1015 	ACPI CPU throttle
1020-1020 	ACPI PM2_CNT_BLK
1028-102f 	gpio_ich
1028-102f 	ACPI GPE0_BLK
1030-1033 	iTCO_wdt
1060-107f 	iTCO_wdt
2000-2fff 	PCI Bus 0000:01
e400-e41f 	PCI Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
e400-e41f 	uhci_hcd
e480-e49f 	PCI Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
e480-e49f 	uhci_hcd
e800-e81f 	PCI Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
e800-e81f 	uhci_hcd
e880-e89f 	PCI Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
e880-e89f 	uhci_hcd
ec00-ec07 	PCI Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
ff90-ff9f 	PCI Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
ff90-ff9f 	ata_piix
Memory
00000000-00000fff 	reserved
00001000-0009fbff 	System RAM
0009fc00-0009ffff 	reserved
000a0000-000bffff 	PCI Bus 0000:00
000a0000-000bffff 	Video RAM area
000c0000-000c7fff 	Video ROM
000d0000-000dffff 	PCI Bus 0000:00
000e0000-000fffff 	reserved
000f0000-000fffff 	System ROM
00100000-7f58ffff 	System RAM
01000000-0136ba08 	Kernel code
0136ba09-014e917f 	Kernel data
0154d000-01580fff 	Kernel bss
7f590000-7f59dfff 	ACPI Tables
7f59e000-7f5cffff 	ACPI Non-volatile Storage
7f5d0000-7f5dffff 	reserved
7f5e0000-7f5e7fff 	RAM buffer
7f5e8000-dfffffff 	reserved
7f700000-dfffffff 	PCI Bus 0000:00
80000000-801fffff 	PCI Bus 0000:01
80200000-802003ff 	PCI Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
80201000-80201fff 	Intel Flush Page
80204000-80207fff 	i915 MCHBAR
d0000000-dfffffff 	PCI Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
e0000000-efffffff 	PCI MMCONFIG 0000 [bus 00-ff]
e0000000-efffffff 	pnp 00:0b
f0000000-fed8ffff 	PCI Bus 0000:00
fe880000-fe8fffff 	PCI Intel Corporation N10 Family Integrated Graphics Controller
fe977c00-fe977fff 	PCI Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
fe977c00-fe977fff 	ehci_hcd
fe978000-fe97bfff 	PCI Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
fe978000-fe97bfff 	ICH HD audio
fe980000-fe9fffff 	PCI Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
fea00000-feafffff 	PCI Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
feb00000-febfffff 	PCI Bus 0000:01
febf0000-febfffff 	PCI Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
febf0000-febfffff 	Module Support for 5xxx series of Atheros 802.11 wireless LAN cards.
fec00000-fec003ff 	IOAPIC 0
fed00000-fed003ff 	HPET 0
fed14000-fed19fff 	pnp 00:00
fed1c000-fed1ffff 	pnp 00:06
fed1f410-fed1f414 	iTCO_wdt
fed20000-fed8ffff 	pnp 00:06
fed90000-fed93fff 	pnp 00:00
fee00000-fee00fff 	Local APIC
fee00000-fee00fff 	reserved
fee00000-fee00fff 	pnp 00:0a
ffb00000-ffffffff 	reserved
ffc00000-ffefffff 	pnp 00:09
DMA
4	cascade
Network
Interfaces
Network Interfaces
wlan0	0.00MiB	0.00MiB	
lo	0.00MiB	0.00MiB	127.0.0.1
IP Connections
Connections
127.0.0.1:631	LISTEN	0.0.0.0:*	tcp
0.0.0.0:631		0.0.0.0:*	udp
Routing Table
IP routing table
127.0.0.0 / 0.0.0.0	255.0.0.0	U	lo
ARP Table
ARP Table
DNS Servers
Name servers
Statistics
IP
2	Requests sent out
0	Incoming packets discarded
0	Incoming packets discarded
2	Requests sent out
2	Requests sent out
ICMP
0	ICMP messages failed
0	ICMP messages failed
0	ICMP messages failed
0	ICMP messages failed
TCP
1	Resets sent
0	Bad segments received.
1	Resets sent
0	Bad segments received.
0	Bad segments received.
2	Segments send out
2	Segments send out
0	Bad segments received.
0	Bad segments received.
1	Resets sent
UDP
0	Packets sent
0	Packets sent
0	Packets sent
0	Packets sent
UDPLITE
TCPEXT
0	Packet headers predicted
IPEXT
Shared Directories
SAMBA
```


UBUNTU

```
Computer
Summary
Computer
Processor	2x Intel(R) Atom(TM) CPU N455 @ 1.66GHz
Memory	2040MB (341MB used)
Operating System	Ubuntu 13.04
User Name	andrea (ANDREA)
Date/Time	ven 11 ott 2013 12:45:59 CEST
Display
Resolution	1024x768 pixels
OpenGL Renderer	Unknown
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	HDA-Intel - HDA Intel
Input Devices
Sleep Button	
Lid Switch	
Power Button	
Power Button	
AT Translated Set 2 keyboard	
Gotek4Tainell	
Video Bus	
HDA Intel Mic	
HDA Intel Front Headphone	
USB Optical Mouse	
CDT 9.75	
GASIA USB Keyboard	
GASIA USB Keyboard	
Printers
No printers found	
SCSI Disks
ATA SuperSSpeed 32GB	
Operating System
Version
Kernel	Linux 3.8.0-19-generic (x86_64)
Compiled	#30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013
C Library	Unknown
Default C Compiler	GNU C Compiler version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1)
Distribution	Ubuntu 13.04
Current Session
Computer Name	andrea-PX1
User Name	andrea (ANDREA)
Home Directory	/home/andrea
Desktop Environment	XFCE 4
Misc
Uptime	13 minutes
Load Average	0,00, 0,00, 0,00
Kernel Modules
Loaded Modules
shpchp	Standard Hot Plug PCI Controller Driver
coretemp	Intel Core temperature monitor
option	USB Driver for GSM modems
usb_wwan	USB Driver for GSM modems
arc4	ARC4 Cipher Algorithm
joydev	Joystick device interfaces
parport_pc	PC-style parallel port driver
rfcomm	Bluetooth RFCOMM ver 1.11
ppdev	
bnep	Bluetooth BNEP ver 1.3
bluetooth	Bluetooth Core ver 2.16
gpio_ich	GPIO interface for Intel ICH series
hid_generic	HID generic driver
hid_multitouch	HID multitouch panels
snd_hda_codec_via	VIA HD-audio codec
snd_hda_intel	Intel HDA driver
snd_hda_codec	HDA codec core
snd_hwdep	Hardware dependent layer
snd_pcm	Midlevel PCM code for ALSA.
microcode	Microcode Update Driver
ath5k	Support for 5xxx series of Atheros 802.11 wireless LAN cards.
snd_page_alloc	Memory allocator for ALSA system.
uvcvideo	USB Video Class driver
ath	Shared library for Atheros wireless LAN cards.
videobuf2_vmalloc	vmalloc memory handling routines for videobuf2
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
videobuf2_memops	common memory handling routines for videobuf2
snd_seq_midi_event	MIDI byte <-> sequencer event coder
videobuf2_core	Driver helper framework for Video for Linux 2
serio_raw	Raw serio driver
snd_rawmidi	Midlevel RawMidi code for ALSA.
videodev	Device registrar for Video4Linux drivers v2
mac80211	IEEE 802.11 subsystem
lpc_ich	LPC interface for Intel ICH
snd_seq	Advanced Linux Sound Architecture sequencer.
cfg80211	wireless configuration support
snd_seq_device	ALSA sequencer device management
snd_timer	ALSA timer interface
snd	Advanced Linux Sound Architecture driver for soundcards.
mac_hid	
usbhid	USB HID core driver
i915	Intel Graphics
video	ACPI Video Driver
drm_kms_helper	DRM KMS helper
drm	DRM shared core routines
hid	
i2c_algo_bit	I2C-Bus bit-banging algorithm
soundcore	Core sound module
usbserial	USB Serial Driver core
lp	
parport	
Boots
Boots
Fri Oct 11 12:32	33..8.0-19-generic|-
Fri Oct 11 12:25	33..8.0-19-generic|-
Fri Oct 11 12:11	33..8.0-19-generic|-
Fri Oct 11 10:41	33..8.0-19-generic|-
Fri Oct 11 10:30	33..8.0-19-generic|-
Fri Oct 11 10:01	33..8.0-19-generic|-
Fri Oct 11 09:30	33..8.0-19-generic|-
Fri Oct 11 08:23	33..8.0-19-generic|-
Fri Oct 11 07:59	33..8.0-19-generic|-
Fri Oct 11 07:54	33..8.0-19-generic|-
Fri Oct 11 07:43	33..8.0-19-generic|-
Fri Oct 11 01:47	33..8.0-19-generic|-
Fri Oct 11 01:26	33..8.0-19-generic|-
Thu Oct 10 23:57	33..8.0-19-generic|-
Thu Oct 10 23:34	33..8.0-19-generic|-
Thu Oct 10 23:32	33..8.0-19-generic|-
Thu Oct 10 22:44	33..8.0-19-generic|-
Thu Oct 10 23:47	33..8.0-19-generic|-
Languages
Available Languages
en_AG	English language locale for Antigua and Barbuda
en_AG.utf8	English language locale for Antigua and Barbuda
en_AU.utf8	English locale for Australia
en_BW.utf8	English locale for Botswana
en_CA.utf8	English locale for Canada
en_DK.utf8	English locale for Denmark
en_GB.utf8	English locale for Britain
en_HK.utf8	English locale for Hong Kong
en_IE.utf8	English locale for Ireland
en_IN	English language locale for India
en_IN.utf8	English language locale for India
en_NG	English locale for Nigeria
en_NG.utf8	English locale for Nigeria
en_NZ.utf8	English locale for New Zealand
en_PH.utf8	English language locale for Philippines
en_SG.utf8	English language locale for Singapore
en_US.utf8	English locale for the USA
en_ZA.utf8	English locale for South Africa
en_ZM	English locale for Zambia
en_ZM.utf8	English locale for Zambia
en_ZW.utf8	English locale for Zimbabwe
it_IT.utf8	Italian locale for Italy
Filesystems
Mounted File Systems
/dev/sda6	/	59,36 % (2,1 GiB of 5,2 GiB)
none	/sys/fs/cgroup	0,00 % (4,0 KiB of 4,0 KiB)
udev	/dev	0,00 % (986,9 MiB of 986,9 MiB)
tmpfs	/run	0,42 % (198,4 MiB of 199,2 MiB)
none	/run/lock	0,00 % (5,0 MiB of 5,0 MiB)
none	/run/shm	0,01 % (996,1 MiB of 996,2 MiB)
none	/run/user	0,01 % (100,0 MiB of 100,0 MiB)
/dev/sda2	/media/andrea/CA6063ED6063DF27	84,23 % (3,7 GiB of 23,6 GiB)
Display
Display
Resolution	1024x768 pixels
Vendor	The X.Org Foundation
Version	1.13.3
Monitors
Monitor 0	1024x768 pixels
Extensions
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
RANDR	
RECORD	
RENDER	
SECURITY	
SGI-GLX	
SHAPE	
SYNC	
X-Resource	
XC-MISC	
XFIXES	
XFree86-DGA	
XFree86-VidModeExtension	
XINERAMA	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
XVideo-MotionCompensation	
OpenGL
Vendor	Unknown
Renderer	Unknown
Version	Unknown
Direct Rendering	No
Environment Variables
Environment Variables
USER	andrea
TEXTDOMAIN	im-config
SSH_AGENT_PID	1331
HOME	/home/andrea
DESKTOP_SESSION	xubuntu
XDG_SESSION_COOKIE	19aab0b037e732690e9ddc9352572060-1381487569.309114-1915115191
XDG_SEAT_PATH	/org/freedesktop/DisplayManager/Seat0
DBUS_SESSION_BUS_ADDRESS	unix:abstract=/tmp/dbus-zi6D73V7uP,guid=fe5c62c7457d73102c25eedf5257d3d1
GLADE_MODULE_PATH	:/usr/share/glade3/pixmaps
MANDATORY_PATH	/usr/share/gconf/xubuntu.mandatory.path
LOGNAME	andrea
DEFAULTS_PATH	/usr/share/gconf/xubuntu.default.path
PATH	/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
GLADE_PIXMAP_PATH	:/usr/lib/glade3/modules
XDG_SESSION_PATH	/org/freedesktop/DisplayManager/Session0
XDG_RUNTIME_DIR	/run/user/andrea
XDG_MENU_PREFIX	xfce-
LANG	it_IT.UTF-8
XDG_CURRENT_DESKTOP	XFCE
XAUTHORITY	/home/andrea/.Xauthority
SSH_AUTH_SOCK	/run/user/andrea/keyring-l6M7J7/ssh
GLADE_CATALOG_PATH	:/usr/share/glade3/catalogs
SHELL	/bin/bash
GDMSESSION	xubuntu
TEXTDOMAINDIR	/usr/share/locale/
PWD	/home/andrea
XDG_CONFIG_DIRS	/etc/xdg/xdg-xubuntu:/etc/xdg:/etc/xdg
XDG_DATA_DIRS	/usr/share/xubuntu:/usr/local/share/:/usr/share/:/usr/share
SESSION_MANAGER	local/andrea-PX1:@/tmp/.ICE-unix/1350,unix/andrea-PX1:/tmp/.ICE-unix/1350
GNOME_KEYRING_CONTROL	/run/user/andrea/keyring-l6M7J7
GPG_AGENT_INFO	/run/user/andrea/keyring-l6M7J7/gpg:0:1
GNOME_KEYRING_PID	1399
DISPLAY	:0.0
Users
Users
root	root
daemon	daemon
bin	bin
sys	sys
sync	sync
games	games
man	man
lp	lp
mail	mail
news	news
uucp	uucp
proxy	proxy
www-data	www-data
backup	backup
list	Mailing List Manager
irc	ircd
gnats	Gnats Bug-Reporting System (admin)
nobody	nobody
libuuid	
syslog	
messagebus	
avahi-autoipd	Avahi autoip daemon
dnsmasq	dnsmasq
whoopsie	
usbmux	usbmux daemon
kernoops	Kernel Oops Tracking Daemon
rtkit	RealtimeKit
speech-dispatcher	Speech Dispatcher
lightdm	Light Display Manager
avahi	Avahi mDNS daemon
colord	colord colour management daemon
pulse	PulseAudio daemon
hplip	HPLIP system user
saned	
andrea	ANDREA
Devices
Processor
Processors
Intel(R) Atom(TM) CPU N455 @ 1.66GHz	1667,00MHz
Intel(R) Atom(TM) CPU N455 @ 1.66GHz	1000,00MHz
Memory
Memory
Total Memory	2040240 kB
Free Memory	1262216 kB
Buffers	30820 kB
Cached	437012 kB
Cached Swap	0 kB
Active	288600 kB
Inactive	409640 kB
Active(anon)	231276 kB
Inactive(anon)	74016 kB
Active(file)	57324 kB
Inactive(file)	335624 kB
Unevictable	0 kB
Mlocked	0 kB
Virtual Memory	459772 kB
Free Virtual Memory	459772 kB
Dirty	4 kB
Writeback	0 kB
AnonPages	230560 kB
Mapped	89816 kB
Shmem	74816 kB
Slab	36344 kB
SReclaimable	19204 kB
SUnreclaim	17140 kB
KernelStack	2424 kB
PageTables	16452 kB
NFS_Unstable	0 kB
Bounce	0 kB
WritebackTmp	0 kB
CommitLimit	1479892 kB
Committed_AS	1450512 kB
VmallocTotal	34359738367 kB
VmallocUsed	533828 kB
VmallocChunk	34359201787 kB
HardwareCorrupted	0 kB
AnonHugePages	0 kB
HugePages_Total	0
HugePages_Free	0
HugePages_Rsvd	0
HugePages_Surp	0
Hugepagesize	2048 kB
DirectMap4k	48704 kB
DirectMap2M	2037760 kB
PCI Devices
PCI Devices
Host bridge	Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
VGA compatible controller	Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (prog-if 00 [VGA controller])
Display controller	Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
Audio device	Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
PCI bridge	Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
USB controller	Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
USB controller	Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
USB controller	Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
USB controller	Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
USB controller	Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
PCI bridge	Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
ISA bridge	Intel Corporation NM10 Family LPC Controller (rev 02)
IDE interface	Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
SMBus	Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
Ethernet controller	Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
USB Devices
Printers
Printers
No printers found	
Battery
No batteries
No batteries found on this system	
Sensors
Input Devices
Input Devices
Sleep Button	
Lid Switch	
Power Button	
Power Button	
AT Translated Set 2 keyboard	
Gotek4Tainell	
Video Bus	
HDA Intel Mic	
HDA Intel Front Headphone	
USB Optical Mouse	
CDT 9.75	
GASIA USB Keyboard	
GASIA USB Keyboard	
Storage
SCSI Disks
ATA SuperSSpeed 32GB	
DMI
BIOS
Date	05/05/2012
Vendor	American Megatrends Inc. (www.ami.com)
Version	080016
Board
Name	PX1
Vendor	THD(Thread technology)
Resources
I/O Ports
0000-0cf7 	PCI Bus 0000:00
0000-001f 	dma1
0020-0021 	pic1
0040-0043 	timer0
0050-0053 	timer1
0060-0060 	keyboard
0062-0062 	EC data
0064-0064 	keyboard
0066-0066 	EC cmd
0070-0071 	rtc0
0080-008f 	dma page reg
00a0-00a1 	pic2
00c0-00df 	dma2
00f0-00ff 	fpu
0170-0177 	Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
0170-0177 	ata_piix
01f0-01f7 	Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
01f0-01f7 	ata_piix
0376-0376 	Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
0376-0376 	ata_piix
03f6-03f6 	Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
03f6-03f6 	ata_piix
0400-041f 	Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
0480-04bf 	GPIO interface for Intel ICH series
0480-04bf 	pnp 00:06
04d0-04d1 	pnp 00:06
0cf8-0cff 	PCI conf1
0d00-ffff 	PCI Bus 0000:00
1000-107f 	pnp 00:06
1000-1003 	ACPI PM1a_EVT_BLK
1004-1005 	ACPI PM1a_CNT_BLK
1008-100b 	ACPI PM_TMR
1010-1015 	ACPI CPU throttle
1020-1020 	ACPI PM2_CNT_BLK
1028-102f 	GPIO interface for Intel ICH series
1028-102f 	ACPI GPE0_BLK
1030-1033 	iTCO_wdt
1060-107f 	iTCO_wdt
2000-2fff 	PCI Bus 0000:01
e400-e41f 	Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
e400-e41f 	uhci_hcd
e480-e49f 	Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
e480-e49f 	uhci_hcd
e800-e81f 	Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
e800-e81f 	uhci_hcd
e880-e89f 	Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
e880-e89f 	uhci_hcd
ec00-ec07 	Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (prog-if 00 [VGA controller])
ff90-ff9f 	Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
ff90-ff9f 	ata_piix
Memory
00000000-0000ffff 	reserved
00010000-0009fbff 	System RAM
0009fc00-0009ffff 	reserved
000a0000-000bffff 	PCI Bus 0000:00
000c0000-000c7fff 	Video ROM
000d0000-000dffff 	PCI Bus 0000:00
000e0000-000fffff 	reserved
000f0000-000fffff 	System ROM
00100000-7f58ffff 	System RAM
01000000-016d7927 	Kernel code
016d7928-01cef2ff 	Kernel data
01df0000-01f27fff 	Kernel bss
7f590000-7f59dfff 	ACPI Tables
7f59e000-7f5cffff 	ACPI Non-volatile Storage
7f5d0000-7f5dffff 	reserved
7f5e0000-7f5e7fff 	RAM buffer
7f5e8000-dfffffff 	reserved
7f700000-dfffffff 	PCI Bus 0000:00
80000000-801fffff 	PCI Bus 0000:01
80200000-802003ff 	Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
80201000-80201fff 	Intel Flush Page
80204000-80207fff 	i915 MCHBAR
d0000000-dfffffff 	Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (prog-if 00 [VGA controller])
e0000000-efffffff 	PCI MMCONFIG 0000 [bus 00-ff]
e0000000-efffffff 	pnp 00:0b
f0000000-fed8ffff 	PCI Bus 0000:00
fe880000-fe8fffff 	Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
fe977c00-fe977fff 	Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
fe977c00-fe977fff 	ehci_hcd
fe978000-fe97bfff 	Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
fe978000-fe97bfff 	ICH HD audio
fe980000-fe9fffff 	Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (prog-if 00 [VGA controller])
fea00000-feafffff 	Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (prog-if 00 [VGA controller])
feb00000-febfffff 	PCI Bus 0000:01
febf0000-febfffff 	Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
febf0000-febfffff 	Support for 5xxx series of Atheros 802.11 wireless LAN cards.
fec00000-fec003ff 	IOAPIC 0
fed00000-fed003ff 	HPET 0
fed14000-fed19fff 	pnp 00:00
fed1c000-fed1ffff 	pnp 00:06
fed1f410-fed1f414 	iTCO_wdt
fed20000-fed8ffff 	pnp 00:06
fed90000-fed93fff 	pnp 00:00
fee00000-fee00fff 	Local APIC
fee00000-fee00fff 	reserved
fee00000-fee00fff 	pnp 00:0a
ffb00000-ffffffff 	reserved
ffc00000-ffefffff 	pnp 00:09
DMA
4	cascade
```

---

### Post by swedenfox on 2013-10-13
doing lsusb -v 

i discovered that the family of this SD card reader is 
**UB623X** from ENE Tecnology .

I Tried this card reader with Windows 7 , it works   with the same card inserted 

some discussion talking about but not solved 
-http://forum.ubuntu-it.org/viewtopic.php?t=484031

---

### Post by bronze2 on 2013-10-15
Hi

It seems we may have the same tablet with CDT 9.75 hid touchscreen.   Could yu detail your configuration methods and config files for it.  I am running precise 5.7.1 dual boot with ubuntu.  Can you emulate right click?

thanks

Marcos

---

### Post by swedenfox on 2013-11-15
hi marcos

i just installed xubuntu 13.04 and works 

my xinput 

> Device 'CDT      9.75 ':
	Device Enabled (134):	1
	Coordinate Transformation Matrix (136):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (259):	0
	Device Accel Constant Deceleration (260):	1.000000
	Device Accel Adaptive Deceleration (261):	1.000000
	Device Accel Velocity Scaling (262):	10.000000
	Device Product ID (251):	1003, 8220
	Device Node (252):	"/dev/input/event7"
	Evdev Axis Inversion (263):	0, 0
	Evdev Axis Calibration (264):	-9, 16439, 21, 12201
	Evdev Axes Swap (265):	0
	Axis Labels (266):	"Abs MT Position X" (257), "Abs MT Position Y" (258), "None" (0), "None" (0)
	Button Labels (267):	"Button Unknown" (254), "Button Unknown" (254), "Button Unknown" (254), "Button Wheel Up" (140), "Button Wheel Down" (141)
	Evdev Middle Button Emulation (268):	0
	Evdev Middle Button Timeout (269):	50
	Evdev Third Button Emulation (270):	0
	Evdev Third Button Emulation Timeout (271):	1000
	Evdev Third Button Emulation Button (272):	3
	Evdev Third Button Emulation Threshold (273):	20
	Evdev Wheel Emulation (274):	0
	Evdev Wheel Emulation Axes (275):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (276):	10
	Evdev Wheel Emulation Timeout (277):	200
	Evdev Wheel Emulation Button (278):	4
	Evdev Drag Lock Buttons (279):	0


---

