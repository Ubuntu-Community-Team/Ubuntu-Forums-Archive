---
title: "Compaq Presario CQ50-130US status report"
date: 2008-09-27
forum: Hardware
---

### Post by kihjin on 2008-09-27
Hi everyone. I bought myself a new laptop from newegg, I thought I'd post my experiences so other people can benefit.

The laptop comes with Vista Home Premium. No recovery disks, you need to make your own. 

I have installed xubuntu 8.04.1. Here's a synopsis of what I've discovered

Installation: no hiccups
Reboot after install: smooth, display comes up
display (intel gma 4500MHD) : full resolution 1280x800
wireless ethernet: nonfunctional
wireless ethernet toggle button: stuck in off mode
wired ethernet: functional
touchpad: functional
touchpad toggle button: nonfunctional
keyboard: functional
audio: functional (good sound)
media card reader: i've only tested it with an xD (olympus) card, and it works great

Minor annoyance, the pc speaker beeps at logon. I added pcspkr /etc/modprobe.d/blacklist

I got wifi working by downloading a new madwifi snapshot. The toggle button is still nonfunctional. [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

The last remaining issue deals with video output. Out of the box, if you try to play a video in totem, it will crash the system. I don't like totem to begin with, so I removed it and installed mplayer. mplayer still crashed the system.

It didn't take me long to determine that the problem was the video output. By default it is set to xv. Switching it to x11 allows me to play video and sound works fine set to alsa.

Here's the good stuff

lspci
```

kyle@laptop:~$ sudo lspci -vnn
[sudo] password for kyle: 
00:00.0 Host bridge [0600]: Intel Corporation Cantiga Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller [0300]: Intel Corporation Cantiga Integrated Graphics Controller [8086:2a42] (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller [0380]: Intel Corporation Cantiga Integrated Graphics Controller [8086:2a43] (rev 07)
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, fast devsel, latency 0
	Memory at 92500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 50e0 [size=32]
	Capabilities: [50] #13 [0306]

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 50c0 [size=32]
	Capabilities: [50] #13 [0306]

00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 50a0 [size=32]
	Capabilities: [50] #13 [0306]

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at 94705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] #13 [0306]

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 94700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: 93700000-946fffff
	Prefetchable memory behind bridge: 0000000090400000-00000000914fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 92600000-936fffff
	Prefetchable memory behind bridge: 0000000091500000-00000000924fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5080 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5060 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 5040 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at 94705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] #13 [0306]

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: [50] Subsystem: Hewlett-Packard Company Unknown device [103c:360b]

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 220
	I/O ports at 5108 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 5100 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at 94705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]
	Capabilities: [b0] #13 [0306]

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: medium devsel, IRQ 11
	Memory at 94706000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]

00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: fast devsel, IRQ 11
	Memory at 94704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device [103c:360b]
	Flags: bus master, fast devsel, latency 0, IRQ 221
	I/O ports at 3000 [size=256]
	Memory at 90410000 (64-bit, prefetchable) [size=4K]
	Memory at 90400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 90420000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint IRQ 1
	Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [cc] Vital Product Data

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device [103c:137a]
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at 92600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint IRQ 0
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

```

lsmod
```

kyle@laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  0 
nls_cp437               6656  0 
vfat                   14464  0 
fat                    54556  1 vfat
wlan_tkip              13824  1 
wlan_ccmp               9728  1 
af_packet              23812  4 
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0 
joydev                 13120  0 
snd_hda_intel         344728  1 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
wlan_scan_sta          16000  1 
ath_rate_sample        16128  1 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
ath_pci               249016  0 
wlan                  236272  6 wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
battery                14212  0 
ac                      6916  0 
ath_hal               305376  3 ath_rate_sample,ath_pci
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
wmi_acer                9644  0 
video                  19856  0 
output                  4736  1 video
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                40336  0 
button                  9232  0 
intel_agp_ich9m        23700  1 
soundcore               8800  1 snd
serio_raw               7940  0 
evdev                  13056  6 
agpgart                34760  3 drm,intel_agp_ich9m
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
xfs                   571416  2 
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
usb_storage            73664  0 
libusual               19108  1 usb_storage
ahci                   28420  3 
libata                159344  1 ahci
scsi_mod              151436  5 sg,sr_mod,sd_mod,usb_storage,libata
r8169                  32900  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 usb_storage,libusual,ehci_hcd,uhci_hcd
dm_mirror              24832  0 
dm_snapshot            19620  0 
dm_mod                 62660  5 dm_mirror,dm_snapshot
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 

```

xorg.conf
```

kyle@laptop:~$ cat /etc/X11/xorg.conf 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

Some specs
```

kyle@laptop:~$ free -b
             total       used       free     shared    buffers     cached
Mem:    2054377472  658870272 1395507200          0     835584  384335872
-/+ buffers/cache:  273698816 1780678656
Swap:   1003442176          0 1003442176
kyle@laptop:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3994.49
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3989.98
clflush size	: 64
kyle@laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```

glxgears doesn't come by default, you need to install mesa utilities
```

4561 frames in 5.0 seconds = 912.122 FPS
4803 frames in 5.0 seconds = 960.487 FPS
3814 frames in 5.0 seconds = 762.672 FPS
660 frames in 5.0 seconds = 131.955 FPS
659 frames in 5.0 seconds = 131.798 FPS
660 frames in 5.0 seconds = 131.852 FPS

```


***UPDATE*** 

I was able to enable video scaling in Mplayer by selecting the video output driver **gl**. 

For those wondering, I was able to setup and play enemy territory. I only had some difficulty with the sound, but that was easily fixed. The solution is described [https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory) in the Troubleshooting section.

---

### Post by itkeepsrepeating on 2009-04-13
I know this post is dated, but I have an HP G50-109NR, it is very similar to your laptop. I had similar problems as yours, and gave it a rest for a bit, but have gone back and tried Jaunty beta. Wifi is fixed [the intrepid fix was to install a backports module], the button stays red, but functions. 

I am now looking to get the touchpad button working. It has the opposite problem from the wifi button. Hitting the touchpad button changes the light, but does not do anything, the touchpad remains active. I can disable the touchpad in preferences>mouse>touchpad tab, but I want the button to work. 

If someone could step in and throw a few commands my way, It'd be greatly appreciated.

---

