---
title: "Ubuntu 9.10 crashes on Dell Latitude E6400 with cisco vpn"
date: 2009-11-05
forum: Hardware
---

### Post by prantor on 2009-11-05
Ubuntu 9.10 crashes on Dell Latitude E6400 when cisco vpn is on. The Capes lock and Num lock LEDs will start blinking and the Ubuntu will crash. It happens on once or twice a day.

I am not 100% sure it is because of VPN or not, but OS crashing is scary. 


Computer 
********
Summary
-------
-Computer-
Processor		: 2x Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
Memory		: 3566MB (839MB used)
Operating System		: Ubuntu 9.10
User Name		: pbora (pbora)
Date/Time		: Thu 05 Nov 2009 02:54:44 PM CST
-Display-
Resolution		: 1440x900 pixels
OpenGL Renderer		: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA Intel
-Input Devices-
 Lid Switch
 Power Button
 Sleep Button
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 HID 413c:8157
 Video Bus
 Video Bus
 Dell WMI hotkeys
 PS/2 Generic Mouse
 HDA Digital PCBeep
 HDA Intel Mic at Sep Left Jack
 HDA Intel Mic at Ext Right Jack
 HDA Intel Line Out at Sep Left Jack
 HDA Intel HP Out at Ext Right Jack
-Printers (CUPS)-
Canon-imageRunner-3025		: <i>Default</i>
-SCSI Disks-
ATA Hitachi HTS72321
TSSTcorp DVD+-RW TS-U633A
ST910082 4A

Operating System
----------------

-Version-
Kernel		: Linux 2.6.31-14-generic (i686)
Compiled		: #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009
C Library		: GNU C Library version 2.10.1 (stable)
Default C Compiler		: GNU C Compiler version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
Distribution		: Ubuntu 9.10
-Current Session-
Computer Name		: pbora-lap
User Name		: pbora (pbora)
Home Directory		: /home/pbora
Desktop Environment		: GNOME 2.28.1
-Misc-
Uptime		: 23 minutes
Load Average		: 0.75, 0.77, 0.79

Kernel Modules
--------------

-Loaded Modules-
nls_iso8859_1
nls_cp437
vfat		: VFAT filesystem support
fat
binfmt_misc
bridge
stp
bnep		: Bluetooth BNEP ver 1.3
cisco_ipsec
vboxnetflt		: VirtualBox Network Filter Driver
vboxnetadp		: VirtualBox Network Adapter Driver
vboxdrv		: VirtualBox Support Driver
vmnet		: VMware Virtual Networking Driver.
ppdev
parport_pc		: PC-style parallel port driver
vmblock		: VMware Blocking File System
vsock		: VMware Virtual Socket Family
vmci		: VMware Virtual Machine Communication Interface (VMCI).
vmmon		: VMware Virtual Machine Monitor.
snd_hda_codec_intelhdmi		: Intel HDMI HD-audio codec
snd_hda_codec_idt		: IDT/Sigmatel HD-audio codec
snd_hda_intel		: Intel HDA driver
snd_hda_codec		: HDA codec core
snd_hwdep		: Hardware dependent layer
snd_pcm_oss		: PCM OSS emulation for ALSA.
snd_mixer_oss		: Mixer OSS emulation for ALSA.
snd_pcm		: Midlevel PCM code for ALSA.
snd_seq_dummy		: ALSA sequencer MIDI-through client
snd_seq_oss		: OSS-compatible sequencer module
snd_seq_midi		: Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi		: Midlevel RawMidi code for ALSA.
snd_seq_midi_event		: MIDI byte &lt;-&gt; sequencer event coder
snd_seq		: Advanced Linux Sound Architecture sequencer.
snd_timer		: ALSA timer interface
snd_seq_device		: ALSA sequencer device management
dell_wmi		: Dell laptop WMI hotkeys driver
lib80211_crypt_tkip		: lib80211 crypt: TKIP
psmouse		: PS/2 mouse driver
iptable_filter		: iptables filter table
dell_laptop		: Dell laptop driver
sdhci_pci		: Secure Digital Host Controller Interface PCI driver
snd		: Advanced Linux Sound Architecture driver for soundcards.
wl
ip_tables		: IPv4 packet filter
soundcore		: Core sound module
sdhci		: Secure Digital Host Controller Interface core driver
ricoh_mmc		: Ricoh MMC Controller disabling driver
serio_raw		: Raw serio driver
led_class		: LED Class Interface
snd_page_alloc		: Memory allocator for ALSA system.
btusb		: Generic Bluetooth USB driver ver 0.5
lp
lib80211		: common routines for IEEE802.11 drivers
dcdbas		: Dell Systems Management Base Driver (version 5.6.0-3.2)
x_tables		: {ip,ip6,arp,eb}_tables backend module
parport
fbcon
tileblit		: Tile Blitting Operation
font		: Console Fonts
bitblit		: Bit Blitting Operation
softcursor		: Generic software cursor
i915		: Intel Graphics
drm		: DRM shared core routines
i2c_algo_bit		: I2C-Bus bit-banging algorithm
usbhid		: USB HID core driver
usb_storage		: USB Mass Storage driver for Linux
ohci1394		: Driver for PCI OHCI IEEE-1394 controllers
intel_agp
agpgart		: AGP GART driver
e1000e		: Intel(R) PRO/1000 Network Driver
ieee1394
video		: ACPI Video Driver
output		: Display Output Switcher Lowlevel Control Abstraction

Boots
-----

-Boots-
Thu Nov 5 14:31		: 2.6.31-14-generi|-
Thu Nov 5 08:25		: 2.6.31-14-generi|-
Thu Nov 5 08:21		: 2.6.31-14-generi|-
Thu Nov 5 08:17		: 2.6.31-14-generi|-
Wed Nov 4 23:12		: 2.6.31-14-generi|-
Wed Nov 4 19:27		: 2.6.31-14-generi|-
Wed Nov 4 08:13		: 2.6.31-14-generi|-
Tue Nov 3 19:35		: 2.6.31-14-generi|-
Tue Nov 3 19:28		: 2.6.31-14-generi|-
Tue Nov 3 19:27		: 2.6.31-14-generi|-
Tue Nov 3 19:25		: 2.6.31-14-generi|-
Tue Nov 3 10:37		: 2.6.31-14-generi|-
Tue Nov 3 07:47		: 2.6.31-14-generi|-
Mon Nov 2 19:34		: 2.6.31-14-generi|-
Mon Nov 2 07:34		: 2.6.31-14-generi|-
Sun Nov 1 09:03		: 2.6.31-14-generi|-
Sun Nov 1 08:55		: 2.6.31-14-generi|-

Languages
---------

-Available Languages-
en_AG		: English language locale for Antigua and Barbuda
en_AU.utf8		: English locale for Australia
en_BW.utf8		: English locale for Botswana
en_CA.utf8		: English locale for Canada
en_DK.utf8		: English locale for Denmark
en_GB.utf8		: English locale for Britain
en_HK.utf8		: English locale for Hong Kong
en_IE.utf8		: English locale for Ireland
en_IN		: English language locale for India
en_NG		: English locale for Nigeria
en_NZ.utf8		: English locale for New Zealand
en_PH.utf8		: English language locale for Philippines
en_SG.utf8		: English language locale for Singapore
en_US.utf8		: English locale for the USA
en_ZA.utf8		: English locale for South Africa

Filesystems
-----------

-Mounted File Systems-
/dev/sda1	/	53.42 % (65.5 GiB of 140.7 GiB)	
udev	/dev	0.02 % (1.7 GiB of 1.7 GiB)	
none	/dev/shm	0.01 % (1.7 GiB of 1.7 GiB)	
none	/var/run	0.01 % (1.7 GiB of 1.7 GiB)	
none	/var/lock	0.00 % (1.7 GiB of 1.7 GiB)	
none	/lib/init/rw	0.00 % (1.7 GiB of 1.7 GiB)	
/dev/sdb5	/media/SEA_DISC	59.20 % (38.0 GiB of 93.1 GiB)	

Display
-------

-Display-
Resolution		: 1440x900 pixels
Vendor		: The X.Org Foundation
Version		: 1.6.4
-Monitors-
Monitor 0		: 1440x900 pixels
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
-OpenGL-
Vendor		: Tungsten Graphics, Inc
Renderer		: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
Version		: 2.1 Mesa 7.6
Direct Rendering		: Yes

Environment Variables
---------------------

-Environment Variables-
GDM_KEYBOARD_LAYOUT		: us
GNOME_KEYRING_PID		: 2141
USER		: pbora
GNOME_KEYRING_SOCKET		: /tmp/keyring-nCfuDk/socket
SSH_AGENT_PID		: 2199
HOME		: /home/pbora
DESKTOP_SESSION		: gnome
XDG_SESSION_COOKIE		: e3bd56f149f96353349d5cd24ab7e26f-1257453123.1918-1049944220
GTK_MODULES		: canberra-gtk-module
DBUS_SESSION_BUS_ADDRESS		: unix:abstract=/tmp/dbus-RyqyT5nYqU,guid=7033206ad19ba0598f93f2ca4af33643
LOGNAME		: pbora
USERNAME		: pbora
GDM_LANG		: en_US.UTF-8
PATH		: /home/pbora/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/pbora/myinstalls/unixtools/devtools/groovy-1.6.4/bin:
DISPLAY		: :0.0
LANG		: en_US.UTF-8
XAUTHORITY		: /var/run/gdm/auth-for-pbora-iuHPsV/database
SSH_AUTH_SOCK		: /tmp/keyring-nCfuDk/socket.ssh
SHELL		: /bin/bash
GDMSESSION		: gnome
PWD		: /home/pbora
SPEECHD_PORT		: 7560
XDG_DATA_DIRS		: /usr/share/gnome:/usr/local/share/:/usr/share/
GPG_AGENT_INFO		: /tmp/seahorse-oNlwtt/S.gpg-agent:2222:1
GNOME_DESKTOP_SESSION_ID		: this-is-deprecated
SESSION_MANAGER		: local/pbora-lap:@/tmp/.ICE-unix/2156,unix/pbora-lap:/tmp/.ICE-unix/2156
ORBIT_SOCKETDIR		: /tmp/orbit-pbora
GTK_RC_FILES		: /etc/gtk/gtkrc:/home/pbora/.gtkrc-1.2-gnome2

Users
-----

-Users-
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
libuuid
syslog
klog
hplip		: HPLIP system user
avahi-autoipd		: Avahi autoip daemon
gdm		: Gnome Display Manager
saned
pulse		: PulseAudio daemon
messagebus
polkituser		: PolicyKit
avahi		: Avahi mDNS daemon
haldaemon		: Hardware abstraction layer
pbora		: pbora
sshd
speech-dispatcher		: Speech Dispatcher
couchdb		: CouchDB Administrator
kernoops		: Kernel Oops Tracking Daemon

Devices
*******


Processor
---------

-Processors-
Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz		: 800.00MHz
Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz		: 2668.00MHz

Memory
------

-Memory-
Total Memory		: 3566440 kB
Free Memory		: 116648 kB
Buffers		: 9576 kB
Cached		: 2620652 kB
Cached Swap		: 37468 kB
Active		: 1915064 kB
Inactive		: 1354644 kB
Active(anon)		: 610248 kB
Inactive(anon)		: 197180 kB
Active(file)		: 1304816 kB
Inactive(file)		: 1157464 kB
Unevictable		: 0 kB
Mlocked		: 0 kB
High Memory		: 2711868 kB
Free High Memory		: 3224 kB
Low Memory		: 854572 kB
Free Low Memory		: 113424 kB
Virtual Memory		: 6385796 kB
Free Virtual Memory		: 6254232 kB
Dirty		: 748 kB
Writeback		: 0 kB
AnonPages		: 611012 kB
Mapped		: 603284 kB
Slab		: 133368 kB
SReclaimable		: 119408 kB
SUnreclaim		: 13960 kB
PageTables		: 7244 kB
NFS_Unstable		: 0 kB
Bounce		: 0 kB
WritebackTmp		: 0 kB
CommitLimit		: 8169016 kB
Committed_AS		: 1759400 kB
VmallocTotal		: 122880 kB
VmallocUsed		: 22480 kB
VmallocChunk		: 69132 kB
HugePages_Total		: 0
HugePages_Free		: 0
HugePages_Rsvd		: 0
HugePages_Surp		: 0
Hugepagesize		: 4096 kB
DirectMap4k		: 16376 kB
DirectMap4M		: 892928 kB

PCI Devices
-----------

-PCI Devices-
Host bridge		: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub 
VGA compatible controller		: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller 
Display controller		: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller 
Ethernet controller		: Intel Corporation 82567LM Gigabit Network Connection 
USB Controller		: Intel Corporation 82801I 
USB Controller		: Intel Corporation 82801I 
USB Controller		: Intel Corporation 82801I 
USB Controller		: Intel Corporation 82801I 
Audio device		: Intel Corporation 82801I 
PCI bridge		: Intel Corporation 82801I 
PCI bridge		: Intel Corporation 82801I 
PCI bridge		: Intel Corporation 82801I 
PCI bridge		: Intel Corporation 82801I 
USB Controller		: Intel Corporation 82801I 
USB Controller		: Intel Corporation 82801I 
USB Controller		: Intel Corporation 82801I 
USB Controller		: Intel Corporation 82801I 
PCI bridge		: Intel Corporation 82801 Mobile PCI Bridge 
ISA bridge		: Intel Corporation ICH9M-E LPC Interface Controller 
SATA controller		: Intel Corporation ICH9M/M-E SATA AHCI Controller 
SMBus		: Intel Corporation 82801I 
FireWire (IEEE 1394)		: Ricoh Co Ltd R5C832 IEEE 1394 Controller 
SD Host controller		: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter 
System peripheral		: Ricoh Co Ltd R5C843 MMC Host Controller 
Network controller		: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller 

USB Devices
-----------


Printers
--------

-Printers (CUPS)-
Canon-imageRunner-3025		: <i>Default</i>

Battery
-------

-Battery: BAT0-
State		: charged (load: 1 mA)
Capacity		: 5200 mAh / 5200 mAh (100.00%)
Battery Technology		: rechargeable (LION)
Model Number		: DELL KY26698
Serial Number		: 5941

Sensors
-------

-ACPI Thermal Zone-
THM		: 40°C

Input Devices
-------------

-Input Devices-
 Lid Switch
 Power Button
 Sleep Button
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 HID 413c:8157
 Video Bus
 Video Bus
 Dell WMI hotkeys
 PS/2 Generic Mouse
 HDA Digital PCBeep
 HDA Intel Mic at Sep Left Jack
 HDA Intel Mic at Ext Right Jack
 HDA Intel Line Out at Sep Left Jack
 HDA Intel HP Out at Ext Right Jack

Storage
-------

-SCSI Disks-
ATA Hitachi HTS72321
TSSTcorp DVD+-RW TS-U633A
ST910082 4A

DMI
---

-BIOS-
Date		: 05/11/2009
Vendor		: Dell Inc.
Version		: A14
-Board-
Name		: 0U692R
Vendor		: Dell Inc.

Resources
---------

-I/O Ports-
<tt>0000-001f </tt>		: dma1
<tt>0020-0021 </tt>		: pic1
<tt>0040-0043 </tt>		: timer0
<tt>0050-0053 </tt>		: timer1
<tt>0060-0060 </tt>		: keyboard
<tt>0064-0064 </tt>		: keyboard
<tt>0070-0071 </tt>		: rtc0
<tt>0080-008f </tt>		: dma page reg
<tt>00a0-00a1 </tt>		: pic2
<tt>00c0-00df </tt>		: dma2
<tt>00f0-00ff </tt>		: fpu
<tt>02f8-02ff </tt>		: serial
<tt>03c0-03df </tt>		: vga+
<tt>04d0-04d1 </tt>		: pnp 00:0b
<tt>0809-0809 </tt>		: pnp 00:0c
<tt>0900-092f </tt>		: pnp 00:0b
<tt>0931-0933 </tt>		: pnp 00:0b
<tt>0935-097f </tt>		: pnp 00:0b
<tt>0c80-0caf </tt>		: pnp 00:05
<tt>0cb0-0cbb </tt>		: pnp 00:0a
<tt>0cf8-0cff </tt>		: PCI conf1
<tt>1000-1005 </tt>		: pnp 00:0b
<tt>  1000-1003 </tt>		: ACPI PM1a_EVT_BLK
<tt>  1004-1005 </tt>		: ACPI PM1a_CNT_BLK
<tt>1006-1007 </tt>		: pnp 00:0c
<tt>1008-100f </tt>		: pnp 00:0b
<tt>  1008-100b </tt>		: ACPI PM_TMR
<tt>1010-102f </tt>		: pnp 00:0c
<tt>  1010-1015 </tt>		: ACPI CPU throttle
<tt>  1020-102f </tt>		: ACPI GPE0_BLK
<tt>1050-1050 </tt>		: ACPI PM2_CNT_BLK
<tt>1060-107f </tt>		: pnp 00:0c
<tt>1080-10bf </tt>		: pnp 00:0c
<tt>1100-111f </tt>		: Intel Corporation 82801I 
<tt>  1100-111f </tt>		: pnp 00:0c
<tt>6e70-6e77 </tt>		: Intel Corporation ICH9M/M-E SATA AHCI Controller 
<tt>  6e70-6e77 </tt>		: ahci
<tt>6e78-6e7b </tt>		: Intel Corporation ICH9M/M-E SATA AHCI Controller 
<tt>  6e78-6e7b </tt>		: ahci
<tt>6e80-6e87 </tt>		: Intel Corporation ICH9M/M-E SATA AHCI Controller 
<tt>  6e80-6e87 </tt>		: ahci
<tt>6e88-6e8b </tt>		: Intel Corporation ICH9M/M-E SATA AHCI Controller 
<tt>  6e88-6e8b </tt>		: ahci
<tt>6ea0-6ebf </tt>		: Intel Corporation ICH9M/M-E SATA AHCI Controller 
<tt>  6ea0-6ebf </tt>		: ahci
<tt>6f00-6f1f </tt>		: Intel Corporation 82801I 
<tt>  6f00-6f1f </tt>		: uhci_hcd
<tt>6f20-6f3f </tt>		: Intel Corporation 82801I 
<tt>  6f20-6f3f </tt>		: uhci_hcd
<tt>6f40-6f5f </tt>		: Intel Corporation 82801I 
<tt>  6f40-6f5f </tt>		: uhci_hcd
<tt>6f60-6f7f </tt>		: Intel Corporation 82801I 
<tt>  6f60-6f7f </tt>		: uhci_hcd
<tt>6f80-6f9f </tt>		: Intel Corporation 82801I 
<tt>  6f80-6f9f </tt>		: uhci_hcd
<tt>6fa0-6fbf </tt>		: Intel Corporation 82801I 
<tt>  6fa0-6fbf </tt>		: uhci_hcd
<tt>d000-dfff </tt>		: PCI Bus 0000:0e
<tt>ef98-ef9f </tt>		: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller 
<tt>efe0-efff </tt>		: Intel Corporation 82567LM Gigabit Network Connection 
<tt>f400-f4fe </tt>		: pnp 00:0c
-Memory-
<tt>00000000-00001fff </tt>		: System RAM
<tt>00002000-00005fff </tt>		: reserved
<tt>00006000-0009efff </tt>		: System RAM
<tt>0009f000-0009ffff </tt>		: reserved
<tt>000a0000-000bffff </tt>		: Video RAM area
<tt>000c0000-000c7fff </tt>		: Video ROM
<tt>000cf800-000cffff </tt>		: Adapter ROM
<tt>000f0000-000fffff </tt>		: System ROM
<tt>00100000-dd04d3ff </tt>		: System RAM
<tt>  00100000-00575553 </tt>		: Kernel code
<tt>  00575554-0078d307 </tt>		: Kernel data
<tt>  0081a000-008a809f </tt>		: Kernel bss
<tt>dd04d400-dd04f3ff </tt>		: ACPI Non-volatile Storage
<tt>dd04f400-dfffffff </tt>		: reserved
<tt>  ddb00000-ddbfffff </tt>		: pnp 00:0d
<tt>e0000000-efffffff </tt>		: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller 
<tt>f0000000-f01fffff </tt>		: PCI Bus 0000:0e
<tt>f0200000-f0200fff </tt>		: Intel Flush Page
<tt>f6500000-f65fffff </tt>		: PCI Bus 0000:03
<tt>  f65ff600-f65ff6ff </tt>		: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter 
<tt>    f65ff600-f65ff6ff </tt>		: mmc0
<tt>  f65ff700-f65ff7ff </tt>		: Ricoh Co Ltd R5C843 MMC Host Controller 
<tt>  f65ff800-f65fffff </tt>		: Ricoh Co Ltd R5C832 IEEE 1394 Controller 
<tt>    f65ff800-f65fffff </tt>		: Driver for PCI OHCI IEEE-1394 controllers
<tt>f6600000-f68fffff </tt>		: PCI Bus 0000:0e
<tt>f6900000-f69fffff </tt>		: PCI Bus 0000:0c
<tt>  f69fc000-f69fffff </tt>		: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller 
<tt>f6adaf00-f6adafff </tt>		: Intel Corporation 82801I 
<tt>f6adb000-f6adbfff </tt>		: Intel Corporation 82567LM Gigabit Network Connection 
<tt>  f6adb000-f6adbfff </tt>		: Intel(R) PRO/1000 Network Driver
<tt>f6adc000-f6adffff </tt>		: Intel Corporation 82801I 
<tt>  f6adc000-f6adffff </tt>		: ICH HD audio
<tt>f6ae0000-f6afffff </tt>		: Intel Corporation 82567LM Gigabit Network Connection 
<tt>  f6ae0000-f6afffff </tt>		: Intel(R) PRO/1000 Network Driver
<tt>f6b00000-f6bfffff </tt>		: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller 
<tt>f6c00000-f6ffffff </tt>		: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller 
<tt>f8000000-fbffffff </tt>		: PCI MMCONFIG 0 [00-3f]
<tt>  f8000000-fbffffff </tt>		: reserved
<tt>    f8000000-fbffffff </tt>		: pnp 00:0d
<tt>fec00000-fec0ffff </tt>		: reserved
<tt>  fec00000-fec00fff </tt>		: IOAPIC 0
<tt>fed00000-fed003ff </tt>		: HPET 0
<tt>  fed00000-fed003ff </tt>		: pnp 00:08
<tt>fed18000-fed1bfff </tt>		: reserved
<tt>  fed18000-fed1bfff </tt>		: pnp 00:0d
<tt>fed1c000-fed1c3ff </tt>		: Intel Corporation 82801I 
<tt>  fed1c000-fed1c3ff </tt>		: ehci_hcd
<tt>fed1c400-fed1c7ff </tt>		: Intel Corporation 82801I 
<tt>  fed1c400-fed1c7ff </tt>		: ehci_hcd
<tt>fed1c800-fed1cfff </tt>		: Intel Corporation ICH9M/M-E SATA AHCI Controller 
<tt>  fed1c800-fed1cfff </tt>		: pnp 00:0d
<tt>    fed1c800-fed1cfff </tt>		: ahci
<tt>fed20000-fed8ffff </tt>		: reserved
<tt>  fed20000-fed3ffff </tt>		: pnp 00:0d
<tt>  fed40000-fed44fff </tt>		: pnp 00:0a
<tt>  fed45000-fed8ffff </tt>		: pnp 00:0d
<tt>feda0000-feda5fff </tt>		: reserved
<tt>  feda0000-feda3fff </tt>		: pnp 00:0d
<tt>  feda4000-feda4fff </tt>		: pnp 00:0d
<tt>  feda5000-feda5fff </tt>		: pnp 00:0d
<tt>feda6000-feda6fff </tt>		: pnp 00:0d
<tt>fee00000-fee0ffff </tt>		: reserved
<tt>  fee00000-fee0ffff </tt>		: pnp 00:0d
<tt>    fee00000-fee00fff </tt>		: Local APIC
<tt>ffa00000-ffbfffff </tt>		: pnp 00:0d
<tt>ffe60000-ffffffff </tt>		: reserved
-DMA-
<tt> 4</tt>		: cascade

Network
*******


Interfaces
----------

-Network Interfaces-
lo	0.04MiB	0.04MiB	127.0.0.1	
eth0	0.00MiB	0.00MiB		
eth1	11.19MiB	2.04MiB	10.0.0.4	
vmnet1	0.00MiB	0.00MiB	172.16.100.1	
vmnet8	0.00MiB	0.00MiB	192.168.63.1	
vboxnet0	0.00MiB	0.00MiB		
cipsec0	0.00MiB	0.00MiB		
pan0	0.00MiB	0.00MiB		

IP Connections
--------------

-Connections-
0.0.0.0:22	LISTEN	0.0.0.0:*	tcp	
127.0.0.1:631	LISTEN	0.0.0.0:*	tcp	
10.0.0.4:48474	ESTABLISHED	74.125.95.91:80	tcp	
10.0.0.4:41403	ESTABLISHED	66.35.213.231:80	tcp	
10.0.0.4:47147	ESTABLISHED	74.125.47.109:993	tcp	
10.0.0.4:33946	ESTABLISHED	74.125.65.125:5222	tcp	
10.0.0.4:35375	CLOSE_WAIT	72.247.203.51:443	tcp	
10.0.0.4:34084	ESTABLISHED	207.195.205.22:80	tcp	
10.0.0.4:34083	ESTABLISHED	207.195.205.22:80	tcp	
10.0.0.4:35376	CLOSE_WAIT	72.247.203.51:443	tcp	
10.0.0.4:48475	ESTABLISHED	74.125.95.91:80	tcp	
10.0.0.4:54850	ESTABLISHED	207.46.124.243:1863	tcp	
10.0.0.4:48473	ESTABLISHED	74.125.95.91:80	tcp	
10.0.0.4:34086	ESTABLISHED	207.195.205.22:80	tcp	
10.0.0.4:36408	ESTABLISHED	74.125.95.164:80	tcp	
10.0.0.4:48038	ESTABLISHED	74.125.95.106:80	tcp	
10.0.0.4:34082	ESTABLISHED	207.195.205.22:80	tcp	
10.0.0.4:56733	ESTABLISHED	74.125.95.190:80	tcp	
10.0.0.4:41199	ESTABLISHED	64.4.9.58:1863	tcp	
10.0.0.4:56336	TIME_WAIT	74.125.95.83:80	tcp	
10.0.0.4:57955	ESTABLISHED	141.146.46.32:993	tcp	
10.0.0.4:34085	ESTABLISHED	207.195.205.22:80	tcp	
10.0.0.4:56731	ESTABLISHED	74.125.95.190:80	tcp	
10.0.0.4:56732	ESTABLISHED	74.125.95.190:80	tcp	
10.0.0.4:40059	ESTABLISHED	74.125.65.125:5222	tcp	
10.0.0.4:48472	ESTABLISHED	74.125.95.91:80	tcp	
10.0.0.4:33433	ESTABLISHED	76.13.15.45:5050	tcp	
10.0.0.4:48477	ESTABLISHED	74.125.95.91:80	tcp	
10.0.0.4:40064	ESTABLISHED	74.125.65.125:5222	tcp	
10.0.0.4:34068	ESTABLISHED	207.195.205.22:80	tcp	
10.0.0.4:49732	ESTABLISHED	74.125.95.19:80	tcp	
10.0.0.4:48476	ESTABLISHED	74.125.95.91:80	tcp	
10.0.0.4:48039	ESTABLISHED	74.125.95.106:80	tcp	
10.0.0.4:35378	CLOSE_WAIT	72.247.203.51:443	tcp	
10.0.0.4:35377	CLOSE_WAIT	72.247.203.51:443	tcp	
:::5900	LISTEN	:::*	tcp6	
:::22	LISTEN	:::*	tcp6	
::1:631	LISTEN	:::*	tcp6	
0.0.0.0:5353		0.0.0.0:*	udp	
0.0.0.0:47620		0.0.0.0:*	udp	
0.0.0.0:49563		0.0.0.0:*	udp	

Routing Table
-------------

-IP routing table-
172.16.100.0 / 0.0.0.0	255.255.255.0	U	vmnet1	
10.0.0.0 / 0.0.0.0	255.255.255.0	U	eth1	
192.168.63.0 / 0.0.0.0	255.255.255.0	U	vmnet8	
169.254.0.0 / 0.0.0.0	255.255.0.0	U	eth1	
0.0.0.0 / 10.0.0.1	0.0.0.0	UG	eth1	

ARP Table
---------

-ARP Table-
10.0.0.1	00:05:5e:9f:e9:d2	eth1	

DNS Servers
-----------

-Name servers-
199.199.195.5

Statistics
----------

-IP-
12310		: Total packets received
1		: With invalid addresses
0		: Incoming packets discarded
0		: Incoming packets discarded
12307		: Incoming packets delivered
12811		: Requests sent out
20		: Dropped because of missing route
-ICMP-
19		: ICMP messages received
10		: Input ICMP message failed.
0		: ICMP messages failed
0		: ICMP messages failed
-ICMPMSG-
-TCP-
615		: Active connections openings
33		: Passive connection openings
11		: Failed connection attempts
5		: Bad segments received.
28		: Connections established
11764		: Segments received
12125		: Segments send out
139		: Segments retransmited
5		: Bad segments received.
69		: Resets sent
-UDP-
670		: Packets received
0		: Packet receive errors
0		: Packet receive errors
706		: Packets sent
-UDPLITE-
-TCPEXT-
435		: TCP sockets finished time wait in fast timer
1		: DSACKs sent for out of order packets
359		: Delayed acks sent
1		: DSACKs sent for out of order packets
28		: Packets directly queued to recvmsg prequeue.
12853		: Bytes directly received in process context from prequeue
6382		: Packet headers predicted
30		: Packets header predicted and directly queued to user
1187		: Acknowledgments not containing data payload received
159		: Predicted acknowledgments
37		: Congestion windows recovered without slow start after partial ack
4		: Connections aborted due to timeout
3		: Connections reset due to early user close
103		: Other TCP timeouts
98		: DSACKs sent for old packets
1		: DSACKs sent for out of order packets
13		: DSACKs received
17		: Connections reset due to unexpected data
3		: Connections reset due to early user close
4		: Connections aborted due to timeout
-IPEXT-

Shared Directories
------------------

-SAMBA-
-NFS-

Benchmarks
**********


CPU Blowfish
------------

-CPU Blowfish-
<big><b>This Machine</b></big>	800 MHz	6.983	
Intel(R) Celeron(R) M processor         1.50GHz	(null)	26.1876862	
PowerPC 740/750 (280.00MHz)	(null)	172.816713	

CPU CryptoHash
--------------

-CPU Cryptohash-
<big><b>This Machine</b></big>	800 MHz	188.918	

CPU Fibonacci
-------------

-CPU Fibonacci-
<big><b>This Machine</b></big>	800 MHz	2.853	
Intel(R) Celeron(R) M processor         1.50GHz	(null)	8.1375674	
PowerPC 740/750 (280.00MHz)	(null)	58.07682	

CPU N-Queens
------------

-CPU N-Queens-
<big><b>This Machine</b></big>	800 MHz	8.599	

FPU FFT
-------

-FPU FFT-
<big><b>This Machine</b></big>	800 MHz	3.589	

FPU Raytracing
--------------

-FPU Raytracing-
<big><b>This Machine</b></big>	800 MHz	17.899	
Intel(R) Celeron(R) M processor         1.50GHz	(null)	40.8816714	
PowerPC 740/750 (280.00MHz)	(null)	161.312647

---

### Post by gauviz on 2009-11-25
I'm also facing the exact same issue. as described above.

After connecting to VPN i opened firefox and entered a URL
The screen went blank and Num Lock leds start blinking.

I used the .deb package provided to me. To make it work with newer kernel I modified the .deb to include the interprator.c patch. It installed successfully.

Help will be greatly appreciated.

Thanks
Gaurav

---

