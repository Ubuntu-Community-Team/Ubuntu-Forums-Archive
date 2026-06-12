---
title: "Fglrx driver doesn't work (Radeon X1650 AGP)"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by Karri on 2008-02-08
Hi.

I bought an ATI Radeon X1650 Sapphire AGP.
I use Ubuntu Gutsy.
I go to Add/Remove, install the Ubuntu supported fglrx driver.
I boot.
After splash screen, I get only a black screen.

I've re-installed the fglrx driver countless times, tried newer drivers from ATI, and it always ends the same.

What do I do?

I'm currently using the vesa driver, so that I can at least access the graphical system.

```

karri@karri-desktop:~$ cat /var/log/Xorg.0.log.old | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX: Screen 0 is not DRI capable

karri@karri-desktop:~$ cat /var/log/Xorg.0.log.old | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

karri@karri-desktop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

karri@karri-desktop:~$ lsmod | grep agp
via_agp                11264  1 
agpgart                35016  1 via_agp

karri@karri-desktop:~$ lsmod
Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
af_packet              24840  2 
binfmt_misc            12936  1 
ipv6                  273892  14 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
sg                     36764  0 
sd_mod                 30336  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
button                  8976  0 
video                  18060  0 
container               5504  0 
dock                   10656  0 
sbs                    19592  0 
ac                      6148  0 
battery                11012  0 
sbp2                   24072  0 
lp                     12580  0 
usb_storage            73024  0 
joydev                 11328  0 
snd_via82xx            29336  0 
gameport               16776  1 snd_via82xx
snd_mpu401_uart         9600  1 snd_via82xx
libusual               18448  1 usb_storage
xpad                    9988  0 
parport_pc             37412  1 
snd_ca0106             34720  2 
usbhid                 29536  0 
hid                    28928  1 usbhid
snd_via82xx_modem      16264  0 
snd_ac97_codec        100644  3 snd_via82xx,snd_ca0106,snd_via82xx_modem
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
parport                37448  3 ppdev,lp,parport_pc
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
psmouse                39952  0 
serio_raw               8068  0 
pcspkr                  4224  0 
i2c_viapro             10004  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25728  3 snd_mpu401_uart,snd_ca0106,snd_seq_midi
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
i2c_core               26112  1 i2c_viapro
snd_pcm                80388  6 snd_via82xx,snd_ca0106,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
shpchp                 34580  0 
snd_timer              24324  3 snd_seq,snd_pcm
snd                    54660  15 snd_via82xx,snd_mpu401_uart,snd_ca0106,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_seq,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore               8800  1 snd
ac97_bus                3200  1 snd_ac97_codec
snd_page_alloc         11400  4 snd_via82xx,snd_ca0106,snd_via82xx_modem,snd_pcm
pci_hotplug            32704  1 shpchp
via_agp                11264  1 
agpgart                35016  1 via_agp
evdev                  11136  4 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ide_disk               18560  7 
ata_generic             8452  0 
ehci_hcd               36492  0 
via_rhine              25992  0 
mii                     6528  1 via_rhine
uhci_hcd               26640  0 
usbcore               138632  7 usb_storage,libusual,xpad,usbhid,ehci_hcd,uhci_hcd
via82cxxx              10372  0 [permanent]
ide_core              116804  4 usb_storage,ide_cd,ide_disk,via82cxxx
sata_via               12548  0 
libata                125168  2 ata_generic,sata_via
scsi_mod              147084  5 sg,sd_mod,sbp2,usb_storage,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor


```

```

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"RV535"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Nokia Valuegraph 447W"
	Option		"DPMS"
	HorizSync	31-85
	VertRefresh	48-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"RV535"
	Monitor		"Nokia Valuegraph 447W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

---

### Post by Karri on 2008-02-09
Anyone?

I'd love to use Ubuntu and Linux but this is definitely the show stopper (for now anyway) if I can't get it working.

I hate Windows but I've done everything I can possibly think of and I just got to get my work done.

:(

---

### Post by olujicz on 2008-02-09
Try envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Yellow Pasque on 2008-02-09
For the Ubuntu driver, try:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv
```

For the latest ATI driver: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by Karri on 2008-02-09
> **olujicz said:**
> Try envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Results in black screen.

> For the Ubuntu driver, try:
Code:

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv

For the latest ATI driver: [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)


Results in black screen.

:(

---

### Post by eyespeculum on 2008-02-09
I'm having the  same issue, only with a PCIe version of the same card. I have tried the above remedies with the same result.  Just a black screen.  Any help would be really appreciated.

---

### Post by Yellow Pasque on 2008-02-09
Try the open-source radeonhd driver with a link in my sig to build from latest sources

---

### Post by Karri on 2008-02-10
Thanks a lot!! That actually works!
Well, 3D doesn't work of course but it doesn't matter now, I'm happy that I can use the desktop normally. Hopefully there will be better driver support soon.

Thanks again. I was going nuts with running vesa.

---

