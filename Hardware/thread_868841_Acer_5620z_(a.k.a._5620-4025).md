---
title: "Acer 5620z (a.k.a. 5620-4025)"
date: 2008-07-24
forum: Hardware
---

### Post by cetheriel on 2008-07-24
Running Hardy (8.04.1)

120GB HDD: works out of the box, needs acpi control (see below)
DVD-Super Multi DL: not tested yet

Sound Chipset: Intel built-in: worked out of the box*.
Video Chipset: Intel Graphics Media Acceleration: worked out of the box
(GMA's open drivers were the reason i bought this laptop)

Wired Network: Broadcom BCM5787M: worked out of the box
Wireless Network: Atheros 5007 (AR242x): needs driver (see below)

5-in-1 multi-reader (SD, MMC, xD, MS, MSPRO): worked out of the box
Bluetooth: worked out of the box
USB ports: worked out of the box
Firewire port: (not tested yet, was found OOB)
Keyboard layout: "acer laptop" works, but still looking for the right one. (euro, dollar and some function keys are not working).

other issues:
suspending/hibernating results in restart.

goodside:
runs smoothly, doesn't heat up, not expensive.

---

### Post by cetheriel on 2008-07-24
Go to System> Administration-> Hardware Drivers
Disable by un-ticking ONLY the following option

#Atheros Hardware Access Layer (Hal)

Then reboot your system

Preparing your System
Go to System->Administration->Software Sources
Make sure you have "Universe" & "Multiverse" checked.
Open the terminal from Applications–>Accessories–>Terminal and copy the following commands:
```
sudo apt-get install build-essential

wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
tar xfz madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007

sudo make 
sudo make install
sudo modprobe ath_pci
sudo reboot

```
[from [http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686) - thank [k33bz]("http://ubuntuforums.org/member.php?u=296107") for it

Update: updating kernel will break driver, install it again ('sudo make', then 'sudo make install') and reboot.

---

### Post by cetheriel on 2008-07-25
There is a bug on HD drive that causes it to park and unpark too often, increasing cycle count too quickly (caps at 600.000, mine was at 9000 after 5 days of use). but it is quite easy to work around.

1) make a file named "99-hdd-ugly-fix.sh". The important thing is starting with "99".
```
sudo gedit 99-hdd-ugly-fix.sh
```
2) make sure the file contains the following lines (fix it if you have PATA HDD):
```
#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda # you might need 255 or a different value
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 128 /dev/sda
fi
```
3) copy this file to 4 locations:
```
sudo install 99-hdd-ugly-fix.sh  /etc/acpi/resume.d/
sudo install 99-hdd-ugly-fix.sh  /etc/acpi/start.d/
sudo install 99-hdd-ugly-fix.sh  /etc/acpi/ac.d/
sudo install 99-hdd-ugly-fix.sh /etc/acpi/battery.d/
```

this should stop parking while on AC POWER (meaning you shouldn't shake your lap too much), and on while running on batteries (preventing problems should you be on a car or whatever).

from [http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046) - thanks to [nicedude]("http://ubuntuforums.org/member.php?u=531942") for bringing issue to my attention, and to [ubuntu_demon]("http://ubuntuforums.org/member.php?u=904") for going far deeper on solving the problem.

---

### Post by zggame on 2008-07-25
The wireless in mine is BroadCom BCM94311MCG. I am not sure whether that is the same one as yours.  The automatically-installed driver works but very poorly.  I used the ndiwrapper.  Check my [post]("http://ubuntuforums.org/showthread.php?p=5453825#post5453825").  But it stop to work after waking from hibernate.  

The sound part:  The volume seems low, you have to turn everything (master/pcm) to the largest to get decent volume, anything below 80% is barely audible. And the maximum seems not as loud as in windows vista.   I am using ALSA. 

Confirm the function key problem.  

Suspend never works.  Hibernate works sometimes.  I have a dual-boot (vista/ubuntu).  It will get to this boot menu of grub when waking, then go back to the ubuntu position before hibernate if ubuntu is choosed.    Not sure whether the suspend problem relates to the dual-boot. 

Overall, the 1G RAM is more than enough to ran most of the programs (eclipse/gimp/open office).  

I only have 8M allocated to video (setting in BIOS).  But the compiz cube works OK while just rotate with Ctl-Alt-left/right.  When use Ctl-Alt-mouse rotating, it is a bit rough.  But I am surprised compiz works in such a low ram setting.

---

### Post by zggame on 2008-08-24
Update:

After about a month, overall, it is very fast and responsible.  I am really delight with the performance with only 1G ram.  I have   It is better than my desktop with 4G RAM, E2140 (overclock to 2.1G) with vista. Now bad part, here is new list of issues. 

1. Wireless.  The ndiswrapper works for me for a while, then has big issue with any network about wpa.  Fortunately, this new broadcom dedicated linux driver rolled out and it works smoothly.  [http://ubuntuforums.org/showthread.php?t=880218]("http://ubuntuforums.org/showthread.php?t=880218")

2.  Graphics, this might be the problem of the laptop.  The laptop's BIOS has no option about the shared video memory. It seems to be fixed at 8M.  I think this limited the possibility of dual monitors.  But it works in windows.  Or maybe the 8.0.4's mesa driver (7.0.3-rc2)  is not good enough.  According to DRI's documents, mesa driver 7.0.4 and above start to support intel 965/960.  I used RandR.  But whenever I set virtual resolution above 2000x2000, system fails to recognized the video driver.

```
OpenGL
Vendor	Tungsten Graphics, Inc
Renderer	Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
Version	1.4 Mesa 7.0.3-rc2
Direct Rendering	Yes
```

3.  Sound.  Alsa does not work with the sound properly.  (Audio Adapter	HDA-Intel - HDA Intel).  The maximum sound level is low.  I have to turn everything into maximum to get decent volume.  And the built-in mic is way low and barely useful.  External mic picks up the sound from the built-in speaker really easily and produced self-feedback scream often.  I tried to mute the all input option in the sound-control and this seems to make no difference. 


[HTML]Computer
Summary
Computer
Processor	2x Intel(R) Pentium(R) Dual CPU T2370 @ 1.73GHz
Memory	1026MB (693MB used)
Operating System	Ubuntu 8.04.1
User Name	tigger (Tigger)
Date/Time	Sun 24 Aug 2008 08:47:11 AM CDT
Display
Resolution	1280x800 pixels
OpenGL Renderer	Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	HDA-Intel - HDA Intel
Input Devices
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
Logitech USB Receiver	
PC Speaker	
Power Button (FF)	
Lid Switch	
Sleep Button (CM)	
Video Bus	
SynPS/2 Synaptics TouchPad	
Printers (CUPS)
PDF	
SCX-4100_Series	
scx4100	(Default)
IDE Disks
SCSI Disks
TSSTcorp CDDVDW TS-L632H	
ATA Hitachi HTS54251	
Operating System
Version
Kernel	Linux 2.6.24-20-generic (i686)
Compiled	#1 SMP Mon Jul 28 13:49:52 UTC 2008
C Library	GNU C Library version 2.7 (stable)
Distribution	Ubuntu 8.04.1
Current Session
Computer Name	tigger-laptop
User Name	tigger (Tigger)
Home Directory	/home/tigger
Desktop Environment	GNOME 2.22 (session name: Default)
Misc
Uptime	37 minutes
Load Average	0.58, 0.33, 0.23
Kernel Modules
Loaded Modules
michael_mic	Michael MIC
arc4	ARC4 Cipher Algorithm
ecb	ECB block cipher algorithm
blkcipher	Generic block chaining cipher type
af_packet	
i915	Intel Graphics
drm	DRM shared core routines
rfcomm	Bluetooth RFCOMM ver 1.8
l2cap	Bluetooth L2CAP ver 2.9
bluetooth	Bluetooth Core ver 2.11
ipv6	IPv6 protocol stack for Linux
vboxdrv	VirtualBox Support Driver
ppdev	
acpi_cpufreq	ACPI Processor P-States Driver
cpufreq_stats	'cpufreq_stats' - A driver to export cpufreq stats through sysfs filesystem
cpufreq_userspace	CPUfreq policy governor 'userspace'
cpufreq_conservative	'cpufreq_conservative' - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors optimised for use in a battery environment
cpufreq_powersave	CPUfreq policy governor 'powersave'
cpufreq_ondemand	'cpufreq_ondemand' - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors
freq_table	CPUfreq frequency table helpers
sbs	Smart Battery System ACPI interface driver
sbshc	ACPI SMBus HC driver
dock	ACPI Dock Station Driver
iptable_filter	iptables filter table
ip_tables	IPv4 packet filter
x_tables	[ip,ip6,arp]_tables backend module
sbp2	IEEE-1394 SBP-2 protocol driver
parport_pc	PC-style parallel port driver
lp	
parport	
joydev	Joystick device interfaces
pcmcia	PCMCIA Driver Services
snd_hda_intel	Intel HDA driver
snd_pcm_oss	PCM OSS emulation for ALSA.
snd_mixer_oss	Mixer OSS emulation for ALSA.
snd_pcm	Midlevel PCM code for ALSA.
snd_page_alloc	Memory allocator for ALSA system.
snd_hwdep	Hardware dependent layer
snd_seq_dummy	ALSA sequencer MIDI-through client
snd_seq_oss	OSS-compatible sequencer module
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
snd_timer	ALSA timer interface
ieee80211_crypt_tkip	Host AP crypt: TKIP
wl	
ieee80211_crypt	HostAP crypto
snd_seq_device	ALSA sequencer device management
sdhci	Secure Digital Host Controller Interface driver
acer_acpi	Acer Laptop ACPI Extras Driver
battery	ACPI Battery Driver
ac	ACPI AC Adapter Driver
snd	Advanced Linux Sound Architecture driver for soundcards.
container	ACPI container driver
video	ACPI Video Driver
output	Display Output Switcher Lowlevel Control Abstraction
tifm_7xx1	TI FlashMedia host driver
nsc_ircc	NSC IrDA Device Driver
led_class	LED Class Interface
mmc_core	
psmouse	PS/2 mouse driver
yenta_socket	
rsrc_nonstatic	
pcmcia_core	Linux Kernel Card Services
serio_raw	Raw serio driver
tifm_core	TI FlashMedia core driver
irda	The Linux IrDA Protocol Stack
wmi_acer	ACPI-WMI Mapping Driver - acer_acpi port
iTCO_wdt	Intel TCO WatchDog Timer Driver
iTCO_vendor_support	Intel TCO Vendor Specific WatchDog Timer Driver Support
button	ACPI Button Driver
intel_agp	
pcspkr	PC Speaker beeper driver
evdev	Input driver event char devices
soundcore	Core sound module
crc_ccitt	CRC-CCITT calculations
shpchp	Standard Hot Plug PCI Controller Driver
pci_hotplug	PCI Hot Plug PCI Core
agpgart	AGP GART driver
ext3	Second Extended Filesystem with journaling extensions
jbd	
mbcache	Meta block cache (for extended attributes)
sg	SCSI generic (sg) driver
sr_mod	SCSI cdrom (sr) driver
sd_mod	SCSI disk (sd) driver
cdrom	
pata_acpi	SCSI low-level driver for ATA in ACPI mode
ata_generic	low-level driver for generic ATA
usbhid	USB HID core driver
hid	
ata_piix	SCSI low-level driver for Intel PIIX/ICH ATA controllers
ohci1394	Driver for PCI OHCI IEEE-1394 controllers
ieee1394	
libata	Library module for ATA devices
scsi_mod	SCSI core
tg3	Broadcom Tigon3 ethernet driver
ehci_hcd	10 Dec 2004 USB 2.0 'Enhanced' Host Controller (EHCI) Driver
uhci_hcd	USB Universal Host Controller Interface driver
usbcore	
thermal	ACPI Thermal Zone Driver
processor	ACPI Processor Driver
fan	ACPI Fan Driver
fbcon	
tileblit	Tile Blitting Operation
font	Console Fonts
bitblit	Bit Blitting Operation
softcursor	Generic software cursor
fuse	Filesystem in Userspace
Boots
Boots
Sun Aug 24 08:12 - 08:47 (00:34)	Kernel 2.6.24-20-generi
Fri Aug 22 17:49 - 08:47 (1+14:57)	Kernel 2.6.24-20-generi
Fri Aug 22 17:44 - 17:48 (00:03)	Kernel 2.6.24-20-generi
Fri Aug 22 17:34 - 17:43 (00:08)	Kernel 2.6.24-20-generi
Fri Aug 22 17:23 - 17:33 (00:10)	Kernel 2.6.24-20-generi
Fri Aug 22 13:54 - 17:22 (03:28)	Kernel 2.6.24-20-generi
Thu Aug 21 12:58 - 02:05 (13:07)	Kernel 2.6.24-20-generi
Thu Aug 21 11:15 - 02:05 (14:50)	Kernel 2.6.24-20-generi
Wed Aug 20 23:06 - 01:05 (01:58)	Kernel 2.6.24-20-generi
Wed Aug 20 18:05 - 21:27 (03:21)	Kernel 2.6.24-20-generi
Wed Aug 20 13:11 - 17:16 (04:04)	Kernel 2.6.24-20-generi
Wed Aug 20 01:31 - 02:09 (00:38)	Kernel 2.6.24-20-generi
Wed Aug 20 00:30 - 01:30 (00:59)	Kernel 2.6.24-19-generi
Tue Aug 19 21:35 - 00:29 (02:54)	Kernel 2.6.24-19-generi
Tue Aug 19 14:43 - 00:29 (09:46)	Kernel 2.6.24-19-generi
Sun Aug 17 12:53 - 23:02 (1+10:08)	Kernel 2.6.24-19-generi
Thu Aug 14 12:12 - 02:33 (14:20)	Kernel 2.6.24-19-generi
Thu Aug 14 12:06 - 12:11 (00:04)	Kernel 2.6.24-19-generi
Thu Aug 14 11:59 - 12:00 (00:00)	Kernel 2.6.24-19-generi
Thu Aug 14 11:54 - 11:58 (00:04)	Kernel 2.6.24-19-generi
Thu Aug 14 11:49 - 11:53 (00:03)	Kernel 2.6.24-19-generi
Thu Aug 14 11:47 - 11:48 (00:00)	Kernel 2.6.24-19-generi
Thu Aug 14 11:41 - 11:46 (00:04)	Kernel 2.6.24-19-generi
Thu Aug 14 11:34 - 11:40 (00:05)	Kernel 2.6.24-19-generi
Thu Aug 14 11:25 - 11:31 (00:06)	Kernel 2.6.24-19-generi
Thu Aug 14 11:12 - 11:21 (00:09)	Kernel 2.6.24-19-generi
Thu Aug 14 08:04 - 11:11 (03:07)	Kernel 2.6.24-19-generi
Wed Aug 13 17:05 - 00:48 (07:43)	Kernel 2.6.24-19-generi
Wed Aug 13 15:31 - 16:49 (01:17)	Kernel 2.6.24-19-generi
Wed Aug 13 09:00 - 13:29 (04:29)	Kernel 2.6.24-19-generi
Tue Aug 12 07:56 - 00:33 (16:37)	Kernel 2.6.24-19-generi
Mon Aug 11 20:37 - 00:06 (03:28)	Kernel 2.6.24-19-generi
Mon Aug 11 09:00 - 20:36 (11:36)	Kernel 2.6.24-19-generi
Fri Aug 8 11:21 - 00:11 (2+12:49)	Kernel 2.6.24-19-generi
Fri Aug 8 09:03 - 09:53 (00:49)	Kernel 2.6.24-19-generi
Thu Aug 7 09:50 - 01:11 (15:20)	Kernel 2.6.24-19-generi
Thu Aug 7 07:51 - 01:11 (17:20)	Kernel 2.6.24-19-generi
Wed Aug 6 11:13 - 11:35 (00:21)	Kernel 2.6.24-19-generi
Tue Aug 5 09:06 - 09:19 (1+00:13)	Kernel 2.6.24-19-generi
Mon Aug 4 16:23 - 09:05 (16:41)	Kernel 2.6.24-19-generi
Mon Aug 4 15:19 - 16:01 (00:41)	Kernel 2.6.24-19-generi
Mon Aug 4 08:22 - 14:57 (06:35)	Kernel 2.6.24-19-generi
Sun Aug 3 09:16 - 01:28 (16:12)	Kernel 2.6.24-19-generi
Sat Aug 2 07:37 - 09:15 (1+01:38)	Kernel 2.6.24-19-generi
Fri Aug 1 21:18 - 23:40 (02:22)	Kernel 2.6.24-19-generi
Fri Aug 1 14:42 - 16:25 (01:42)	Kernel 2.6.24-19-generi
Languages
Available Languages
en_AU.utf8	English locale for Australia
en_BW.utf8	English locale for Botswana
en_CA.utf8	English locale for Canada
en_DK.utf8	English locale for Denmark
en_GB.utf8	English locale for Britain
en_HK.utf8	English locale for Hong Kong
en_IE.utf8	English locale for Ireland
en_IN	English language locale for India
en_NZ.utf8	English locale for New Zealand
en_PH.utf8	English language locale for Philippines
en_SG.utf8	English language locale for Singapore
en_US.utf8	English locale for the USA
en_ZA.utf8	English locale for South Africa
en_ZW.utf8	English locale for Zimbabwe
zh_CN.utf8	Chinese locale for Peoples Republic of China
zh_HK.utf8	Chinese language locale for Hong Kong
zh_SG.utf8	Chinese language locale for Singapore
Filesystems
Mounted File Systems
/dev/sda5	72.4 GiB total, 40.5 GiB free
proc	0.0 B total, 0.0 B free
/sys	0.0 B total, 0.0 B free
varrun	501.0 MiB total, 500.9 MiB free
varlock	501.0 MiB total, 501.0 MiB free
udev	501.0 MiB total, 500.9 MiB free
devshm	501.0 MiB total, 501.0 MiB free
devpts	0.0 B total, 0.0 B free
lrm	501.0 MiB total, 462.2 MiB free
securityfs	0.0 B total, 0.0 B free
gvfs-fuse-daemon	72.4 GiB total, 40.5 GiB free
Shared Directories
SAMBA
NFS
Display
Display
Resolution	1280x800 pixels
Vendor	The X.Org Foundation
Version	1.4.0.90
Monitors
Monitor 0	1280x800 pixels
Extensions
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
OpenGL
Vendor	Tungsten Graphics, Inc
Renderer	Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
Version	1.4 Mesa 7.0.3-rc2
Direct Rendering	Yes
Network Interfaces
Network Interfaces
lo	Sent 0.10MiB, received 0.10MiB (127.0.0.1)
eth0	Sent 0.00MiB, received 0.00MiB
eth1	Sent 0.69MiB, received 11.41MiB (192.168.2.5)
irda0	Sent 0.00MiB, received 0.00MiB
Users
Human Users
tigger	Tigger
System Users
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
dhcp	
syslog	
klog	
hplip	HPLIP system user
avahi-autoipd	Avahi autoip daemon
gdm	Gnome Display Manager
pulse	PulseAudio daemon
messagebus	
avahi	Avahi mDNS daemon
polkituser	PolicyKit
haldaemon	Hardware abstraction layer
mysql	MySQL Server
tomcat55	
ntp	
Devices
Processor
Processors
Intel(R) Pentium(R) Dual CPU T2370 @ 1.73GHz	1733.00MHz
Intel(R) Pentium(R) Dual CPU T2370 @ 1.73GHz	1733.00MHz
Memory
Memory
Total Memory	1026044 kB
Free Memory	16440 kB
Buffers	233424 kB
Cached	316468 kB
Cached Swap	19480 kB
Active	481584 kB
Inactive	402888 kB
High Memory	121664 kB
Free High Memory	240 kB
Low Memory	904380 kB
Free Low Memory	16200 kB
Virtual Memory	3004112 kB
Free Virtual Memory	2984632 kB
Dirty	432 kB
Writeback	0 kB
AnonPages	315252 kB
Mapped	74064 kB
Slab	43072 kB
SReclaimable	30408 kB
SUnreclaim	12664 kB
PageTables	2916 kB
NFS_Unstable	0 kB
Bounce	0 kB
CommitLimit	3517132 kB
Committed_AS	995064 kB
VmallocTotal	114680 kB
VmallocUsed	9568 kB
VmallocChunk	104564 kB
PCI Devices
PCI Devices
Host bridge	Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub
VGA compatible controller	Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
Display controller	Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
Audio device	Intel Corporation 82801H
PCI bridge	Intel Corporation 82801H
PCI bridge	Intel Corporation 82801H
PCI bridge	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
USB Controller	Intel Corporation 82801H
PCI bridge	Intel Corporation 82801 Mobile PCI Bridge
ISA bridge	Intel Corporation 82801HEM
IDE interface	Intel Corporation 82801HBM/HEM
IDE interface	Intel Corporation 82801HBM/HEM
SMBus	Intel Corporation 82801H
Ethernet controller	Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express
Network controller	Broadcom Corporation BCM4311 802.11b/g WLAN
CardBus bridge	Texas Instruments PCIxx12 Cardbus Controller
FireWire (IEEE 1394)	Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
Mass storage controller	Texas Instruments 5-in-1 Multimedia Card Reader
SD Host controller	Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
USB Devices
Printers
Printers (CUPS)
PDF	
SCX-4100_Series	
scx4100	(Default)
Battery
Battery: BAT0
State	charged (load: 0 mA)
Capacity	3947 mAh / 4000 mAh (98.67%)
Battery Technology	rechargeable (LION)
Model Number	CONIS51
Serial Number	16549
Sensors
ACPI Thermal Zone
TZS1	60°C
TZS0	50°C
Input Devices
Input Devices
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
Logitech USB Receiver	
PC Speaker	
Power Button (FF)	
Lid Switch	
Sleep Button (CM)	
Video Bus	
SynPS/2 Synaptics TouchPad	
Storage
IDE Disks
SCSI Disks
TSSTcorp CDDVDW TS-L632H	
ATA Hitachi HTS54251	
Benchmarks
CPU ZLib
CPU ZLib
This Machine	9503.391
PowerPC 740/750 (280.00MHz)	2150.597408
Intel(R) Celeron(R) M processor 1.50GHz	8761.604561
CPU Fibonacci
CPU Fibonacci
This Machine	4.968
Intel(R) Celeron(R) M processor 1.50GHz	8.1375674
PowerPC 740/750 (280.00MHz)	58.07682
CPU MD5
CPU MD5
This Machine	57.212
PowerPC 740/750 (280.00MHz)	7.115258
Intel(R) Celeron(R) M processor 1.50GHz	38.6607998
CPU SHA1
CPU SHA1
This Machine	65.671
PowerPC 740/750 (280.00MHz)	6.761451
Intel(R) Celeron(R) M processor 1.50GHz	49.6752776
CPU Blowfish
CPU Blowfish
This Machine	18.823
Intel(R) Celeron(R) M processor 1.50GHz	26.1876862
PowerPC 740/750 (280.00MHz)	172.816713
FPU Raytracing
FPU Raytracing
This Machine	25.830
Intel(R) Celeron(R) M processor 1.50GHz	40.8816714
PowerPC 740/750 (280.00MHz)	161.312647
[/HTML]

---

### Post by cetheriel on 2008-08-25
sound issues:
i have installed module-assistant, an app that lets modules be built for the kernel.
```
sudo apt-get install module-assistant
```
then i updated it
```
sudo m-a update
```
then prepared
```
sudo m-a prepare
```
and finally, built alsa from source. alsa controls sound for linux.
```
sudo m-a install alsa-source
```
now my laptop sounds good.

---

### Post by zggame on 2008-08-26
Thanks. But I am using 2.6.24-21 for the wireless.  The repository universe (include the pre-release one) has no header for the kernal.  What should I do?

---

### Post by cetheriel on 2008-10-04
more info on [http://ubuntuforums.org/showthread.php?p=5906960](http://ubuntuforums.org/showthread.php?p=5906960)
i should have searched with google (ubuntuforums search sucks) before creating this topic..

---

