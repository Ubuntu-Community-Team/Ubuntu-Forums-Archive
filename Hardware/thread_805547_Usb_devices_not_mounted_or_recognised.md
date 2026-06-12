---
title: "Usb devices not mounted or recognised"
date: 2008-05-24
forum: Hardware
---

### Post by mac71 on 2008-05-24
Hi, I've had this problem for about two weeks now, and its really starting to irritate.

All of my usb slots are fine (both in ubuntu and windows), as they have all been individually checked with known working devices.

The problem is, none of them detect or mount usb memory sticks, mp3 players, or cameras. I can get it to detect and mount usb stick and mp3 player if i plug them in at boot but not after. The camera just doesn't show at all.

This cant be to do with the individual devices as they have all worked fine since dapper.

If anyone has any ideas it would be greatly appreciated.

---

### Post by kgriff on 2008-05-26
Mac,
  I don't necessarily have a solution for you, but I can tell you what I've found out so far.
  I'm having the same problem you are, and I've not found much information about it.  There's lots of talk about USB devices not automounting, but very few people talking about our problem.
  Do you, by any chance, know what your USB controller is?  You can see this using lspci.
  The only partial solution I've found is to disable USB 2.0 support in BIOS.  This seems to work sometimes.  From my testing, if you reboot your machine with USB 2.0 off, plug in a USB device, and have it recognized, USB will function fairly normally until the next reboot.  The next reboot, USB may or may not work.  It's pretty much a crap shoot with each reboot.
  On those reboots when USB does work, my camera, flash drive, USB printer, USB hub, USB HDD are all recognized and function.  Not that this is a good solution for data transfer, as data transfer is extremely with USB 2.0 disabled.

I've got a theory, with no evidence to support the theory, that this is a kernel issue.

In any event, please post your USB controller here and we'll go from there.

---

### Post by irksomekitty on 2008-05-27
I'm a newbie, so forgive me if this isn't in the right place, but I can't get my pictures from my Kodak EasyShare C533 camera. Except once. And it just doesn't show up anywhere.

Okay. F-spot wouldn't open, at all. Period. The first time I plugged in my camera I got a message that said a camera was found, and would I like to import the images? I clicked OK, and then nothing happened.

I tried to open F-spot, with or without the camera, and got a busy cursor, then nothing. Not even an error message. Checked forums, found a suggestion to try G-thumb if F-spot didn't work. Uninstalled F-spot, and installed G-thumb. Success! Retrieved photos from camera smooth as silk.

Then I disconnected the camera and took more pictures. Now G-thumb doesn't work either. When I try to import my pictures, G-thumb shows the NAME of my camera, but can't or won't get pictures from it. In any case, the camera doesn't show up anywhere on the system. First I searched for possible solutions, and didn't find anything that worked. So I tried restarting the computer, turning the camera off and back on, and disconnecting and reconnecting the camera, in over a dozen combinations, but nothing worked (and got no error messages to point me in the right direction, either). I then tried various combinations of screaming, vulgar hand gestures, and stomping my feet. That didn't work either. So now I'm asking for help.

This machine is a "reconditioned" piece of junk that I picked up for cheap cheap cheap after my nice computer died. I installed Ubuntu on it because it was slower than molasses running WinXP, and now it's fast fast fast, but I can't get my pictures! Wahh! Help!


Here's the information I got from running hardinfo: I can't make heads or tails of most of it.


Computer
Summary
Computer
Processor	Intel(R) Pentium(R) 4 CPU 2.40GHz
Memory	385MB (215MB used)
Operating System	Ubuntu 8.04
User Name	janice (janice)
Date/Time	Tue 27 May 2008 09:30:37 PM EDT
Display
Resolution	1024x768 pixels
OpenGL Renderer	Mesa DRI Rage 128 20051027 x86/MMX/SSE2
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	ICH4 - Intel ICH5
Input Devices
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
PIXART USB OPTICAL MOUSE	
Power Button (FF)	
Power Button (CM)	
PC Speaker	
Printers (CUPS)
PDF	
Photosmart_C3100_series	
IDE Disks
SCSI Disks
ATA Maxtor 93073U6	
Model: 52X32COMBO Rev: 104G 52X32COMBO	
Operating System
Version
Kernel	Linux 2.6.24-17-generic (i686)
Compiled	#1 SMP Thu May 1 14:31:33 UTC 2008
C Library	GNU C Library version 2.7 (stable)
Distribution	Ubuntu 8.04
Current Session
Computer Name	janice-desktop
User Name	janice (janice)
Home Directory	/home/janice
Desktop Environment	GNOME 2.22 (session name: Default)
Misc
Uptime	22 hours, 32 minutes
Load Average	0.57, 0.22, 0.13
Kernel Modules
Loaded Modules
xt_limit	iptables rate limit match
xt_tcpudp	x_tables match for TCP and UDP(-Lite), supports IPv4 and IPv6
ipt_LOG	iptables syslog logging module
ipt_MASQUERADE	iptables MASQUERADE target module
ipt_TOS	iptables TOS mangling module
ipt_REJECT	iptables REJECT target module
nf_conntrack_irc	IRC (DCC) connection tracking helper
nf_conntrack_ftp	ftp connection tracking helper
xt_state	ip[6]_tables connection tracking state match module
af_packet	
rndis_host	USB Host side RNDIS driver
cdc_ether	USB CDC Ethernet devices
usbnet	USB network driver framework
mii	MII hardware support library
snd_rtctimer	
ipv6	IPv6 protocol stack for Linux
binfmt_misc	
r128	ATI Rage 128
drm	DRM shared core routines
rfcomm	Bluetooth RFCOMM ver 1.8
l2cap	Bluetooth L2CAP ver 2.9
bluetooth	Bluetooth Core ver 2.11
ppdev	
speedstep_lib	Library for Intel SpeedStep 1 or 2 cpufreq drivers.
cpufreq_userspace	CPUfreq policy governor 'userspace'
cpufreq_conservative	'cpufreq_conservative' - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors optimised for use in a battery environment
cpufreq_ondemand	'cpufreq_ondemand' - A dynamic cpufreq governor for Low Latency Frequency Transition capable processors
cpufreq_stats	'cpufreq_stats' - A driver to export cpufreq stats through sysfs filesystem
freq_table	CPUfreq frequency table helpers
cpufreq_powersave	CPUfreq policy governor 'powersave'
sbs	Smart Battery System ACPI interface driver
container	ACPI container driver
sbshc	ACPI SMBus HC driver
dock	ACPI Dock Station Driver
video	ACPI Video Driver
output	Display Output Switcher Lowlevel Control Abstraction
battery	ACPI Battery Driver
ac	ACPI AC Adapter Driver
lp	
snd_intel8x0	Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455
snd_ac97_codec	Universal interface for Audio Codec '97
ac97_bus	
snd_pcm_oss	PCM OSS emulation for ALSA.
snd_mixer_oss	Mixer OSS emulation for ALSA.
parport_pc	PC-style parallel port driver
parport	
snd_pcm	Midlevel PCM code for ALSA.
evdev	Input driver event char devices
snd_seq_dummy	ALSA sequencer MIDI-through client
psmouse	PS/2 mouse driver
pcspkr	PC Speaker beeper driver
serio_raw	Raw serio driver
snd_seq_oss	OSS-compatible sequencer module
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
snd_timer	ALSA timer interface
snd_seq_device	ALSA sequencer device management
snd	Advanced Linux Sound Architecture driver for soundcards.
soundcore	Core sound module
snd_page_alloc	Memory allocator for ALSA system.
button	ACPI Button Driver
iTCO_wdt	Intel TCO WatchDog Timer Driver
iTCO_vendor_support	Intel TCO Vendor Specific WatchDog Timer Driver Support
shpchp	Standard Hot Plug PCI Controller Driver
pci_hotplug	PCI Hot Plug PCI Core
intel_agp	
agpgart	AGP GART driver
iptable_nat	
nf_nat	
nf_conntrack_ipv4	
nf_conntrack	
iptable_mangle	iptables mangle table
iptable_filter	iptables filter table
ip_tables	IPv4 packet filter
x_tables	[ip,ip6,arp]_tables backend module
ext3	Second Extended Filesystem with journaling extensions
jbd	
mbcache	Meta block cache (for extended attributes)
sg	SCSI generic (sg) driver
sr_mod	SCSI cdrom (sr) driver
cdrom	
sd_mod	SCSI disk (sd) driver
ata_generic	low-level driver for generic ATA
usbhid	USB HID core driver
hid	
ata_piix	SCSI low-level driver for Intel PIIX/ICH ATA controllers
floppy	
pata_acpi	SCSI low-level driver for ATA in ACPI mode
tg3	Broadcom Tigon3 ethernet driver
libata	Library module for ATA devices
scsi_mod	SCSI core
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
Mon May 26 22:58 - 21:18 (22:19)	Kernel 2.6.24-17-generi
Mon May 26 19:43 - 21:01 (01:17)	Kernel 2.6.24-17-generi
Mon May 26 19:08 - 19:43 (00:34)	Kernel 2.6.24-16-generi
Mon May 26 14:53 - 19:07 (04:14)	Kernel 2.6.24-16-generi
Mon May 26 14:25 - 14:52 (00:27)	Kernel 2.6.24-16-generi
Sun May 25 22:00 - 14:24 (16:24)	Kernel 2.6.24-16-generi
Fri May 23 23:39 - 14:24 (2+14:44)	Kernel 2.6.24-16-generi
Thu May 22 18:59 - 14:24 (3+19:25)	Kernel 2.6.24-16-generi
Thu May 22 18:24 - 18:58 (00:34)	Kernel 2.6.24-16-generi
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
Filesystems
Mounted File Systems
/dev/sda1	27.4 GiB total, 20.8 GiB free
proc	0.0 B total, 0.0 B free
/sys	0.0 B total, 0.0 B free
varrun	188.2 MiB total, 188.1 MiB free
varlock	188.2 MiB total, 188.2 MiB free
udev	188.2 MiB total, 188.2 MiB free
devshm	188.2 MiB total, 188.2 MiB free
devpts	0.0 B total, 0.0 B free
lrm	188.2 MiB total, 151.0 MiB free
securityfs	0.0 B total, 0.0 B free
binfmt_misc	0.0 B total, 0.0 B free
gvfs-fuse-daemon	27.4 GiB total, 20.8 GiB free
Shared Directories
SAMBA
NFS
Display
Display
Resolution	1024x768 pixels
Vendor	The X.Org Foundation
Version	1.4.0.90
Monitors
Monitor 0	1024x768 pixels
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
Vendor	VA Linux Systems, Inc.
Renderer	Mesa DRI Rage 128 20051027 x86/MMX/SSE2
Version	1.2 Mesa 7.0.3-rc2
Direct Rendering	Yes
Network Interfaces
Network Interfaces
lo	Sent 0.07MiB, received 0.07MiB (127.0.0.1)
eth0	Sent 21.30MiB, received 92.36MiB (192.168.1.97)
Users
Human Users
janice	janice
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
Devices
Processor
Processor
Name	Intel(R) Pentium(R) 4 CPU 2.40GHz
Family, model, stepping	15, 2, 9 (Pentium 4)
Vendor	Intel Corp.
Configuration
Cache Size	512kb
Frequency	2394.25MHz
BogoMIPS	4793.40
Byte Order	Little Endian
Features
FDIV Bug	no
HLT Bug	no
F00F Bug	no
Coma Bug	no
Has FPU	yes
Capabilities
fpu	Floating Point Unit
vme	Virtual 86 Mode Extension
de	Debug Extensions - I/O breakpoints
pse	Page Size Extensions (4MB pages)
tsc	Time Stamp Counter and RDTSC instruction
msr	Model Specific Registers
pae	Physical Address Extensions
mce	Machine Check Architeture
cx8	CMPXCHG8 instruction
apic	Advanced Programmable Interrupt Controller
sep	Fast System Call (SYSENTER/SYSEXIT)
mtrr	Memory Type Range Registers
pge	Page Global Enable
mca	Machine Check Architecture
cmov	Conditional Move instruction
pat	Page Attribute Table
pse36	36bit Page Size Extensions
clflush	Cache Line Flush instruction
dts	Debug Store
acpi	Thermal Monitor and Software Controlled Clock
mmx	MMX technology
fxsr	FXSAVE and FXRSTOR instructions
sse	SSE instructions
sse2	SSE2 (WNI) instructions
ss	Self Snoop
ht	HyperThreading
tm	Thermal Monitor
pbe	Pending Break Enable
up	
pebs	
bts	
sync_rdtsc	
cid	
xtpr	
Memory
Memory
Total Memory	385532 kB
Free Memory	83644 kB
Buffers	5044 kB
Cached	86064 kB
Cached Swap	3960 kB
Active	222472 kB
Inactive	48172 kB
High Memory	0 kB
Free High Memory	0 kB
Low Memory	385532 kB
Free Low Memory	83644 kB
Virtual Memory	1100412 kB
Free Virtual Memory	1039168 kB
Dirty	56 kB
Writeback	0 kB
AnonPages	179280 kB
Mapped	47988 kB
Slab	13116 kB
SReclaimable	5648 kB
SUnreclaim	7468 kB
PageTables	1724 kB
NFS_Unstable	0 kB
Bounce	0 kB
CommitLimit	1293176 kB
Committed_AS	573136 kB
VmallocTotal	638968 kB
VmallocUsed	12736 kB
VmallocChunk	626036 kB
PCI Devices
PCI Devices
Host bridge	Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface
PCI bridge	Intel Corporation 82865G/PE/P PCI to AGP Controller
USB Controller	Intel Corporation 82801EB/ER
USB Controller	Intel Corporation 82801EB/ER
USB Controller	Intel Corporation 82801EB/ER
USB Controller	Intel Corporation 82801EB/ER
PCI bridge	Intel Corporation 82801 PCI Bridge
ISA bridge	Intel Corporation 82801EB/ER
IDE interface	Intel Corporation 82801EB/ER
IDE interface	Intel Corporation 82801EB
SMBus	Intel Corporation 82801EB/ER
Multimedia audio controller	Intel Corporation 82801EB/ER
Ethernet controller	Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet
VGA compatible controller	ATI Technologies Inc Rage 128 PP/PRO TMDS [Xpert 128]
USB Devices
Printers
Printers (CUPS)
PDF	
Photosmart_C3100_series	
Battery
No batteries
No batteries found on this system	
Sensors
Input Devices
Input Devices
Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
PIXART USB OPTICAL MOUSE	
Power Button (FF)	
Power Button (CM)	
PC Speaker	
Storage
IDE Disks
SCSI Disks
ATA Maxtor 93073U6	
Model: 52X32COMBO Rev: 104G 52X32COMBO	
Benchmarks
CPU ZLib
CPU ZLib
This Machine	0.000
PowerPC 740/750 (280.00MHz)	2150.597408
Intel(R) Celeron(R) M processor 1.50GHz	8761.604561
CPU Fibonacci
CPU Fibonacci
This Machine	6.035
Intel(R) Celeron(R) M processor 1.50GHz	8.1375674
PowerPC 740/750 (280.00MHz)	58.07682
CPU MD5
CPU MD5
This Machine	29.216
PowerPC 740/750 (280.00MHz)	7.115258
Intel(R) Celeron(R) M processor 1.50GHz	38.6607998
CPU SHA1
CPU SHA1
This Machine	40.404
PowerPC 740/750 (280.00MHz)	6.761451
Intel(R) Celeron(R) M processor 1.50GHz	49.6752776
CPU Blowfish
CPU Blowfish
This Machine	21.788
Intel(R) Celeron(R) M processor 1.50GHz	26.1876862
PowerPC 740/750 (280.00MHz)	172.816713
FPU Raytracing
FPU Raytracing
This Machine	29.353
Intel(R) Celeron(R) M processor 1.50GHz	40.8816714
PowerPC 740/750 (280.00MHz)	161.312647

---

### Post by kgriff on 2008-05-28
irksomekitty,
  Regarding your camera:  In those instances when you are unable to download pictures from the camera, does camera show up in the Places menu, or on the Desktop?  (Forget about gThumb or F-Spot for now.  I don't think either of those are the problem.)
If the camera does show up in Places, but not on the desktop, then the volume is probably not mounted.  Your computer does not necessarily know that your camera is a camera.  It looks at it as an external USB storage device.  In order to read data from a storage device, whether it is internal or external, the drive has to first be mounted.  To mount the volume, click on its' name in Places.
If it shows up in Places and on the Desktop, it is probably mounted already.  In this case, double click on the desktop icon and it should open in Nautilus.  At this point, you should be able to see the pictures on the camera.

Try this and let me know what happens.  Sorry if I sound patronizing above with the description of volumes and mounting, but I don't know your experience or knowledge level with this.

---

### Post by mac71 on 2008-05-28
Hi,
Here's my read out from lspci
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0a:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet (rev 03)
ubuntu@ubuntu:~$ 

I believe its a kernel issue also. I have a copy of mandriva spring 2008 which has the same issues, while pclinuxos 2007 is using 2.6.18 and all is working fine.

If anyone knows of a permanent fix, it'd be great.

---

### Post by irksomekitty on 2008-05-28
> **kgriff said:**
> irksomekitty,
  Regarding your camera:  In those instances when you are unable to download pictures from the camera, does camera show up in the Places menu, or on the Desktop?  (Forget about gThumb or F-Spot for now.  I don't think either of those are the problem.)
If the camera does show up in Places, but not on the desktop, then the volume is probably not mounted.  Your computer does not necessarily know that your camera is a camera.  It looks at it as an external USB storage device.  In order to read data from a storage device, whether it is internal or external, the drive has to first be mounted.  To mount the volume, click on its' name in Places.
If it shows up in Places and on the Desktop, it is probably mounted already.  In this case, double click on the desktop icon and it should open in Nautilus.  At this point, you should be able to see the pictures on the camera.

Try this and let me know what happens.  Sorry if I sound patronizing above with the description of volumes and mounting, but I don't know your experience or knowledge level with this.

It's not showing up ANYWHERE, at ALL. The camera is plugged in, and turned on. I uninstalled G-thumb, and installed digiKam, and once again was somehow able to get my photos... but this might only work once, too!

:( 

... I'll have to test it.

At any rate, my ignorance ticks me off. Where's a good place for a newbie to learn more about how this stuff works? Workarounds are okay for a quick fix, but not understanding bothers me. I'm intelligent enough to figure out a way to JUST MAKE IT WORK, if I knew what was actually going on (instead of just randomly trying different things with my fingers crossed).

Help! Somebody infuse me with knowledge (or point me to a website that has nice, clear explanations, preferably with a glossary)!

---

### Post by krlhc8 on 2008-05-28
My flash drive worked fine under Hardy until I upgraded to the newest kernel 2.6.24-17-generic.  I don't understand how it could be a kernel issue though because I rebooted with 2.6.24-16, and it still wouldn't mount the device.

---

### Post by kgriff on 2008-05-28
krlhc8,
  I agree that, in your case, it doesn't sound like a kernel issue.  What is the USB controller in your machine?  In my case, on the computer in question, I have not anything installed other than Hardy and USB is sporadic.  My controller is ATI SB600.  I have another machine, also running Hardy, with an Nvidia MCP61 controller and the USB works perfectly.  However, everything I have seen still leads me to believe that it is a kernel issue.

Mac71,
  Thanks for the lspci.  I'm kinda trying to make a list of controllers that don't work correctly.  That was my issue when I purchased the motherboard with the currently sporadically working USB.  I couldn't find any information about specific controllers or chipsets, other than "If you have an AMD chipset, the board should work fine."  Well, my board is proving that theory wrong.

My solution, on the machine with the ATI controller, was to install a PCI USB controller.  It is of Belkin manufacture and now USB on that computer works flawlessly.

irksomekitty,
Unfortunately, I don't know of a website with the technical information you are looking for.  I've learned what I know over the years of messing with computers.  From Commodore 64's and Tandy TRS-80's to the present.  I will attempt to answer any questions you have as best I can, though I have only recently returned to Linux, so I'm not a Linux expert, by any means.

As for your USB problem:  Let's tackle it systematically:
Step 1 - From terminal, type lspci.  This will give you a list of all pci buses and devices on your computer, and will include your USB controller.  Please include the entire printout of lspci, or at least the USB lines in your next post.  Knowing the manufacturer and model, it will be possible to search and see if other people running Ubuntu in particular, or Linux in general, are having problems with this USB chipset.
Step 2 - Uninstall digiKam and forget about imaging programs for a bit.  First we need to get your USB running reliably.  Once USB works properly, you should be able to use any imaging program you want to.
Step 3 - Shut down your computer and plug in your digital camera, and any other USB devices you have, then reboot the computer.  From terminal, type lsusb and post the result here.  This will show a list of all USB devices currently connected to the computer.
Step 4 - If any USB devices automounted (you will know this if they show up on your desktop) right click on them and select Unmount, then shut the computer down.
Step 5 - With the computer turned off, unplug all USB devices, then restart the computer.  Plug in your camera, then type lsusb from terminal and post the result.

This should give enough information to figure out the next steps.

I did just locate a couple of web sites that may give you some of the information you want.  [http://www.howstuffworks.com/usb.htm](http://www.howstuffworks.com/usb.htm) howstuffworks is a pretty cool web site that has all kinds of information about, you guessed it, how stuff works.  [http://www.linux-usb.org/](http://www.linux-usb.org/) has a ton of USB information.  Also [http://en.wikipedia.org/wiki/USB](http://en.wikipedia.org/wiki/USB)

I know this is frustrating, and it doesn't help that you have to wait hours or days for a reply, but hang in there and we should be able to get your problem solved.

edit - I just re-read your hardinfo from your first post and see that you have an intel 82801 EB/ER USB controller.  I find this interesting, because mac71 also has an intel 82801 USB controller.

---

### Post by irksomekitty on 2008-05-29
Thank you, kgriff. I'm not in a huge rush, and I don't mind waiting for help; this is not exactly a life-or-death situation. I shall follow the steps you outlined, and check out the links you kindly provided when I'm not drowsy and bewildered.

Irksomekitty out. I'll work on this tomorrow, and keep you posted.

---

### Post by cdtech on 2008-05-29
From my experiances this is a race condition between hal and dbus which happens when the two initscripts are started concurrently by upstart.

This should not happen because hal initscript requires dbus for starting but instead happens when upstart concurrency is enabled because the scripts have been symlinked with the same number (12).

The solution is to install hal initscript with S13.

Try this and see if this corrects the problem:

```
sudo mv /etc/rc2.d/S12hal /etc/rc2.d/S13hal
```

Hope this helps.....

---

### Post by krlhc8 on 2008-05-29
Thanks for the quick response cdtech, yet in the rc2.d folder, I have S24hal and S12dbus.  So I don't think this is my problem.  I do know that when I run a fresh 8.04 live CD, my USB flash drive works great.  Have any other ideas?

---

### Post by cdtech on 2008-05-29
I've heard some had success uninstalling hal and reinstalling. It's worth a shot.

---

### Post by krlhc8 on 2008-05-29
Yeah I tried that, too.

---

### Post by linxed on 2008-06-08
Hi,
I have recently installed ubuntu 8.04 and I have came to the conclusion that ubuntu does not support my usb hardware at all.
the hardware works fine with windows so it is a ubuntu driver issue.
The bios is Phoenix award version 6.00PG and mainboard is a Jetway.

I tried ubuntu on another machine and USB does seem to work ok.

Hope someone could shed some light.

Thanks

---

### Post by sammydadams on 2008-06-08
this might be a band-aid fix, but it's worth a shot maybe...just try to restart the hardware abstraction layer...if it works on startup, just type into the terminal ```
sudo /etc/init.d/hal restart
```if this works you can make a launcher or script and just run it once you have the usb installed...sucks, but might be the only way to get access to the usb for the time being...hope it helps
good luck

---

### Post by linxed on 2008-06-09
Thanks Sammy,
I have tried this but no luck.
Wierd thing is that I have installed ubuntu on another computer (laptop) following exact same procedure as with the pc, works on one but doesnt on the other.
Seems like Ubuntu is fussy on what hardware it decides to work with. Have no idea what it doesnt like about my PC usb.

I also tried downloading linux openSUSE but USB keyboard doesnt work on that either.

On a different note, my laptop keyboard has now stopped working properly, with the num lock LED not going off, and the keys around jkl spitting out numbers instead.
Everything normal until ubuntu kicks in, so definitely a driver issue.

Thanks again for your reply,

---

### Post by sammydadams on 2008-06-09
wow...that is weird....have you tried another version of ubuntu? i know some people have had more success with gutsy...i have run out of ideas tho...sorry

---

### Post by newsboy on 2008-06-09
I have been having similar problems. Prior to hardy all my usb devices were automent. However following the upgrade it does seem to want to automount any of the devices. 
An 'lspci' results in:
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)

and when i run 'sudo udevmonitor --environment'

UDEV  [1213046819.407552] add      /block/sdc (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sdc
SUBSYSTEM=block
MINOR=32
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:02.0/usb1/1-8/1-8:1.0/host9/target9:0:0/9:0:0:0
PHYSDEVBUS=scsi
SEQNUM=4349
UDEVD_EVENT=1
DEVTYPE=disk
ID_VENDOR=Memorex
ID_MODEL=TD_Classic_003C
ID_REVISION=6.16
ID_SERIAL=Memorex_TD_Classic_003C_0A40A4613121D997-0:0
ID_SERIAL_SHORT=0A40A4613121D997
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_PATH=pci-0000:00:02.0-usb-0:8:1.0-scsi-0:0:0:0
DEVNAME=/dev/sdc
DEVLINKS=/dev/disk/by-id/usb-Memorex_TD_Classic_003C_0A40A4613121D997-0:0 /dev/disk/by-path/pci-0000:00:02.0-usb-0:8:1.0-scsi-0:0:0:0

it seems the computer is seeing and recognizing the devices but doesn't automount them. I have tried uninstalling hal which resulted in a large mess of packages that needed to be reinstalled, but i believe I got all of them.

Making matters worse, when I boot off the livecd, hardy recognizes and automounts all my usb devices.

I tried to solutions set forth in this thread already and nothing seems to work.

---

### Post by MarkX on 2008-06-10
BUMP!
Having the same problem, suddenly none of my USB flash drives or memory cards are detected at all.

---

### Post by krlhc8 on 2008-06-10
Yeah, I had to reinstall everything from the liveCD, and now everything works.  Barbaric, yes, but at least it works.

---

### Post by MarkX on 2008-06-10
Looks like I'll have to reinstall everything then! Another day down the drain...
Could a mod please move this thread to somewhere where it will get attention because USB drives stopping to work is a MAJOR bug.

---

### Post by krlhc8 on 2008-06-10
Check to make sure it works on a fresh liveCD first!!!  And be wary about installing the latest kernel in the update manager (most likely the problem).

---

### Post by tenmoi on 2008-06-10
I posted some 3 days ago about Hardy (2.6.24_eight teen) not recognizing my SE k550i and didn't get any answer. So I knew I had to find the solution myself.

Today after I read this thread I thought someone was having the problem as me. And I decided to give it a try. And this was what I did to successfully access my phone.

1. I plugged in an Imation usb stick and did a lsusb. I could see the usb. This was expected as only this phone was not recognised.
2. I opened up f-photo and then plugged in the phone again and to my surprise the phone and phone card were there and f-phone was offering to import my pictures. I unmounted the phone and closed f-photo and plugged in the phone and it was recognised immediately. Note that I have only updated 5 packages only since the phone was not recognised and they are the gcc packages.

I don't know if the phone will be recognised on the next boot but I'm happy right now.

--------------------------------------------------------------------------------

Also be noted that 3 days ago no matter how many times I restarted Hardy, it failed to recognise the phone. And to make sure that the usb connector was properly plugged in I had booted to M$ Windows and after successfully accessing the phone, and with the usb cable still being plugged in I rebooted into Hardy only to find that the phone was not recognised.

Just my 2 cents. Does Hardy play the naughty boy sometimes?

---

### Post by tenmoi on 2008-06-10
just did a reboot and the phone is recognised.

ANd I recently changed the resolution to 1152 x 864.

---

### Post by pixelstuff on 2008-06-11
> **tenmoi said:**
> 
Today after I read this thread I thought someone was having the problem as me. And I decided to give it a try. And this was what I did to successfully access my phone.

tenmoi, what out of this thread did you try? reinstall everything, reinstall hal? or are you just using f-photo and your phone is still not automounted as a drive? (my mp3players and cameras won't automount on hardy...)
ty

---

### Post by tenmoi on 2008-06-11
Well I did not do anything, just what was described in my post. My phone was recognised by Gutsy until I installed Hardy and took some photos and wanted to transfer some mp3 files to my phone and Hardy did not recognise it. 
What was frustrating was that Hardy recognised my friend's Nokia 5610 and he was poking fun of my GREAT phone.

I came across this thread and f-photo caught my eyes and I did a lsusb then lspci then plugged in my usb stick, and the phone just for fun. And it solved it like magic. 

what really led me to do it that way was that I thought "if the OS cannot read it, let the f-phone read it. And let Hardy read the usb stick first and deceive it into reading the phone by plugging it later on". and it works.

---

### Post by linxed on 2008-06-11
Well, been messing around with ubuntu for the last 5 days and its beginning to wear on me. I have searched all over internet for clues as to why the USB doesnt work in ubuntu kernel but no luck.
I had the USB keyboard plugged in with caps lock light on, but as soon as linux kernel begins, the light goes out and USB is unusable at that point.
here is result of lsusb:
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Result in lspci returns the following info about USB hardware:

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)

Another point is that the USB never worked when using the Live CD either.

Im also having trouble with flash plugins. Gnash and macromedia both fail to work. But that is for another thread, which I might post if I decide to keep on with linux/ubuntu.

Hope someone has the answer.

Thanks again.

---

### Post by linxed on 2008-06-11
I've managed to get my USB Keyboard (Apple slimline) working.
A bizarre situation with a bizarre resolution, here goes.

Well it turns out that the two USB connectors on the front of my PC are not being detected by Kernel.
I have been using the back USB with an extension wire and no results.

However I have removed the extension wire and now the back USB socket is functioning normally.

As strange as it seems, it looks like linux is fussy about the USB extension wire as it worked ok with windows, dos, grub, etc...
Dont see why, its only a simple cable to enable my apple keyboard to reach my pc from my tabletop?!

It's a bit of a long shot but perhaps the highspeed timing of the USB port is crucial here, with the least bit of interference throwing the kernel out of sync?

Regarding the front USB, nothing works in that, unless it is powered.
Also tried the dodgy extension cable again, this time with a small USB hub on the end of it, which now works ok (wierd), so anything which i would have needed to plug into front will go in here.

I also managed to resolve the issue with the jammed numlock on my laptop (see above). Simply plug the USB apple keyboard in and then Press F6 twice. Then remove keyboard again (if desired).


Look forward to your thoughts :confused:

---

### Post by billir on 2008-06-13
USB sticks not mounting on insertion or even with one in at boot up.
There is two exception to this, on installation the 8.04 system it will see my Brother 7820N USB printer  enough to install and the Logitec USB headset.
I have tried the Ubuntu 8.04 amd64 desktop and the kubuntu 8.04 I-386 Alternate. 
Both work very well except for the USB problem

the computer mobo is a Gigabyte GA-MA77-DS3/S3
running an amd64 phenom 4 core cpu and 4 gig of memory

**lsusb** from the hardy heron amd64 live disk with 2 Kensington USB sticks plugged in
ubuntu@ubuntu:~$ sudo lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 046d:0a01 Logitech, Inc. Logitech USB Headset
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04f9:0181 Brother Industries, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$ 


**lspci** from the hardy heron amd64 live disk

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

I must have a reliable USB system so I am going to buy a pci usb card and see if that will get me going.
Perhaps some day we will get USB support from a most excellent product.
If anyone hears of new development Please Post
Thanks

---

### Post by billir on 2008-06-13
Tried a new install of Desktop Ubuntu 8.04 on the same machine as my pervious post.
Immediately checked the logs.The kernel log showed errors concerning the USB connections
Im not good a reading and understanding the log much less fix something so I am posting the whole log - perhaps someone will know how to fix the problem.

Jun 13 08:16:35 ubun-br kernel: Inspecting /boot/System.map-2.6.24-16-generic
Jun 13 08:16:35 ubun-br kernel: Loaded 28313 symbols from /boot/System.map-2.6.24-16-generic.
Jun 13 08:16:35 ubun-br kernel: Symbols match kernel version 2.6.24.
Jun 13 08:16:35 ubun-br kernel: Loaded 18123 symbols from 83 modules.
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Command line: root=UUID=75b76e7d-1e82-4c0f-977e-65e2dbe1a231 ro quiet splash
Jun 13 08:16:35 ubun-br kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jun 13 08:16:35 ubun-br kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
Jun 13 08:16:35 ubun-br kernel: [    0.000000] end_pfn_map = 1245184
Jun 13 08:16:35 ubun-br kernel: [    0.000000] DMI 2.3 present.
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6C70 checksum 0
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: RSDP 000F6C70, 0014 (r0 GBT   )
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: RSDT CFEE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: FACP CFEE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: DSDT CFEE30C0, 4162 (r1 GBT    GBTUACPI     1000 MSFT  3000000)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: FACS CFEE0000, 0040
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: SSDT CFEE7300, 0544 (r1 PTLTD  POWERNOW        1  LTP        1)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: HPET CFEE7880, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: MCFG CFEE78C0, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: APIC CFEE7240, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] No NUMA configuration found
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Faking a node at 0000000000000000-0000000130000000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Zone PFN ranges:
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   DMA             0 ->     4096
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   DMA32        4096 ->  1048576
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   Normal    1048576 ->  1245184
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Movable zone start PFN for each node
Jun 13 08:16:35 ubun-br kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 13 08:16:35 ubun-br kernel: [    0.000000]     0:        0 ->      159
Jun 13 08:16:35 ubun-br kernel: [    0.000000]     0:      256 ->   851680
Jun 13 08:16:35 ubun-br kernel: [    0.000000]     0:  1048576 ->  1245184
Jun 13 08:16:35 ubun-br kernel: [    0.000000] On node 0 totalpages: 1048191
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   DMA zone: 1210 pages reserved
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   DMA zone: 2733 pages, LIFO batch:0
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   Normal zone: 2688 pages used for memmap
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   Normal zone: 193920 pages, LIFO batch:31
Jun 13 08:16:35 ubun-br kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Processor #1
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Processor #2
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Processor #3
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 13 08:16:35 ubun-br kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Setting APIC routing to flat
Jun 13 08:16:35 ubun-br kernel: [    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfee0000 - 00000000cfee3000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfee3000 - 00000000cfef0000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfef0000 - 00000000cff00000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cff00000 - 00000000e0000000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Jun 13 08:16:35 ubun-br kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029957
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Policy zone: Normal
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Kernel command line: root=UUID=75b76e7d-1e82-4c0f-977e-65e2dbe1a231 ro quiet splash
Jun 13 08:16:35 ubun-br kernel: [    0.000000] Initializing CPU#0
Jun 13 08:16:35 ubun-br kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jun 13 08:16:35 ubun-br kernel: [    0.000000] hpet clockevent registered
Jun 13 08:16:35 ubun-br kernel: [    0.000000] TSC calibrated against HPET
Jun 13 08:16:35 ubun-br kernel: [   35.420295] Marking TSC unstable due to TSCs unsynchronized
Jun 13 08:16:35 ubun-br kernel: [   35.420297] time.c: Detected 2410.985 MHz processor.
Jun 13 08:16:35 ubun-br kernel: [   35.421176] Console: colour VGA+ 80x25
Jun 13 08:16:35 ubun-br kernel: [   35.421179] console [tty0] enabled
Jun 13 08:16:35 ubun-br kernel: [   35.421192] Checking aperture...
Jun 13 08:16:35 ubun-br kernel: [   35.421194] CPU 0: aperture @ 4000000 size 32 MB
Jun 13 08:16:35 ubun-br kernel: [   35.421195] Aperture too small (32 MB)
Jun 13 08:16:35 ubun-br kernel: [   35.432164] No AGP bridge found
Jun 13 08:16:35 ubun-br kernel: [   35.432165] Your BIOS doesn't leave a aperture memory hole
Jun 13 08:16:35 ubun-br kernel: [   35.432167] Please enable the IOMMU option in the BIOS setup
Jun 13 08:16:35 ubun-br kernel: [   35.432168] This costs you 64 MB of RAM
Jun 13 08:16:35 ubun-br kernel: [   35.452599] Mapping aperture over 65536 KB of RAM @ 4000000
Jun 13 08:16:35 ubun-br kernel: [   35.477728] Memory: 4045760k/4980736k available (2466k kernel code, 147004k reserved, 1309k data, 316k init)
Jun 13 08:16:35 ubun-br kernel: [   35.477753] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Jun 13 08:16:35 ubun-br kernel: [   35.554339] Calibrating delay using timer specific routine.. 5023.98 BogoMIPS (lpj=10047968)
Jun 13 08:16:35 ubun-br kernel: [   35.554360] Security Framework initialized
Jun 13 08:16:35 ubun-br kernel: [   35.554365] SELinux:  Disabled at boot.
Jun 13 08:16:35 ubun-br kernel: [   35.554375] AppArmor: AppArmor initialized
Jun 13 08:16:35 ubun-br kernel: [   35.554378] Failure registering capabilities with primary security module.
Jun 13 08:16:35 ubun-br kernel: [   35.554667] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 13 08:16:35 ubun-br kernel: [   35.556097] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 13 08:16:35 ubun-br kernel: [   35.556751] Mount-cache hash table entries: 256
Jun 13 08:16:35 ubun-br kernel: [   35.556848] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 13 08:16:35 ubun-br kernel: [   35.556850] CPU: L2 Cache: 512K (64 bytes/line)
Jun 13 08:16:35 ubun-br kernel: [   35.556852] CPU 0/0 -> Node 0
Jun 13 08:16:35 ubun-br kernel: [   35.556854] CPU: Physical Processor ID: 0
Jun 13 08:16:35 ubun-br kernel: [   35.556855] CPU: Processor Core ID: 0
Jun 13 08:16:35 ubun-br kernel: [   35.556873] SMP alternatives: switching to UP code
Jun 13 08:16:35 ubun-br kernel: [   35.557339] Early unpacking initramfs... done
Jun 13 08:16:35 ubun-br kernel: [   35.831568] ACPI: Core revision 20070126
Jun 13 08:16:35 ubun-br kernel: [   35.831606] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun 13 08:16:35 ubun-br kernel: [   35.901199] Using local APIC timer interrupts.
Jun 13 08:16:35 ubun-br kernel: [   35.942616] APIC timer calibration result 12557205
Jun 13 08:16:35 ubun-br kernel: [   35.942617] Detected 12.557 MHz APIC timer.
Jun 13 08:16:35 ubun-br kernel: [   35.942686] SMP alternatives: switching to SMP code
Jun 13 08:16:35 ubun-br kernel: [   35.943081] Booting processor 1/4 APIC 0x1
Jun 13 08:16:35 ubun-br kernel: [   35.953735] Initializing CPU#1
Jun 13 08:16:35 ubun-br kernel: [   36.030476] Calibrating delay using timer specific routine.. 4822.15 BogoMIPS (lpj=9644309)
Jun 13 08:16:35 ubun-br kernel: [   36.030481] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 13 08:16:35 ubun-br kernel: [   36.030482] CPU: L2 Cache: 512K (64 bytes/line)
Jun 13 08:16:35 ubun-br kernel: [   36.030484] CPU 1/1 -> Node 0
Jun 13 08:16:35 ubun-br kernel: [   36.030486] CPU: Physical Processor ID: 0
Jun 13 08:16:35 ubun-br kernel: [   36.030487] CPU: Processor Core ID: 1
Jun 13 08:16:35 ubun-br kernel: [   36.030755] AMD Phenom(tm) 9750 Quad-Core Processor stepping 03
Jun 13 08:16:35 ubun-br kernel: [   36.030879] SMP alternatives: switching to SMP code
Jun 13 08:16:35 ubun-br kernel: [   36.031183] Booting processor 2/4 APIC 0x2
Jun 13 08:16:35 ubun-br kernel: [   36.041835] Initializing CPU#2
Jun 13 08:16:35 ubun-br kernel: [   36.122319] Calibrating delay using timer specific routine.. 4822.00 BogoMIPS (lpj=9644001)
Jun 13 08:16:35 ubun-br kernel: [   36.122324] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 13 08:16:35 ubun-br kernel: [   36.122325] CPU: L2 Cache: 512K (64 bytes/line)
Jun 13 08:16:35 ubun-br kernel: [   36.122327] CPU 2/2 -> Node 0
Jun 13 08:16:35 ubun-br kernel: [   36.122329] CPU: Physical Processor ID: 0
Jun 13 08:16:35 ubun-br kernel: [   36.122330] CPU: Processor Core ID: 3
Jun 13 08:16:35 ubun-br kernel: [   36.122599] AMD Phenom(tm) 9750 Quad-Core Processor stepping 03
Jun 13 08:16:35 ubun-br kernel: [   36.122714] SMP alternatives: switching to SMP code
Jun 13 08:16:35 ubun-br kernel: [   36.123013] Booting processor 3/4 APIC 0x3
Jun 13 08:16:35 ubun-br kernel: [   36.133668] Initializing CPU#3
Jun 13 08:16:35 ubun-br kernel: [   36.214161] Calibrating delay using timer specific routine.. 4821.99 BogoMIPS (lpj=9643995)
Jun 13 08:16:35 ubun-br kernel: [   36.214167] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 13 08:16:35 ubun-br kernel: [   36.214168] CPU: L2 Cache: 512K (64 bytes/line)
Jun 13 08:16:35 ubun-br kernel: [   36.214170] CPU 3/3 -> Node 0
Jun 13 08:16:35 ubun-br kernel: [   36.214172] CPU: Physical Processor ID: 0
Jun 13 08:16:35 ubun-br kernel: [   36.214173] CPU: Processor Core ID: 2
Jun 13 08:16:35 ubun-br kernel: [   36.214442] AMD Phenom(tm) 9750 Quad-Core Processor stepping 03
Jun 13 08:16:35 ubun-br kernel: [   36.214519] Brought up 4 CPUs
Jun 13 08:16:35 ubun-br kernel: [   36.214664] CPU0 attaching sched-domain:
Jun 13 08:16:35 ubun-br kernel: [   36.214666]  domain 0: span 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214668]   groups: 01 02 04 08
Jun 13 08:16:35 ubun-br kernel: [   36.214671]   domain 1: span 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214672]    groups: 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214673] CPU1 attaching sched-domain:
Jun 13 08:16:35 ubun-br kernel: [   36.214675]  domain 0: span 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214676]   groups: 02 04 08 01
Jun 13 08:16:35 ubun-br kernel: [   36.214678]   domain 1: span 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214679]    groups: 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214680] CPU2 attaching sched-domain:
Jun 13 08:16:35 ubun-br kernel: [   36.214681]  domain 0: span 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214682]   groups: 04 08 01 02
Jun 13 08:16:35 ubun-br kernel: [   36.214684]   domain 1: span 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214685]    groups: 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214686] CPU3 attaching sched-domain:
Jun 13 08:16:35 ubun-br kernel: [   36.214687]  domain 0: span 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214688]   groups: 08 01 02 04
Jun 13 08:16:35 ubun-br kernel: [   36.214690]   domain 1: span 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214691]    groups: 0f
Jun 13 08:16:35 ubun-br kernel: [   36.214903] net_namespace: 120 bytes
Jun 13 08:16:35 ubun-br kernel: [   36.215240] Time: 14:14:27  Date: 06/13/08
Jun 13 08:16:35 ubun-br kernel: [   36.215260] NET: Registered protocol family 16
Jun 13 08:16:35 ubun-br kernel: [   36.215385] ACPI: bus type pci registered
Jun 13 08:16:35 ubun-br kernel: [   36.215434] PCI: Using configuration type 1
Jun 13 08:16:35 ubun-br kernel: [   36.216225] ACPI: EC: Look up EC in DSDT
Jun 13 08:16:35 ubun-br kernel: [   36.220022] ACPI: Interpreter enabled
Jun 13 08:16:35 ubun-br kernel: [   36.220024] ACPI: (supports S0 S1 S4 S5)
Jun 13 08:16:35 ubun-br kernel: [   36.220034] ACPI: Using IOAPIC for interrupt routing
Jun 13 08:16:35 ubun-br kernel: [   36.223200] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 13 08:16:35 ubun-br kernel: [   36.223381] pci 0000:00:12.0: set SATA to AHCI mode
Jun 13 08:16:35 ubun-br kernel: [   36.224445] PCI: Transparent bridge - 0000:00:14.4
Jun 13 08:16:35 ubun-br kernel: [   36.224468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 13 08:16:35 ubun-br kernel: [   36.224675] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Jun 13 08:16:35 ubun-br kernel: [   36.235661] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 13 08:16:35 ubun-br kernel: [   36.235743] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 13 08:16:35 ubun-br kernel: [   36.235822] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 13 08:16:35 ubun-br kernel: [   36.235896] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 13 08:16:35 ubun-br kernel: [   36.235971] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 13 08:16:35 ubun-br kernel: [   36.236044] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 13 08:16:35 ubun-br kernel: [   36.236115] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 13 08:16:35 ubun-br kernel: [   36.236183] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Jun 13 08:16:35 ubun-br kernel: [   36.236269] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 13 08:16:35 ubun-br kernel: [   36.236287] pnp: PnP ACPI init
Jun 13 08:16:35 ubun-br kernel: [   36.236292] ACPI: bus type pnp registered
Jun 13 08:16:35 ubun-br kernel: [   36.238508] pnp: PnP ACPI: found 15 devices
Jun 13 08:16:35 ubun-br kernel: [   36.238510] ACPI: ACPI bus type pnp unregistered
Jun 13 08:16:35 ubun-br kernel: [   36.238649] PCI: Using ACPI for IRQ routing
Jun 13 08:16:35 ubun-br kernel: [   36.238651] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 13 08:16:35 ubun-br kernel: [   36.250146] NET: Registered protocol family 8
Jun 13 08:16:35 ubun-br kernel: [   36.250148] NET: Registered protocol family 20
Jun 13 08:16:35 ubun-br kernel: [   36.250199] PCI-DMA: Disabling AGP.
Jun 13 08:16:35 ubun-br kernel: [   36.251184] PCI-DMA: aperture base @ 4000000 size 65536 KB
Jun 13 08:16:35 ubun-br kernel: [   36.251188] PCI-DMA: using GART IOMMU.
Jun 13 08:16:35 ubun-br kernel: [   36.251193] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun 13 08:16:35 ubun-br kernel: [   36.252109] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jun 13 08:16:35 ubun-br kernel: [   36.252113] hpet0: 4 32-bit timers, 14318180 Hz
Jun 13 08:16:35 ubun-br kernel: [   36.253159] AppArmor: AppArmor Filesystem Enabled
Jun 13 08:16:35 ubun-br kernel: [   36.254105] Time: hpet clocksource has been installed.
Jun 13 08:16:35 ubun-br kernel: [   36.254120] Switched to high resolution mode on CPU 0
Jun 13 08:16:35 ubun-br kernel: [   36.254414] Switched to high resolution mode on CPU 3
Jun 13 08:16:35 ubun-br kernel: [   36.254418] Switched to high resolution mode on CPU 1
Jun 13 08:16:35 ubun-br kernel: [   36.254423] Switched to high resolution mode on CPU 2
Jun 13 08:16:35 ubun-br kernel: [   36.262131] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262134] system 00:01: ioport range 0x220-0x225 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262136] system 00:01: ioport range 0x290-0x294 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262141] system 00:02: ioport range 0x4100-0x411f has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262143] system 00:02: ioport range 0x228-0x22f has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262145] system 00:02: ioport range 0x40b-0x40b has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262147] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262149] system 00:02: ioport range 0xc00-0xc01 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262151] system 00:02: ioport range 0xc14-0xc14 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262152] system 00:02: ioport range 0xc50-0xc52 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262154] system 00:02: ioport range 0xc6c-0xc6d has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262156] system 00:02: ioport range 0xc6f-0xc6f has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262158] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262160] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262161] system 00:02: ioport range 0xcd4-0xcdf has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262163] system 00:02: ioport range 0x4000-0x40fe has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262165] system 00:02: ioport range 0x4210-0x4217 has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262167] system 00:02: ioport range 0xb00-0xb1f could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262169] system 00:02: ioport range 0x238-0x23f has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262180] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262185] system 00:0e: iomem range 0xf0000-0xf3fff could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262187] system 00:0e: iomem range 0xf4000-0xf7fff could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262189] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262191] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262193] system 00:0e: iomem range 0xcfee0000-0xcfefffff could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262196] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262198] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262200] system 00:0e: iomem range 0x100000-0xcfedffff could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262202] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262204] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262206] system 00:0e: iomem range 0xfff80000-0xfffeffff has been reserved
Jun 13 08:16:35 ubun-br kernel: [   36.262492] PCI: Bridge: 0000:00:02.0
Jun 13 08:16:35 ubun-br kernel: [   36.262495]   IO window: d000-dfff
Jun 13 08:16:35 ubun-br kernel: [   36.262497]   MEM window: fde00000-fdefffff
Jun 13 08:16:35 ubun-br kernel: [   36.262499]   PREFETCH window: d0000000-dfffffff
Jun 13 08:16:35 ubun-br kernel: [   36.262502] PCI: Bridge: 0000:00:0a.0
Jun 13 08:16:35 ubun-br kernel: [   36.262504]   IO window: e000-efff
Jun 13 08:16:35 ubun-br kernel: [   36.262506]   MEM window: fdd00000-fddfffff
Jun 13 08:16:35 ubun-br kernel: [   36.262508]   PREFETCH window: fdf00000-fdffffff
Jun 13 08:16:35 ubun-br kernel: [   36.262511] PCI: Bridge: 0000:00:14.4
Jun 13 08:16:35 ubun-br kernel: [   36.262513]   IO window: c000-cfff
Jun 13 08:16:35 ubun-br kernel: [   36.262517]   MEM window: fdc00000-fdcfffff
Jun 13 08:16:35 ubun-br kernel: [   36.262521]   PREFETCH window: fdb00000-fdbfffff
Jun 13 08:16:35 ubun-br kernel: [   36.262533] PCI: Setting latency timer of device 0000:00:02.0 to 64
Jun 13 08:16:35 ubun-br kernel: [   36.262540] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Jun 13 08:16:35 ubun-br kernel: [   36.262554] NET: Registered protocol family 2
Jun 13 08:16:35 ubun-br kernel: [   36.298106] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 13 08:16:35 ubun-br kernel: [   36.298942] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 13 08:16:35 ubun-br kernel: [   36.301610] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 13 08:16:35 ubun-br kernel: [   36.301960] TCP: Hash tables configured (established 524288 bind 65536)
Jun 13 08:16:35 ubun-br kernel: [   36.301963] TCP reno registered
Jun 13 08:16:35 ubun-br kernel: [   36.310101] checking if image is initramfs... it is
Jun 13 08:16:35 ubun-br kernel: [   36.800682] Freeing initrd memory: 8185k freed
Jun 13 08:16:35 ubun-br kernel: [   36.804517] audit: initializing netlink socket (disabled)
Jun 13 08:16:35 ubun-br kernel: [   36.804527] audit(1213366467.324:1): initialized
Jun 13 08:16:35 ubun-br kernel: [   36.806194] VFS: Disk quotas dquot_6.5.1
Jun 13 08:16:35 ubun-br kernel: [   36.806247] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 13 08:16:35 ubun-br kernel: [   36.806347] io scheduler noop registered
Jun 13 08:16:35 ubun-br kernel: [   36.806349] io scheduler anticipatory registered
Jun 13 08:16:35 ubun-br kernel: [   36.806350] io scheduler deadline registered
Jun 13 08:16:35 ubun-br kernel: [   36.806422] io scheduler cfq registered (default)
Jun 13 08:16:35 ubun-br kernel: [   36.946452] Boot video device is 0000:01:00.0
Jun 13 08:16:35 ubun-br kernel: [   36.946582] PCI: Setting latency timer of device 0000:00:02.0 to 64
Jun 13 08:16:35 ubun-br kernel: [   36.946604] assign_interrupt_mode Found MSI capability
Jun 13 08:16:35 ubun-br kernel: [   36.946628] Allocate Port Service[0000:00:02.0:pcie00]
Jun 13 08:16:35 ubun-br kernel: [   36.946683] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Jun 13 08:16:35 ubun-br kernel: [   36.946704] assign_interrupt_mode Found MSI capability
Jun 13 08:16:35 ubun-br kernel: [   36.946724] Allocate Port Service[0000:00:0a.0:pcie00]
Jun 13 08:16:35 ubun-br kernel: [   36.966436] Real Time Clock Driver v1.12ac
Jun 13 08:16:35 ubun-br kernel: [   36.966551] hpet_resources: 0xfed00000 is busy
Jun 13 08:16:35 ubun-br kernel: [   36.966584] Linux agpgart interface v0.102
Jun 13 08:16:35 ubun-br kernel: [   36.966585] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 13 08:16:35 ubun-br kernel: [   36.966707] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 13 08:16:35 ubun-br kernel: [   36.967140] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 13 08:16:35 ubun-br kernel: [   36.967639] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 13 08:16:35 ubun-br kernel: [   36.967682] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 13 08:16:35 ubun-br kernel: [   36.967742] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 13 08:16:35 ubun-br kernel: [   36.968120] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 13 08:16:35 ubun-br kernel: [   36.968126] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 13 08:16:35 ubun-br kernel: [   36.977880] mice: PS/2 mouse device common for all mice
Jun 13 08:16:35 ubun-br kernel: [   36.977912] cpuidle: using governor ladder
Jun 13 08:16:35 ubun-br kernel: [   36.977913] cpuidle: using governor menu
Jun 13 08:16:35 ubun-br kernel: [   36.978018] NET: Registered protocol family 1
Jun 13 08:16:35 ubun-br kernel: [   36.978064] registered taskstats version 1
Jun 13 08:16:35 ubun-br kernel: [   36.978155]   Magic number: 12:627:232
Jun 13 08:16:35 ubun-br kernel: [   36.978170]   hash matches device ttyv2
Jun 13 08:16:35 ubun-br kernel: [   36.978228] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jun 13 08:16:35 ubun-br kernel: [   36.978230] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 13 08:16:35 ubun-br kernel: [   36.978232] EDD information not available.
Jun 13 08:16:35 ubun-br kernel: [   36.978241] Freeing unused kernel memory: 316k freed
Jun 13 08:16:35 ubun-br kernel: [   37.017087] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 13 08:16:35 ubun-br kernel: [   38.128129] fuse init (API version 7.9)
Jun 13 08:16:35 ubun-br kernel: [   38.231859] usbcore: registered new interface driver usbfs
Jun 13 08:16:35 ubun-br kernel: [   38.231876] usbcore: registered new interface driver hub
Jun 13 08:16:35 ubun-br kernel: [   38.243409] SCSI subsystem initialized
Jun 13 08:16:35 ubun-br kernel: [   38.248136] usbcore: registered new device driver usb
Jun 13 08:16:35 ubun-br kernel: [   38.255360] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 13 08:16:35 ubun-br kernel: [   38.255398] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 13 08:16:35 ubun-br kernel: [   38.255993] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 13 08:16:35 ubun-br kernel: [   38.256186] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jun 13 08:16:35 ubun-br kernel: [   38.256215] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Jun 13 08:16:35 ubun-br kernel: [   38.289222] libata version 3.00 loaded.
Jun 13 08:16:35 ubun-br kernel: [   38.316077] usb usb1: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   38.316097] hub 1-0:1.0: USB hub found
Jun 13 08:16:35 ubun-br kernel: [   38.316106] hub 1-0:1.0: 2 ports detected
Jun 13 08:16:35 ubun-br kernel: [   38.325156] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 13 08:16:35 ubun-br kernel: [   38.325162] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 13 08:16:35 ubun-br kernel: [   38.345278] Floppy drive(s): fd0 is 1.44M
Jun 13 08:16:35 ubun-br kernel: [   38.363222] FDC 0 is a post-1991 82077
Jun 13 08:16:35 ubun-br kernel: [   38.419870] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jun 13 08:16:35 ubun-br kernel: [   38.420460] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jun 13 08:16:35 ubun-br kernel: [   38.420509] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jun 13 08:16:35 ubun-br kernel: [   38.420531] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Jun 13 08:16:35 ubun-br kernel: [   38.479767] usb usb2: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   38.479788] hub 2-0:1.0: USB hub found
Jun 13 08:16:35 ubun-br kernel: [   38.479796] hub 2-0:1.0: 2 ports detected
Jun 13 08:16:35 ubun-br kernel: [   38.583592] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jun 13 08:16:35 ubun-br kernel: [   38.584182] ohci_hcd 0000:00:13.2: OHCI Host Controller
Jun 13 08:16:35 ubun-br kernel: [   38.584230] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jun 13 08:16:35 ubun-br kernel: [   38.584252] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Jun 13 08:16:35 ubun-br kernel: [   38.643477] usb usb3: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   38.643494] hub 3-0:1.0: USB hub found
Jun 13 08:16:35 ubun-br kernel: [   38.643502] hub 3-0:1.0: 2 ports detected
Jun 13 08:16:35 ubun-br kernel: [   38.733741] usb 1-1: new full speed USB device using ohci_hcd and address 2
Jun 13 08:16:35 ubun-br kernel: [   38.745783] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jun 13 08:16:35 ubun-br kernel: [   38.746385] ohci_hcd 0000:00:13.3: OHCI Host Controller
Jun 13 08:16:35 ubun-br kernel: [   38.746438] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Jun 13 08:16:35 ubun-br kernel: [   38.746453] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Jun 13 08:16:35 ubun-br kernel: [   38.805701] usb usb4: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   38.805719] hub 4-0:1.0: USB hub found
Jun 13 08:16:35 ubun-br kernel: [   38.805726] hub 4-0:1.0: 2 ports detected
Jun 13 08:16:35 ubun-br kernel: [   38.909490] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jun 13 08:16:35 ubun-br kernel: [   38.910062] ohci_hcd 0000:00:13.4: OHCI Host Controller
Jun 13 08:16:35 ubun-br kernel: [   38.910116] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Jun 13 08:16:35 ubun-br kernel: [   38.910132] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Jun 13 08:16:35 ubun-br kernel: [   38.949994] usb 1-1: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   38.970908] usb usb5: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   38.970927] hub 5-0:1.0: USB hub found
Jun 13 08:16:35 ubun-br kernel: [   38.970934] hub 5-0:1.0: 2 ports detected
Jun 13 08:16:35 ubun-br kernel: [   39.074739] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
Jun 13 08:16:35 ubun-br kernel: [   39.074750] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jun 13 08:16:35 ubun-br kernel: [   39.074759] SB600_PATA: not 100% native mode: will probe irqs later
Jun 13 08:16:35 ubun-br kernel: [   39.074767]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:DMA, hdb:pio
Jun 13 08:16:35 ubun-br kernel: [   39.074777] Probing IDE interface ide0...
Jun 13 08:16:35 ubun-br kernel: [   39.264802] usb 3-2: new full speed USB device using ohci_hcd and address 2
Jun 13 08:16:35 ubun-br kernel: [   39.488049] usb 3-2: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   39.490182] usbcore: registered new interface driver libusual
Jun 13 08:16:35 ubun-br kernel: [   39.497018] Initializing USB Mass Storage driver...
Jun 13 08:16:35 ubun-br kernel: [   39.799857] usb 4-1: new full speed USB device using ohci_hcd and address 2
Jun 13 08:16:35 ubun-br kernel: [   40.021640] usb 4-1: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   40.151571] hda: HL-DT-STDVD-RAM GSA-H22L, ATAPI CD/DVD-ROM drive
Jun 13 08:16:35 ubun-br kernel: [   40.151596] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Jun 13 08:16:35 ubun-br kernel: [   40.151727] hda: UDMA/66 mode selected
Jun 13 08:16:35 ubun-br kernel: [   40.152046] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jun 13 08:16:35 ubun-br kernel: [   40.154538] ahci 0000:00:12.0: version 3.0
Jun 13 08:16:35 ubun-br kernel: [   40.154569] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
Jun 13 08:16:35 ubun-br kernel: [   40.155160] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Jun 13 08:16:35 ubun-br kernel: [   40.155164] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Jun 13 08:16:35 ubun-br kernel: [   40.330923] usb 4-2: new full speed USB device using ohci_hcd and address 3
Jun 13 08:16:35 ubun-br kernel: [   40.553737] usb 4-2: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   40.555835] scsi0 : SCSI emulation for USB Mass Storage devices
Jun 13 08:16:35 ubun-br kernel: [   40.555872] usb-storage: device found at 2
Jun 13 08:16:35 ubun-br kernel: [   40.555876] usb-storage: waiting for device to settle before scanning
Jun 13 08:16:35 ubun-br kernel: [   40.555931] scsi1 : SCSI emulation for USB Mass Storage devices
Jun 13 08:16:35 ubun-br kernel: [   40.555962] usb-storage: device found at 3
Jun 13 08:16:35 ubun-br kernel: [   40.555964] usb-storage: waiting for device to settle before scanning
Jun 13 08:16:35 ubun-br kernel: [   40.555968] usbcore: registered new interface driver usb-storage
Jun 13 08:16:35 ubun-br kernel: [   40.555971] USB Mass Storage support registered.
Jun 13 08:16:35 ubun-br kernel: [   41.155000] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jun 13 08:16:35 ubun-br kernel: [   41.155004] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Jun 13 08:16:35 ubun-br kernel: [   41.155190] scsi2 : ahci
Jun 13 08:16:35 ubun-br kernel: [   41.155249] scsi3 : ahci
Jun 13 08:16:35 ubun-br kernel: [   41.155290] scsi4 : ahci
Jun 13 08:16:35 ubun-br kernel: [   41.155323] scsi5 : ahci
Jun 13 08:16:35 ubun-br kernel: [   41.155373] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Jun 13 08:16:35 ubun-br kernel: [   41.155376] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Jun 13 08:16:35 ubun-br kernel: [   41.155379] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Jun 13 08:16:35 ubun-br kernel: [   41.155382] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Jun 13 08:16:35 ubun-br kernel: [   41.628639] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 13 08:16:35 ubun-br kernel: [   41.631433] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
Jun 13 08:16:35 ubun-br kernel: [   41.631438] ata1.00: ATA-8: ST3500320AS, SD15, max UDMA/133
Jun 13 08:16:35 ubun-br kernel: [   41.631440] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 13 08:16:35 ubun-br kernel: [   41.633172] ata1.00: configured for UDMA/133
Jun 13 08:16:35 ubun-br kernel: [   42.107795] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 13 08:16:35 ubun-br kernel: [   42.112760] ata2.00: ATA-7: SAMSUNG SP2004C, VM100-31, max UDMA7
Jun 13 08:16:35 ubun-br kernel: [   42.112763] ata2.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 13 08:16:35 ubun-br kernel: [   42.117769] ata2.00: configured for UDMA/133
Jun 13 08:16:35 ubun-br kernel: [   42.590939] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 13 08:16:35 ubun-br kernel: [   42.749316] ata3.00: ATAPI: HL-DT-ST DVDRAM GH20NS10, EL01, max UDMA/100
Jun 13 08:16:35 ubun-br kernel: [   42.906085] ata3.00: configured for UDMA/100
Jun 13 08:16:35 ubun-br kernel: [   43.217834] ata4: SATA link down (SStatus 0 SControl 300)
Jun 13 08:16:35 ubun-br kernel: [   43.217921] scsi 2:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
Jun 13 08:16:35 ubun-br kernel: [   43.217993] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG SP2004C  VM10 PQ: 0 ANSI: 5
Jun 13 08:16:35 ubun-br kernel: [   43.220901] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS10  EL01 PQ: 0 ANSI: 5
Jun 13 08:16:35 ubun-br kernel: [   43.221021] r8169 Gigabit Ethernet driver 2.2LK loaded
Jun 13 08:16:35 ubun-br kernel: [   43.221041] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Jun 13 08:16:35 ubun-br kernel: [   43.221059] PCI: Setting latency timer of device 0000:02:00.0 to 64
Jun 13 08:16:35 ubun-br kernel: [   43.221284] eth0: RTL8168b/8111b at 0xffffc20001040000, 00:1d:7d:d7:e0:2c, XID 38000000 IRQ 509
Jun 13 08:16:35 ubun-br kernel: [   43.222405] ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 22 (level, low) -> IRQ 22
Jun 13 08:16:35 ubun-br kernel: [   43.222408] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Jun 13 08:16:35 ubun-br kernel: [   43.223010] ehci_hcd 0000:00:13.5: EHCI Host Controller
Jun 13 08:16:35 ubun-br kernel: [   43.223061] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Jun 13 08:16:35 ubun-br kernel: [   43.223099] ehci_hcd 0000:00:13.5: debug port 1
Jun 13 08:16:35 ubun-br kernel: [   43.223116] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Jun 13 08:16:35 ubun-br kernel: [   43.223165] usb 1-1: USB disconnect, address 2
Jun 13 08:16:35 ubun-br kernel: [   43.234806] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 13 08:16:35 ubun-br kernel: [   43.234894] usb usb6: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   43.234911] hub 6-0:1.0: USB hub found
Jun 13 08:16:35 ubun-br kernel: [   43.234916] hub 6-0:1.0: 10 ports detected
Jun 13 08:16:35 ubun-br kernel: [   43.274884] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun 13 08:16:35 ubun-br kernel: [   43.275124] Driver 'sd' needs updating - please use bus_type methods
Jun 13 08:16:35 ubun-br kernel: [   43.275190] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Jun 13 08:16:35 ubun-br kernel: [   43.275198] sd 2:0:0:0: [sda] Write Protect is off
Jun 13 08:16:35 ubun-br kernel: [   43.275199] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 13 08:16:35 ubun-br kernel: [   43.275214] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 13 08:16:35 ubun-br kernel: [   43.275257] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Jun 13 08:16:35 ubun-br kernel: [   43.275262] sd 2:0:0:0: [sda] Write Protect is off
Jun 13 08:16:35 ubun-br kernel: [   43.275264] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 13 08:16:35 ubun-br kernel: [   43.275272] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 13 08:16:35 ubun-br kernel: [   43.275274]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jun 13 08:16:35 ubun-br kernel: [   43.295026]  sda1 sda2 < sda5 >
Jun 13 08:16:35 ubun-br kernel: [   43.319295] sd 2:0:0:0: [sda] Attached SCSI disk
Jun 13 08:16:35 ubun-br kernel: [   43.319338] sd 3:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Jun 13 08:16:35 ubun-br kernel: [   43.319345] sd 3:0:0:0: [sdb] Write Protect is off
Jun 13 08:16:35 ubun-br kernel: [   43.319347] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun 13 08:16:35 ubun-br kernel: [   43.319356] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 13 08:16:35 ubun-br kernel: [   43.319386] sd 3:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Jun 13 08:16:35 ubun-br kernel: [   43.319391] sd 3:0:0:0: [sdb] Write Protect is off
Jun 13 08:16:35 ubun-br kernel: [   43.319393] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jun 13 08:16:35 ubun-br kernel: [   43.319402] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 13 08:16:35 ubun-br kernel: [   43.319404]  sdb: sdb1 sdb2 < sdb5 >
Jun 13 08:16:35 ubun-br kernel: [   43.345405] sd 3:0:0:0: [sdb] Attached SCSI disk
Jun 13 08:16:35 ubun-br kernel: [   43.349839] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jun 13 08:16:35 ubun-br kernel: [   43.349855] sd 3:0:0:0: Attached scsi generic sg1 type 0
Jun 13 08:16:35 ubun-br kernel: [   43.349868] sr 4:0:0:0: Attached scsi generic sg2 type 5
Jun 13 08:16:35 ubun-br kernel: [   43.359627] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Jun 13 08:16:35 ubun-br kernel: [   43.359631] Uniform CD-ROM driver Revision: 3.20
Jun 13 08:16:35 ubun-br kernel: [   43.370575] usb 4-1: USB disconnect, address 2
Jun 13 08:16:35 ubun-br kernel: [   43.498339] usb 4-2: USB disconnect, address 3
Jun 13 08:16:35 ubun-br kernel: [   43.530299] Attempting manual resume
Jun 13 08:16:35 ubun-br kernel: [   43.530302] swsusp: Resume From Partition 8:5
Jun 13 08:16:35 ubun-br kernel: [   43.530303] PM: Checking swsusp image.
Jun 13 08:16:35 ubun-br kernel: [   43.530973] PM: Resume from disk failed.
Jun 13 08:16:35 ubun-br kernel: [   43.581336] kjournald starting.  Commit interval 5 seconds
Jun 13 08:16:35 ubun-br kernel: [   43.581343] EXT3-fs: mounted filesystem with ordered data mode.
Jun 13 08:16:35 ubun-br kernel: [   43.626133] usb 3-2: USB disconnect, address 2
Jun 13 08:16:35 ubun-br kernel: [   43.783118] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 13 08:16:35 ubun-br kernel: [   43.783159] sr 4:0:0:0: Attached scsi CD-ROM sr0
Jun 13 08:16:35 ubun-br kernel: [   43.993463] usb 6-1: new high speed USB device using ehci_hcd and address 2
Jun 13 08:16:35 ubun-br kernel: [   44.127649] usb 6-1: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   44.127894] scsi6 : SCSI emulation for USB Mass Storage devices
Jun 13 08:16:35 ubun-br kernel: [   44.127979] usb-storage: device found at 2
Jun 13 08:16:35 ubun-br kernel: [   44.127981] usb-storage: waiting for device to settle before scanning
Jun 13 08:16:35 ubun-br kernel: [   44.544587] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00db733e00001d7d]
Jun 13 08:16:35 ubun-br kernel: [   44.843956] usb 6-8: new high speed USB device using ehci_hcd and address 5
Jun 13 08:16:35 ubun-br kernel: [   44.984932] usb 6-8: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   44.985045] scsi7 : SCSI emulation for USB Mass Storage devices
Jun 13 08:16:35 ubun-br kernel: [   44.985130] usb-storage: device found at 5
Jun 13 08:16:35 ubun-br kernel: [   44.985131] usb-storage: waiting for device to settle before scanning
Jun 13 08:16:35 ubun-br kernel: [   45.295158] usb 3-2: new full speed USB device using ohci_hcd and address 3
Jun 13 08:16:35 ubun-br kernel: [   45.513759] usb 3-2: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   45.825217] usb 4-1: new full speed USB device using ohci_hcd and address 4
Jun 13 08:16:35 ubun-br kernel: [   46.048022] usb 4-1: configuration #1 chosen from 1 choice
Jun 13 08:16:35 ubun-br kernel: [   48.238544] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 13 08:16:35 ubun-br kernel: [   48.290521] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 13 08:16:35 ubun-br kernel: [   48.319167] input: Power Button (FF) as /devices/virtual/input/input2
Jun 13 08:16:35 ubun-br kernel: [   48.340516] ACPI: Power Button (FF) [PWRF]
Jun 13 08:16:35 ubun-br kernel: [   48.340579] input: Power Button (CM) as /devices/virtual/input/input3
Jun 13 08:16:35 ubun-br kernel: [   48.370261] ACPI: Power Button (CM) [PWRB]
Jun 13 08:16:35 ubun-br kernel: [   48.454164] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jun 13 08:16:35 ubun-br kernel: [   48.804105] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0181
Jun 13 08:16:35 ubun-br kernel: [   48.804122] usbcore: registered new interface driver usblp
Jun 13 08:16:35 ubun-br kernel: [   48.860736] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jun 13 08:16:35 ubun-br kernel: [   48.918656] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 18 (level, low) -> IRQ 18
Jun 13 08:16:35 ubun-br kernel: [   48.919222] PCI: Setting latency timer of device 0000:01:00.1 to 64
Jun 13 08:16:35 ubun-br kernel: [   48.919445] input: PC Speaker as /devices/platform/pcspkr/input/input4
Jun 13 08:16:35 ubun-br kernel: [   49.116849] usb-storage: device scan complete
Jun 13 08:16:35 ubun-br kernel: [   49.117195] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
Jun 13 08:16:35 ubun-br kernel: [   49.117916] sd 6:0:0:0: [sdc] 1994752 512-byte hardware sectors (1021 MB)
Jun 13 08:16:35 ubun-br kernel: [   49.118169] sd 6:0:0:0: [sdc] Write Protect is off
Jun 13 08:16:35 ubun-br kernel: [   49.118171] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
Jun 13 08:16:35 ubun-br kernel: [   49.118172] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Jun 13 08:16:35 ubun-br kernel: [   49.135886] usbcore: registered new interface driver snd-usb-audio
Jun 13 08:16:35 ubun-br kernel: [   49.271631] sd 6:0:0:0: [sdc] 1994752 512-byte hardware sectors (1021 MB)
Jun 13 08:16:35 ubun-br kernel: [   49.282325] irq 19: nobody cared (try booting with the "irqpoll" option)
Jun 13 08:16:35 ubun-br kernel: [   49.282329] Pid: 3319, comm: modprobe Not tainted 2.6.24-16-generic #1
Jun 13 08:16:35 ubun-br kernel: [   49.282331] 
Jun 13 08:16:35 ubun-br kernel: [   49.282332] Call Trace:
Jun 13 08:16:35 ubun-br kernel: [   49.282333]  <IRQ>  [__report_bad_irq+0x1e/0x80] __report_bad_irq+0x1e/0x80
Jun 13 08:16:35 ubun-br kernel: [   49.282346]  [note_interrupt+0x2ad/0x2e0] note_interrupt+0x2ad/0x2e0
Jun 13 08:16:35 ubun-br kernel: [   49.282351]  [handle_fasteoi_irq+0xa1/0x110] handle_fasteoi_irq+0xa1/0x110
Jun 13 08:16:35 ubun-br kernel: [   49.282355]  [do_IRQ+0x7b/0x100] do_IRQ+0x7b/0x100
Jun 13 08:16:35 ubun-br kernel: [   49.282358]  [ret_from_intr+0x0/0x0a] ret_from_intr+0x0/0xa
Jun 13 08:16:35 ubun-br kernel: [   49.282360]  <EOI>  [__delay+0x8/0x20] __delay+0x8/0x20
Jun 13 08:16:35 ubun-br kernel: [   49.282381]  [snd_hda_intel:azx_get_response+0x12c/0x200] :snd_hda_intel:azx_get_response+0x12c/0x200
Jun 13 08:16:35 ubun-br kernel: [   49.282392]  [snd_hda_intel:snd_hda_codec_read+0x6a/0xb0] :snd_hda_intel:snd_hda_codec_read+0x6a/0xb0
Jun 13 08:16:35 ubun-br kernel: [   49.282403]  [snd_hda_intel:snd_hda_codec_new+0xf9/0x580] :snd_hda_intel:snd_hda_codec_new+0xf9/0x580
Jun 13 08:16:35 ubun-br kernel: [   49.282414]  [snd_hda_intel:azx_probe+0x816/0xb60] :snd_hda_intel:azx_probe+0x816/0xb60
Jun 13 08:16:35 ubun-br kernel: [   49.282423]  [snd_hda_intel:azx_send_cmd+0x0/0xf0] :snd_hda_intel:azx_send_cmd+0x0/0xf0
Jun 13 08:16:35 ubun-br kernel: [   49.282431]  [snd_hda_intel:azx_get_response+0x0/0x200] :snd_hda_intel:azx_get_response+0x0/0x200
Jun 13 08:16:35 ubun-br kernel: [   49.282439]  [snd_hda_intel:azx_power_notify+0x0/0x60] :snd_hda_intel:azx_power_notify+0x0/0x60
Jun 13 08:16:35 ubun-br kernel: [   49.282446]  [pci_device_probe+0xf8/0x170] pci_device_probe+0xf8/0x170
Jun 13 08:16:35 ubun-br kernel: [   49.282451]  [driver_probe_device+0x9c/0x1b0] driver_probe_device+0x9c/0x1b0
Jun 13 08:16:35 ubun-br kernel: [   49.282455]  [__driver_attach+0xc9/0xd0] __driver_attach+0xc9/0xd0
Jun 13 08:16:35 ubun-br kernel: [   49.282457]  [__driver_attach+0x0/0xd0] __driver_attach+0x0/0xd0
Jun 13 08:16:35 ubun-br kernel: [   49.282460]  [scsi_mod:bus_for_each_dev+0x4d/0x100] bus_for_each_dev+0x4d/0x80
Jun 13 08:16:35 ubun-br kernel: [   49.282464]  [bus_add_driver+0xac/0x220] bus_add_driver+0xac/0x220
Jun 13 08:16:35 ubun-br kernel: [   49.282468]  [parport_pc:__pci_register_driver+0x69/0x6a0] __pci_register_driver+0x69/0xb0
Jun 13 08:16:35 ubun-br kernel: [   49.282472]  [sys_init_module+0x18e/0x1a90] sys_init_module+0x18e/0x1a90
Jun 13 08:16:35 ubun-br kernel: [   49.282489]  [snd_pcm_oss:snd_pcm_format_width+0x0/0x30] :snd_pcm:snd_pcm_format_width+0x0/0x30
Jun 13 08:16:35 ubun-br kernel: [   49.282495]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Jun 13 08:16:35 ubun-br kernel: [   49.282500] 
Jun 13 08:16:35 ubun-br kernel: [   49.282500] handlers:
Jun 13 08:16:35 ubun-br kernel: [   49.282502] [usbcore:usb_hcd_irq+0x0/0x60] (usb_hcd_irq+0x0/0x60 [usbcore])
Jun 13 08:16:35 ubun-br kernel: [   49.282515] Disabling IRQ #19
Jun 13 08:16:35 ubun-br kernel: [   49.323537] sd 6:0:0:0: [sdc] Write Protect is off
Jun 13 08:16:35 ubun-br kernel: [   49.323540] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
Jun 13 08:16:35 ubun-br kernel: [   49.323542] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Jun 13 08:16:35 ubun-br kernel: [   49.323545]  sdc: sdc1
Jun 13 08:16:35 ubun-br kernel: [   49.574821] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Jun 13 08:16:35 ubun-br kernel: [   49.574857] sd 6:0:0:0: Attached scsi generic sg3 type 0
Jun 13 08:16:35 ubun-br kernel: [   49.586237] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jun 13 08:16:35 ubun-br kernel: [   49.933963] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
Jun 13 08:16:35 ubun-br kernel: [   50.034228] parport_pc 00:0a: reported by Plug and Play ACPI
Jun 13 08:16:35 ubun-br kernel: [   50.034335] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jun 13 08:16:35 ubun-br kernel: [   50.986570] usb-storage: device scan complete
Jun 13 08:16:35 ubun-br kernel: [   56.598218] usb 6-8: reset high speed USB device using ehci_hcd and address 5
Jun 13 08:16:35 ubun-br kernel: [   72.126834] usb 6-8: device not accepting address 5, error -110
Jun 13 08:16:35 ubun-br kernel: [   72.238626] usb 6-8: reset high speed USB device using ehci_hcd and address 5
Jun 13 08:16:35 ubun-br kernel: [   87.767248] usb 6-8: device not accepting address 5, error -110
Jun 13 08:16:35 ubun-br kernel: [   87.879048] usb 6-8: reset high speed USB device using ehci_hcd and address 5
Jun 13 08:16:35 ubun-br kernel: [   98.292682] usb 6-8: device not accepting address 5, error -110
Jun 13 08:16:35 ubun-br kernel: [   98.404481] usb 6-8: reset high speed USB device using ehci_hcd and address 5
Jun 13 08:16:35 ubun-br kernel: [  108.818115] usb 6-8: device not accepting address 5, error -110
Jun 13 08:16:35 ubun-br kernel: [  108.818133] usb 6-8: USB disconnect, address 5
Jun 13 08:16:35 ubun-br kernel: [  108.818248] scsi 7:0:0:0: Device offlined - not ready after error recovery
Jun 13 08:16:35 ubun-br kernel: [  108.929916] usb 6-1: reset high speed USB device using ehci_hcd and address 2
Jun 13 08:16:35 ubun-br kernel: [  124.458527] usb 6-1: device not accepting address 2, error -110
Jun 13 08:16:35 ubun-br kernel: [  124.570325] usb 6-1: reset high speed USB device using ehci_hcd and address 2
Jun 13 08:16:35 ubun-br kernel: [  140.098928] usb 6-1: device not accepting address 2, error -110
Jun 13 08:16:35 ubun-br kernel: [  140.210736] usb 6-1: reset high speed USB device using ehci_hcd and address 2
Jun 13 08:16:35 ubun-br kernel: [  150.624370] usb 6-1: device not accepting address 2, error -110
Jun 13 08:16:35 ubun-br kernel: [  150.736170] usb 6-1: reset high speed USB device using ehci_hcd and address 2
Jun 13 08:16:35 ubun-br kernel: [  161.149804] usb 6-1: device not accepting address 2, error -110
Jun 13 08:16:35 ubun-br kernel: [  161.149822] sd 6:0:0:0: Device offlined - not ready after error recovery
Jun 13 08:16:35 ubun-br kernel: [  161.262594] usb 6-8: new high speed USB device using ehci_hcd and address 6
Jun 13 08:16:35 ubun-br kernel: [  161.804298] lp0: using parport0 (interrupt-driven).
Jun 13 08:16:35 ubun-br kernel: [  161.875047] Adding 11871992k swap on /dev/sda5.  Priority:-1 extents:1 across:11871992k
Jun 13 08:16:35 ubun-br kernel: [  162.407872] EXT3 FS on sda1, internal journal
Jun 13 08:16:35 ubun-br kernel: [  163.514806] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 13 08:16:35 ubun-br kernel: [  163.794763] No dock devices found.
Jun 13 08:16:35 ubun-br kernel: [  164.592608] ppdev: user-space parallel port driver
Jun 13 08:16:35 ubun-br kernel: [  164.679947] audit(1213366595.948:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5949 profile="/usr/sbin/cupsd" namespace="default"
Jun 13 08:16:37 ubun-br kernel: [  166.328288] r8169: eth0: link up
Jun 13 08:16:37 ubun-br kernel: [  166.328295] r8169: eth0: link up
Jun 13 08:16:37 ubun-br kernel: [  166.384205] Bluetooth: Core ver 2.11
Jun 13 08:16:37 ubun-br kernel: [  166.384454] NET: Registered protocol family 31
Jun 13 08:16:37 ubun-br kernel: [  166.384458] Bluetooth: HCI device and connection manager initialized
Jun 13 08:16:37 ubun-br kernel: [  166.384462] Bluetooth: HCI socket layer initialized
Jun 13 08:16:37 ubun-br kernel: [  166.389934] Bluetooth: L2CAP ver 2.9
Jun 13 08:16:37 ubun-br kernel: [  166.389938] Bluetooth: L2CAP socket layer initialized
Jun 13 08:16:37 ubun-br kernel: [  166.426412] Bluetooth: RFCOMM socket layer initialized
Jun 13 08:16:37 ubun-br kernel: [  166.426426] Bluetooth: RFCOMM TTY layer initialized
Jun 13 08:16:37 ubun-br kernel: [  166.426428] Bluetooth: RFCOMM ver 1.8
Jun 13 08:16:40 ubun-br kernel: [  169.715333] NET: Registered protocol family 17
Jun 13 08:16:42 ubun-br kernel: [  171.577051] NET: Registered protocol family 10
Jun 13 08:16:42 ubun-br kernel: [  171.577217] lo: Disabled Privacy Extensions
Jun 13 08:16:48 ubun-br kernel: [  176.790219] usb 6-8: device not accepting address 6, error -110
Jun 13 08:16:48 ubun-br kernel: [  176.902016] usb 6-8: new high speed USB device using ehci_hcd and address 7
Jun 13 08:16:54 ubun-br kernel: [  182.168741] eth0: no IPv6 routers present
Jun 13 08:17:04 ubun-br kernel: [  192.430629] usb 6-8: device not accepting address 7, error -110
Jun 13 08:17:04 ubun-br kernel: [  192.542425] usb 6-8: new high speed USB device using ehci_hcd and address 8
Jun 13 08:17:14 ubun-br kernel: [  202.956062] usb 6-8: device not accepting address 8, error -110
Jun 13 08:17:14 ubun-br kernel: [  203.067858] usb 6-8: new high speed USB device using ehci_hcd and address 9
Jun 13 08:17:25 ubun-br kernel: [  213.481492] usb 6-8: device not accepting address 9, error -110
Jun 13 08:17:25 ubun-br kernel: [  213.481553] usb 6-1: USB disconnect, address 2
Jun 13 08:17:25 ubun-br kernel: [  213.593295] usb 6-1: new high speed USB device using ehci_hcd and address 10
Jun 13 08:17:41 ubun-br kernel: [  229.121905] usb 6-1: device not accepting address 10, error -110
Jun 13 08:17:41 ubun-br kernel: [  229.233705] usb 6-1: new high speed USB device using ehci_hcd and address 11
Jun 13 08:17:56 ubun-br kernel: [  244.762316] usb 6-1: device not accepting address 11, error -110
Jun 13 08:17:56 ubun-br kernel: [  244.874110] usb 6-1: new high speed USB device using ehci_hcd and address 12
Jun 13 08:18:07 ubun-br kernel: [  255.287750] usb 6-1: device not accepting address 12, error -110
Jun 13 08:18:07 ubun-br kernel: [  255.399547] usb 6-1: new high speed USB device using ehci_hcd and address 13
Jun 13 08:18:17 ubun-br kernel: [  265.813182] usb 6-1: device not accepting address 13, error -110
Jun 13 08:18:22 ubun-br kernel: [  270.917857] hda-intel: Invalid position buffer, using LPIB read method instead.
Jun 13 08:18:27 ubun-br kernel: [  274.971000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 13 08:18:27 ubun-br kernel: [  274.971006] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jun 13 08:25:12 ubun-br kernel: [  680.184186] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 13 08:25:12 ubun-br kernel: [  680.184192] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jun 13 08:26:23 ubun-br kernel: [  750.871524] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 13 08:26:23 ubun-br kernel: [  750.871530] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jun 13 08:27:23 ubun-br kernel: [  810.492116] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 13 08:27:23 ubun-br kernel: [  810.492121] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jun 13 08:28:54 ubun-br kernel: [  901.365582] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 13 08:28:54 ubun-br kernel: [  901.365588] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jun 13 08:29:54 ubun-br kernel: [  960.851508] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 13 08:29:54 ubun-br kernel: [  960.851513] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jun 13 08:30:56 ubun-br kernel: [ 1022.720458] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 13 08:30:56 ubun-br kernel: [ 1022.720463] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jun 13 08:32:34 ubun-br kernel: [ 1120.567376] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 13 08:32:34 ubun-br kernel: [ 1120.567381] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jun 13 08:34:40 ubun-br kernel: [ 1246.727622] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jun 13 08:34:40 ubun-br kernel: [ 1246.727627] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.

Any suggestions anyone

---

### Post by krlhc8 on 2008-06-13
From the looks of your log, it seems as if you've been plagued by some sort of smiley virus! :)  

Okay seriously though, what kernel is everyone running?  It seems like the linux devs have been playing a "lesser of two evils" game by making things work for most people while breaking a minority of computers in the process.  In this case its between having functional suspend/hibernate work for most people and in the process screwing up USB on some computers.  

A potential easy fix for some would be to go into the BIOS and find anything USB related and dick with it, or as fenix1224 pointed out, set "Plug and Play O/S" to No in some BIOSes.  Or as MarkX pointed out: in some BIOSes, set PCI to AGP vid card. Otherwise you'll probably have to try a different flavor of kernel (yum).

Uploading a different kernel is really easy with synaptics package manager.  Open up synaptics, search for "linux-image", and select the appropriate kernel.  If you want the latest kernel available for Hardy (2.6.24-19), just check the "pre-released updates" checkbox in the updates tab in the >>settings>>repositories menu.  

If you find a kernel that works, you can have it run as default at startup.  To do this, open menu.lst:
```
sudo gedit /boot/grub/menu.lst
```
find the preferred kernel at the bottom of the page, and add the as the last line [COLOR="Red"]savedefault[/COLOR].  Example:

```

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=67f22489-03ea-4f91-9d26-ef4e8ffe7b02 ro single
initrd		/boot/initrd.img-2.6.24-18-generic
quiet
[COLOR="Red"]savedefault[/COLOR]

```

Note that you'll have to have to reset the default in menu.lst after each kernel upgrade.

I hope this helps.  Goodluck.

---

### Post by Tamale on 2008-06-13
you might be able to do an even easier fix.. you might have an extra, unneeded line in your fstab..

refer to this thread:
[http://ph.ubuntuforums.com/showthread.php?p=5179975#post5179975](http://ph.ubuntuforums.com/showthread.php?p=5179975#post5179975)

this is a serious problem.  it should be addressed appropriately!

---

### Post by ZootNerper on 2008-06-13
Hi Folks,

I've had the problem of a USB thumb drive becoming unmountable (no entry in Places and no pop up file manager on plug in. (I run Hardy) One day one drive worked next two didn't.

Anyway, I noticed of 3 computers (one running Gutsy that was the last in line for testing if the mount worked) that it maybe the thunmb drive itself. I re-formatted both thumb drives and "hey presto" without fiddling with anything else, both were mountable and readable.

This worked for me. I suppose, those you want to try this route should plug the drive into a (sorry) Windows machine to backup anything they want and then re-format (my drives were formatted in ext2 and ext3, so this dodge would not work for me)

Not a good solution, but a solution for me.

-- Zoot

---

### Post by fenix1224 on 2008-06-13
Just got usb devices to work on my computer and wanted to give you guys some info.

My computer is a compaq sr1650nx, which I use the noapic flag to boot up.

lspci shows I have:

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller

I went into my bios and set "Plug and Play O/S" to No, which lets the bios configure non-bootable devices. By setting this my computer now detects my usb devices, as opposed to none before.

---

### Post by MarkX on 2008-06-13
> **tenmoi said:**
> just did a reboot and the phone is recognised.

ANd I recently changed the resolution to 1152 x 864.

I can't be sure what fixed my problem but USB seemed to start  working again after I corrected from PCI to AGP vid card in BIOS. I don't know why it was set to PCI in the first place (vga worked fine) but maybe the USB problem has something to do with bus or IRQ assignments?

---

### Post by weemikey on 2008-06-14
Same stuff going on here. My printer and scanner are recognized but not functioning. Memory sticks mount with no problem, but my external cd/dvd burner seems to be in outer space as far as my computer is concerned.
Below are a few print-outs:

lsusb:
michael@michael-desktop:~$ lsusb
Bus 004 Device 002: ID 04b8:0119 Seiko Epson Corp. Perfection 4490 Photo
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 043d:0057 Lexmark International, Inc. Z35 Printer
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


lspci:
michael@michael-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]


id:
michael@michael-desktop:~$ id
uid=1000(michael) gid=1000(michael) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(michael)
michael@michael-desktop:~$ lsusb
Bus 004 Device 002: ID 04b8:0119 Seiko Epson Corp. Perfection 4490 Photo
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
michael@michael-desktop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
michael@michael-desktop:~$ ls -l /dev/bus/usb/004/002
crw-rw-r--+ 1 root scanner 189, 385 2008-06-07 08:44 /dev/bus/usb/004/002


hal restart: followed by lsusb:  followed by udevmonitor --environment
michael@michael-desktop:~$ sudo /etc/init.d/hal restart
[sudo] password for michael: 
 * Restarting Hardware abstraction layer hald                            [ OK ] 
michael@michael-desktop:~$ lsusb
Bus 004 Device 002: ID 04b8:0119 Seiko Epson Corp. Perfection 4490 Photo
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 043d:0057 Lexmark International, Inc. Z35 Printer
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
michael@michael-desktop:~$ sudo udevmonitor --environment
udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent


I have tried re-installing my Lexmark printer, have followed the guide for installing the drivers for the 4490 Scanner.
I AM NOT a computer whiz and therefore need to have my hand held through this (at the age of 70: not an excuse, but a basic reason).
When I ran Dapper previously to Hardy I had, with help, managed to get past of these problems and glitches: printer, scanner, external cd/dvd burner, webcam - all worked well.  What has Hardy done to me?:rolleyes:

---

### Post by billir on 2008-06-17
Well I took what I hoped to be the easy way out and it worked,
I when out an bought a USB card (Nec) and my USB stick now work. in that card
billir@ubun-br:~$ lsusb
Bus 009 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:0a01 Logitech, Inc. Logitech USB Headset
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 04f9:0181 Brother Industries, Ltd 
Bus 003 Device 001: ID 0000:0000  
**Bus 007 Device 002: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter**
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000

t@ubun-br:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
[B]03:07.0 USB Controller: NEC Corporation USB (rev 43)
03:07.1 USB Controller: NEC Corporation USB (rev 43)
03:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)[/B]
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Just posted this to show what an addition that works will do.

---

### Post by Presbuteros on 2008-06-26
Anyone feel like we are the blind leading the blind here?

Attempting to connect an "A-Data PD16" 16GB USB Stick Drive with no success. 

@linuxbox:~$ lsusb
Bus 004 Device 004: ID 067b:2528 Prolific Technology, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

@linuxbox:~$ lspci
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)

@linuxbox:~$ dmesg | tail
[  867.368000] scsi4 : SCSI emulation for USB Mass Storage devices
[  867.368000] usb-storage: device found at 4
[  867.368000] usb-storage: waiting for device to settle before scanning
[  872.368000] usb-storage: device scan complete
[  877.980000] usb 4-1: reset high speed USB device using ehci_hcd and address 4
[  888.224000] usb 4-1: reset high speed USB device using ehci_hcd and address 4
[  904.468000] usb 4-1: reset high speed USB device using ehci_hcd and address 4
[  904.716000] usb 4-1: reset high speed USB device using ehci_hcd and address 4
[  914.960000] usb 4-1: reset high speed USB device using ehci_hcd and address 4
[  915.092000] scsi 4:0:0:0: scsi: Device offlined - not ready after error recovery

@linuxbox:~$ fdisk
would copy all here but no need. only shows my internal drive with xp partition, linux partition, and swap partition. there is no other device recognized... period... hence, the problem... no command gives sd? sb? sc? or whatever to manually mount because it is NOT recognized...

again just providing some stats for what is not working...

---

### Post by alvinson on 2008-06-26
so good,good knowledge

Create online surveys with [www.surveylover.com](www.surveylover.com), a powerful online survey tool

---

### Post by Odrodzona-Sarmacja on 2008-06-27
I have a thought.
Is your BIOS set for plug&play OS? Does your BIOS support USB? If so, then fix it for non plug&play OS and let it reconfigure its hardware setup.
Is it of any help?

---

### Post by newsboy on 2008-06-27
I know this is know real help but I did a fresh install and all my USB devices are recognized and automounting.

Something must be getting trashed by doing a dist. upgrade.

---

### Post by Presbuteros on 2008-07-03
@ Mac - device is not recognized in Live CD so no good.

@ newsboy - Really?...  working from fresh install 8.04 fully upgraded and no go... but no thanks.

@linuxbox:~$ fdisk
would copy output here but no need. only shows my internal drive with xp partition, shared partition between xp/linux, linux partition, and swap partition. there is no other device recognized... period... hence, the problem... no command gives sd? sb? sc? or whatever to manually mount because it is NOT recognized...

---

### Post by newsboy on 2008-07-03
> **Presbuteros said:**
> 
@ newsboy - Really?...  working from fresh install 8.04 fully upgraded and no go... but no thanks.


Do you have a fresh install or an upgrade? I had problems with my USB devices after upgrading to 8.04 But upon installing a fresh copy all my USB devices started working.

---

### Post by billir on 2008-07-06
I was having the same problem USB device could be seen but not anything with a files system (see my previous posts).
My motherboard is a Gigabyte MA770DCS running a 4 core phemom processor and a SB600 Southbridge (controls the USB on the system)
I have sequentially flashed the bios 3, 4, 5, 6 using the bios updates from Gigabyte. My Kensington 1 gig USB stick was recognized by the latest kernel at update #4.
I suggest to all to make sure the bios on there machines is up to date.
It worked for me.

---

### Post by izmeh on 2008-07-08
I have a 3 day old install of hardy. My flash thumbdrive was working fine at first. Problem arose when I right clicked and dismounted it from the desktop. Now it won't pop up anymore when I plug it in. However it shows up as /dev/sdc with "fdisk -l".

---

### Post by marlon89br on 2008-07-08
I'm with the same problem here. My laptop is not automountig neither my external USB hard drive nor my pendrive. Both of them appear with "fdisk -l" and I can mount them manually (just read mode, I don't know the correct arguments for writing mode). This is a fresh install of Hardy and it was working properly until sunday...

---

### Post by reech on 2008-07-15
Same problem  - fdisk lists the valid partitions but they're not automatically mounted as expected(I can mount them manually - but that's a real pain for a nooob) CD's have also stopped automounting.

Anyone know what systems are responsible for automounting?

---

### Post by mac71 on 2008-08-01
Don't know if its of any help to anyone, all my troubles seemed to happen after a bios update from lenovo (via windoze- which i've now totally removed), i've just re-flashed my bios to a 2006 release from ibm/lenovo and everything now works perfectly.:)

---

