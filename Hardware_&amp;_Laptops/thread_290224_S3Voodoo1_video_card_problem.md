---
title: "S3/Voodoo1 video card problem"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by bishop71 on 2006-10-31
Some help needed, please!

I can run X only with "vesa" driver @60Hz and my eyes are bleeding!

This rather old computer (Compaq DeskPro, 233 Mhz) has also eaten Windows98se and 3Dfx Voodoo1 card so I can play very old games;) S3 Trio64V2-DX/GX is connected to Voodoo and from voodoo signal goes to monitor. S3 has 2 MB of graphics memory. S3 and Voodoo are connected to PCI slots. Voodoo can't work alone, it needs S3. Windows works fine @85Hz,  1024*768 and 16 bit colors.

So this won't work:
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Device"
	Identifier	"S3 Trio64V2-GX"
	Driver		"s3"
	BusID		"PCI:0:4:0"
	VideoRam	2048
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"PanaSync TX-D1753-G"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Trio64V2-GX"
	Monitor		"PanaSync TX-D1753-G"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768@85" "800x600@85" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768@85" "800x600@85" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768@85" "800x600@85" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768@85" "800x600@85" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768@85" "800x600@85" "640x480@85"
	EndSubSection

EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

... but if I change driver to vesa it works:

Section "Device"
	Identifier	"S3 Trio64V2-GX"
	Driver		"vesa"
	BusID		"PCI:0:4:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-86
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Trio64V2-GX"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "720x400" "640x480"
	EndSubSection
EndSection

lspci gives this information:

PCI:0:0:0 Host bridge: VIA Technologies, Inc. VT82C595/97 [Apollo VP2/97]
PCI:0:2:0 Ethernet controller: Advanced Micro Devices [AMD] 79c978 [HomePNA]
PCI:0:3:0 Multimedia video controller: 3Dfx Interactive, Inc. Voodoo
PCI:0:4:0 VGA compatible controller: S3 Inc. 86c775/86c785 [Trio 64V2/DX or /GX]
PCI:0:7:0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP]
PCI:0:7:1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
PCI:0:7:2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
PCI:0:7:3 Non-VGA unclassified device: VIA Technologies, Inc. VT82C586B ACPI
PCI:0:15:0 VGA compatible controller: S3 Inc. 86c775/86c785 [Trio 64V2/DX or /GX]

...strange, two  times S3: at PCI:0:4:0 and PCI:0:15:0??


in /var/log/kdm.log I found these two chapters:

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ilzu-desktop 2.6.15-26-386 #1 PREEMPT Thu Aug
3 02:52:00 UTC 2006 i586
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  1 01:55:39 2006
(==) Using config file: "/etc/X11/xorg.conf"
(WW) s3: No matching Device section for instance (BusID PCI:0:4:0) found
(WW) ****INVALID MEM ALLOCATION**** b: 0x10000000 e: 0x13ffffff correcting^G
(EE) s3(0): Cannot read V_BIOS
(EE) s3(0): Cannot read V_BIOS
(EE) s3(0): no valid modes found
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found



X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ilzu-desktop 2.6.15-26-386 #1 PREEMPT Thu Aug
3 02:52:00 UTC 2006 i586
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  1 02:46:19 2006
(==) Using config file: "/etc/X11/xorg.conf"
(WW) Voodoo: No matching Device section for instance (BusID PCI:0:3:0) found
(EE) No devices detected.

Fatal server error:
no screens found

I am powerless, can you help me or should I buy a Ferrari??

--*bishop71*

---

### Post by zgornel on 2006-11-01
Are there any kernel modules loaded for the S3 ? Put a *lsmod* output...

---

### Post by bishop71 on 2006-11-02
Ok. Here it comes! Hmm. No mention of s3 :confused: 
Btw: I had to type in "sudo modprobe snd-sbawe" to make sounds work. I don't even know how to make it permanent in this system. Maybe I should type it into some file?

--

Module                 Size  Used by
snd_sbawe              29504  0
snd_opl3_lib           10624  1 snd_sbawe
snd_sb16_dsp           11520  1 snd_sbawe
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  2 snd_sb16_dsp,snd_pcm_oss
snd_timer              25220  2 snd_opl3_lib,snd_pcm
snd_page_alloc         10632  1 snd_pcm
snd_sb16_csp           19968  1 snd_sbawe
snd_sb_common          15616  3 snd_sbawe,snd_sb16_dsp,snd_sb16_csp
snd_hwdep               9376  2 snd_opl3_lib,snd_sb16_csp
snd_mpu401_uart         7808  1 snd_sbawe
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  3 snd_sbawe,snd_opl3_lib,snd_rawmidi
snd                    55268  13 snd_sbawe,snd_opl3_lib,snd_sb16_dsp,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_sb16_csp,snd_sb_common,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
xfs                   589656  0
exportfs                6272  1 xfs
reiserfs              268016  0
jfs                   195780  0
ext3                  135688  0
jbd                    58772  1 ext3
ntfs                  103536  0
vfat                   13440  0
fat                    53020  1 vfat
ext2                   68360  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
apm                    21228  1
ppdev                   9220  0
lp                     11844  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
dm_mod                 58936  1
md_mod                 72532  0
tsdev                   8000  0
analog                 12320  0
ns558                   5636  0
gameport               15496  3 analog,ns558
rtc                    13492  0
pcspkr                  2180  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
i2c_via                 4484  0
i2c_algo_bit            9608  1 i2c_via
psmouse                36100  0
floppy                 62148  0
i2c_core               21904  1 i2c_algo_bit
serio_raw               7300  0
ipv6                  265728  6
af_packet              22920  2
evdev                   9856  1
pcnet32                30084  0
mii                     5888  1 pcnet32
squashfs               44980  1
unionfs                89884  1
loop                   17288  2
nls_cp437               5888  1
isofs                  37688  1
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  2 uhci_hcd
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  3
via82cxxx               9988  0 [permanent]
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit


--bishop71

---

### Post by zgornel on 2006-11-02
Hmmm. For the snd_sbawe /etc/modules.conf has to be modified. Try reading the ALSA Project documentation for your soundcard. For the S3, I don't remember what support was in the kernel or what driver Xorg uses. Try searching for modifications to be done in /etc/X11/xorg.conf for S3 cards. :(

---

