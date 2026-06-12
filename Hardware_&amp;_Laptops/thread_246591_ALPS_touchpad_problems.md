---
title: "ALPS touchpad problems"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by Hotaru on 2006-08-29
After recent update my ALPS touchpad has gone numb.
I have HP Pavilion dv4152ea and it used to work fine straight from the box when I installed Dapper (tapping, scrolling etc.) but after recent update (the one that kinda broke my compiz-vanilla as well :P) it't gone numb (for the lack of a better word).
The tapping isn't working, neither is scrolling and it started to move the pointer extremely slowly! I've reinstalled *xserver-xorg-input-synaptics* (version 0.14.4) but it didn't help one bit. Then I've found this how-to: [this how-to]("http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide/") on the net and have done what the author suggested. My pointer is moving faster now, but tapping and scrolling still don't work! :(
Any idea what am I doing wrong?

Contents of my xorg.conf:
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	# Load "GLcore"
	Load "bitmap"
	Load "ddc"
	Load "dbe"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "type1"
	Load "vbe"
	Load "synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver "synaptics"
	Identifier "touchpad"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "LeftEdge" "130&#8243;
	Option "RightEdge" "840&#8243;
	Option "TopEdge" "130&#8243;
	Option "BottomEdge" "640&#8243;
	Option "FingerLow" "7&#8243;
	Option "FingerHigh" "8&#8243;
	Option "MaxTapTime" "180&#8243;
	Option "MaxTapMove" "110&#8243;
	Option "EmulateMidButtonTime" "75&#8243;
	Option "VertScrollDelta" "20&#8243;
	Option "HorizScrollDelta" "20&#8243;
	Option "MinSpeed" "0.25&#8243;
	Option "MaxSpeed" "0.50&#8243;
	Option "AccelFactor" "0.030&#8243;
	Option "EdgeMotionMinSpeed" "200&#8243;
	Option "EdgeMotionMaxSpeed" "200&#8243;
	Option "UpDownScrolling" "1&#8243;
	Option "CircularScrolling" "1&#8243;
	Option "CircScrollDelta" "0.1&#8243;
	Option "CircScrollTrigger" "2&#8243;
	Option "SHMConfig" "on"

	#always usefull
	Option "Emulate3Buttons" "on"
EndSection


Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	Option		"XAANoOffscreenPixmaps"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Option 		"AIGLX" "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice 	"touchpad" "AlwaysCore"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option 		"Composite" "Enable"
EndSection
```

lsmod results:
```
Module                  Size  Used by
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppp_deflate             6272  0
zlib_deflate           24344  1 ppp_deflate
bsd_comp                6272  0
ipv6                  265728  8
pppoatm                 6400  1
ppp_generic            30100  7 ppp_deflate,bsd_comp,pppoatm
slhc                    7424  1 ppp_generic
ppdev                   9220  0
i915                   22528  2
drm                    82968  3 i915
speedstep_centrino      8400  1
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
af_packet              22920  2
dm_mod                 58936  1
fuse                   38412  4
sr_mod                 16932  0
sbp2                   24196  0
scsi_mod              139496  2 sr_mod,sbp2
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
pcmcia                 40508  0
8139cp                 22528  0
joydev                 10048  0
tsdev                   8000  0
ipw2200               107308  0
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  1 ieee80211
ieee80211_1_1_13       38216  0
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
sdhci                  14848  0
rtc                    13492  0
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
8139too                26880  0
mmc_core               30104  1 sdhci
mii                     5888  2 8139cp,8139too
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
psmouse                36100  0
serio_raw               7300  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
speedtch               12040  0
usbatm                 16128  2 speedtch
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  5 speedtch,usbatm,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  5
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  2 speedstep_centrino,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

Your help would be greatly appreciated :).

---

### Post by iluvdrbonner on 2006-08-29
Hey, 

I have an Alps Touchpad in a Toshiba Satellite M55 and I used to have a lot of stuff under the input. I reconfigured it and have my current setup listed below. You really shouldn't need if all the stuff for tap and scroll to work. Try these settings in there but make sure you backup the old ones first. Use Ctrl Alt Backspace to Restart X11.

Hope it helps.
Will


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option "VertScrollDelta" "10"
	Option "HorizScrollDelta" "10"
EndSection

---

### Post by Hotaru on 2006-08-30
> **iluvdrbonner said:**
> Hey, 

I have an Alps Touchpad in a Toshiba Satellite M55 and I used to have a lot of stuff under the input. I reconfigured it and have my current setup listed below. You really shouldn't need if all the stuff for tap and scroll to work. Try these settings in there but make sure you backup the old ones first. Use Ctrl Alt Backspace to Restart X11.

Hope it helps.
Will


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option "VertScrollDelta" "10"
	Option "HorizScrollDelta" "10"
EndSection

Thanks for your tip but it didn't work :(. When I've done as suggested and restarted x11 my touchpad went totally numb again, meaning no tapping, scrolling and extremely slow pointer. Restored the backup and at least the pointer acts normal - still no tapping or scrolling though. :(

---

### Post by iluvdrbonner on 2006-09-01
One thing to try would be to remove the "AlwaysCore"  from your xserver section and add the line 
Option		"SendCoreEvents"	"true"
 into the mouse input section.  Then restart X obviously. Also check /var/log/ for an Xorg logs and paste the newest one here so we can check it for any errors relating to the mouse. You can use  "ls -l /var/log/Xorg.*" to check to see which is newest. I really hope some of this helps, I am new at helping other people.... used to just debuging everything myself after I break Xgl and other stuff

---

### Post by Hotaru on 2006-09-01
It didn't work :(. The speed is fine, but still no scrolling or tapping. This is my xorg.conf:
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	# Load "GLcore"
	Load "bitmap"
	Load "ddc"
	Load "dbe"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "type1"
	Load "vbe"
	Load "synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver "synaptics"
	Identifier "touchpad"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "LeftEdge" "130&#8243;
	Option "RightEdge" "840&#8243;
	Option "TopEdge" "130&#8243;
	Option "BottomEdge" "640&#8243;
	Option "FingerLow" "7&#8243;
	Option "FingerHigh" "8&#8243;
	Option "MaxTapTime" "180&#8243;
	Option "MaxTapMove" "110&#8243;
	Option "EmulateMidButtonTime" "75&#8243;
	Option "VertScrollDelta" "20&#8243;
	Option "HorizScrollDelta" "20&#8243;
	Option "MinSpeed" "0.25&#8243;
	Option "MaxSpeed" "0.50&#8243;
	Option "AccelFactor" "0.030&#8243;
	Option "EdgeMotionMinSpeed" "200&#8243;
	Option "EdgeMotionMaxSpeed" "200&#8243;
	Option "UpDownScrolling" "1&#8243;
	Option "CircularScrolling" "1&#8243;
	Option "CircScrollDelta" "0.1&#8243;
	Option "CircScrollTrigger" "2&#8243;
	Option "SHMConfig" "on"

	#always usefull
	Option "Emulate3Buttons" "on"
EndSection


Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	Option		"XAANoOffscreenPixmaps"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Option 		"AIGLX" "true"
	Option		"SendCoreEvents"	"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice 	"touchpad" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option 		"Composite" "Enable"
EndSection

```

And this is a part of my Xorg.0.log. I Deleted everything related to my graphics' card display modes *(DELETED):*
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15-26-686 i686 
Current Operating System: Linux cerebra 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  1 18:19:09 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg-air/modules/"
(**) Option "AIGLX" "true"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg-air/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg-air/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
*DELETED*
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,10), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xb0100000 - 0xb01fffff (0x100000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:6:0), (6,7,10), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[1] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(--) PCI:*(0:2:0) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 4, Mem @ 0xb0080000/19, 0xc0000000/28, 0xb0000000/18, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 4, Mem @ 0x52000000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xb0109400 - 0xb01094ff (0x100) MX[B]
	[1] -1	0	0xb0108800 - 0xb01088ff (0x100) MX[B]
	[2] -1	0	0xb0108c00 - 0xb0108cff (0x100) MX[B]
	[3] -1	0	0xb0109000 - 0xb01090ff (0x100) MX[B]
	[4] -1	0	0xb0104000 - 0xb0105fff (0x2000) MX[B]
	[5] -1	0	0xb0100000 - 0xb0103fff (0x4000) MX[B]
	[6] -1	0	0xb0108000 - 0xb01087ff (0x800) MX[B]
	[7] -1	0	0xb0106000 - 0xb0106fff (0x1000) MX[B]
	[8] -1	0	0xb0040400 - 0xb00404ff (0x100) MX[B]
	[9] -1	0	0xb0040800 - 0xb00409ff (0x200) MX[B]
	[10] -1	0	0xb0040000 - 0xb00403ff (0x400) MX[B]
	[11] -1	0	0xb0000000 - 0xb003ffff (0x40000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xb0080000 - 0xb00fffff (0x80000) MX[B](B)
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[16] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[17] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[20] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[21] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x52000000 - 0x5207ffff (0x80000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb0109400 - 0xb01094ff (0x100) MX[B]
	[1] -1	0	0xb0108800 - 0xb01088ff (0x100) MX[B]
	[2] -1	0	0xb0108c00 - 0xb0108cff (0x100) MX[B]
	[3] -1	0	0xb0109000 - 0xb01090ff (0x100) MX[B]
	[4] -1	0	0xb0104000 - 0xb0105fff (0x2000) MX[B]
	[5] -1	0	0xb0100000 - 0xb0103fff (0x4000) MX[B]
	[6] -1	0	0xb0108000 - 0xb01087ff (0x800) MX[B]
	[7] -1	0	0xb0106000 - 0xb0106fff (0x1000) MX[B]
	[8] -1	0	0xb0040400 - 0xb00404ff (0x100) MX[B]
	[9] -1	0	0xb0040800 - 0xb00409ff (0x200) MX[B]
	[10] -1	0	0xb0040000 - 0xb00403ff (0x400) MX[B]
	[11] -1	0	0xb0000000 - 0xb003ffff (0x40000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xb0080000 - 0xb00fffff (0x80000) MX[B](B)
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[16] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[17] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[20] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[21] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x52000000 - 0x5207ffff (0x80000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0109400 - 0xb01094ff (0x100) MX[B]
	[5] -1	0	0xb0108800 - 0xb01088ff (0x100) MX[B]
	[6] -1	0	0xb0108c00 - 0xb0108cff (0x100) MX[B]
	[7] -1	0	0xb0109000 - 0xb01090ff (0x100) MX[B]
	[8] -1	0	0xb0104000 - 0xb0105fff (0x2000) MX[B]
	[9] -1	0	0xb0100000 - 0xb0103fff (0x4000) MX[B]
	[10] -1	0	0xb0108000 - 0xb01087ff (0x800) MX[B]
	[11] -1	0	0xb0106000 - 0xb0106fff (0x1000) MX[B]
	[12] -1	0	0xb0040400 - 0xb00404ff (0x100) MX[B]
	[13] -1	0	0xb0040800 - 0xb00409ff (0x200) MX[B]
	[14] -1	0	0xb0040000 - 0xb00403ff (0x400) MX[B]
	[15] -1	0	0xb0000000 - 0xb003ffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xb0080000 - 0xb00fffff (0x80000) MX[B](B)
	[18] -1	0	0x52000000 - 0x5207ffff (0x80000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[22] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[23] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[24] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[25] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[26] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[27] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[28] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg-air/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg-air/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg-air/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg-air/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg-air/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg-air/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg-air/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg-air/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg-air/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg-air/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg-air/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg-air/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg-air/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.6.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg-air/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg-air/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg-air/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Reloading /usr/lib/xorg-air/modules/input/synaptics_drv.so
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 915GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	*DELETED*
(II) resource ranges after probing:
	*DELETED*
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg-air/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg-air/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg-air/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg-air/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) I810(0): Chipset: "915GM"
(--) I810(0): Linear framebuffer at 0xC0000000
(--) I810(0): IO registers at addr 0xB0080000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 7932 kB stolen memory.
(II) I810(0): Kernel reported 238592 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 954364 kB available
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg-air/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 1222
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
*DELETED*
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.4 (1404)
(--) touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "SHMConfig" "on"
(WW) Option "LeftEdge" requires an integer value
(WW) Option "RightEdge" requires an integer value
(WW) Option "TopEdge" requires an integer value
(WW) Option "BottomEdge" requires an integer value
(WW) Option "FingerLow" requires an integer value
(WW) Option "FingerHigh" requires an integer value
(WW) Option "MaxTapTime" requires an integer value
(WW) Option "MaxTapMove" requires an integer value
(WW) Option "EmulateMidButtonTime" requires an integer value
(WW) Option "VertScrollDelta" requires an integer value
(WW) Option "HorizScrollDelta" requires an integer value
(WW) Option "EdgeMotionMinSpeed" requires an integer value
(WW) Option "EdgeMotionMaxSpeed" requires an integer value
(WW) Option "UpDownScrolling" requires a boolean value
(WW) Option "CircularScrolling" requires a boolean value
(WW) Option "CircScrollTrigger" requires an integer value
(--) touchpad touchpad found
(**) Option "SendCoreEvents"
(**) touchpad: always reports core events
(II) XINPUT: Adding extended input device "touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+gb" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/misc/, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1/, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
AUDIT: Fri Sep  1 18:19:11 2006: 6095 Xorg-air: client 2 rejected from local host
ProcXCloseDevice to close or not ?

```

If only I knew what it means... Don't like these *Could not init...* messages! :(

---

### Post by ianmillington on 2006-09-01
I use kubuntu dapper. For a couple of years I had problems with the touchpad in both Mandriva and, when I changed, in Kubuntu. The thing used to just go crazy without warning.

I installed synaptics and also ksynaptics which provided me with a GUI from where I could configure the touchpad. That solved everything. There are options for both scrolling and tapping, which I suspect will help solve the issues here. Don't know whether gnome users will be able to make full use though, or whether there is a gnome alternative.

Ian

---

### Post by Hotaru on 2006-09-02
Hmm... I have installed ksynaptics from Synaptic Package Manager and... silly me, I don't know how to run it! :P Couldn't find it in Applications Menu, in System Preferences and nothing happens when I type *gksudo ksynaptics* in the terminal. However, my touchpad isn't responding to any of the setting I change in Gnome Mouse Preferences Utility. Frankly, I don't think it ever did, even when it was working fine. Is that normal?

---

### Post by iluvdrbonner on 2006-09-05
Try this Tutorial its really for Alps Touchpads instead of synaptics setups. Try it out and let us know how it goes. I think part of the problem maybe with where you are recieving mouse input from. 

[http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/](http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/)

---

### Post by Hotaru on 2006-09-06
> **iluvdrbonner said:**
> Try this Tutorial its really for Alps Touchpads instead of synaptics setups. Try it out and let us know how it goes. I think part of the problem maybe with where you are recieving mouse input from. 

[http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/](http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/)

THANK YOU SO MUCH!
It's worked! I've done exactly what the How-To suggested and have my touchpad back! Appreciate you help guys! Was slowly getting accustomed with a though of reinstalling whole system. :)

---

