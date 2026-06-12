---
title: "Problems with HP Pavilion tx2690eo tablet"
date: 2008-12-20
forum: Hardware
---

### Post by RaZoR1394 on 2008-12-20
I have gotten most things working except two major things (for me) and some smaller ones.

* Wacom
* Touchscreen

Wacom

The kernel module is autoloaded and the device is recognized with lsusb. However even though I've followed all four ways of installing wacom-tools and the Xorg driver (compiling, prebuilt, from ubuntu repository and debs from Ubuntu Wiki) it won't work. Using cat and wacdump on all event* and ttyS* does not result in any progress. /dev/input/wacom does not even exist and I don't know of any device file that is connected with the digitizer. wacomcpl is totally empty.

```

razor1394@scorpia:~$ ls /dev/ttyS*
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3

```

```

razor1394@scorpia:~$ ls /dev/input/event*
/dev/input/event0   /dev/input/event11  /dev/input/event4  /dev/input/event7
/dev/input/event1   /dev/input/event2   /dev/input/event5  /dev/input/event8
/dev/input/event10  /dev/input/event3   /dev/input/event6  /dev/input/event9

```

Touchscreen

I downloaded the latest beta and it installs and seems to configure fine but after reboot and starting TouchKit the icon is covered by a red cross and no touchscreen is detected. I have tried RS232, PS/2, USB and none work.

And something about the Mobility 3200 HD drivers...

radeon - Works with correct resolution on the desktop but when I'm at GDM the resolution is very low. Rotate works but results in static and corruption.
radeonhd - Correct resolution but everything is very small.
fglrx - Always correct resolution but the computer locks up when logging out.

Temp sensors are also not working. The only one I see says 65C and I think it refers to the motherboard. I can't find any temp info in BIOS either.

I have flashed the latest bios.

So any help please?

---

### Post by Favux on 2008-12-21
Hi RaZoR1394,

Most likely your problem is not having a correctly configured xorg.conf (found in /etc/X11/).  Attached find a correctly configured xorg.conf for a TX2500.  If you have questions about implementing this just ask.  Be sure to back yours up before messing around with it.

You have a USB tablet, the tty stuff is for serial tablets.  What linuxwacom driver version do you currently have installed?

You do not need separate touch screen drivers, linuxwacom will handle it.  The main problem with using  "fglrx" is that it will not let you rotate into tablet mode.  See:

   [http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

Hope this helps some.

---

### Post by RaZoR1394 on 2008-12-21
Thanks for the reply. I almost thought there was no hope left in getting an answer.

I tried your xorg.conf but I changed all three wacom device names to this:

pci-0000:00:13.2-usb-0:2:1.0-event-

Here's what's under the by-path dir.

```

razor1394@scorpia:~$ ls /dev/input/by-path/
pci-0000:00:13.2-usb-0:2:1.0-event-  platform-i8042-serio-1-event-mouse
platform-i8042-serio-0-event-kbd     platform-i8042-serio-1-mouse

```

I have tried using "sudo cat" and sudo wacdump on all these devices and at the same time using the wacom pen with no results.

I'm using 0.8.2 prebuilt Xorg drivers and tools and I have tried the 0.8.1-6 from the Ubuntu Wiki and the ones from the Intrepid repository.

I recently tried grabbing the latest source from cvs and compile it but it did not work.

pci-0000:00:14.5-usb-0:2:1.0-event-mouse

and

pci-0000:00:14.5-usb-0:2:1.1-event-

does not exist.

```

razor1394@scorpia:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
08:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

```

razor1394@scorpia:~$ lsusb
Bus 007 Device 002: ID 064e:a104 Suyin Corp. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 056a:0093 Wacom Co., Ltd 
Bus 006 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

edit:

stroage ? It seems Realtek made a nasty typo there and I have no idea what this is. Card reader?

---

### Post by Favux on 2008-12-21
Hi RaZoR1394,

It is not clear to me why you changed the inputs in xorg.conf.  Your Wacom identifies the same as mine in lsusb:
```
Bus 002 Device 006: ID 056a:0093 Wacom Co., Ltd 
Bus 002 Device 005: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 004: ID 064e:a110 Suyin Corp. 
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
I have a TX2110us.  I see that your usb identifier for input under ls /dev/input/by-path/ looks different from the included TX2500 xorg.conf, I just don't know why.  Do you know of a change in the Wacom tablet between earlier TX2500's and yours?  I thought only the new TX2z had the multi-touch screen.

I have compiled the latest 0.8.2 using the following tutorial:
   [http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")
by gali98, substituting 0.8.2 for 0.8.1-6  .

Since you have no stylus or touch activity, or tools under wacomcpl do we even know if the wacom module is loading?  Try:
```
dmesg | grep Wacom

or

reset

dmesg | grep Wacom
```
or failing that reboot and then "dmesg | grep Wacom".  Let's see if the module is there and what usb paths are there.  Or if that doesn't work try:
```
lsmod

and

modinfo -d wacom
```

---

### Post by RaZoR1394 on 2008-12-21
I'm not sure if the screen part has changed. It shouldn't. It says tx2500 in the bios configuration.

```

razor1394@scorpia:~$ dmesg | grep wacom
[  261.738861] usbcore: registered new interface driver wacom
[  261.741746] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
razor1394@scorpia:~$ dmesg | grep Wacom
[  261.741746] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

```

```

razor1394@scorpia:~$ lsmod
Module                  Size  Used by
wacom                  27264  0 
michael_mic            10496  4 
arc4                    9984  4 
ecb                    10880  4 
crypto_blkcipher       25476  1 ecb
af_packet              25728  4 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
rfcomm                 44432  2 
l2cap                  30464  16 bnep,rfcomm
ppdev                  15620  0 
ipv6                  263972  16 
powernow_k8            22148  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  2 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
psmouse                45200  0 
serio_raw              13444  0 
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
i2c_piix4              16144  0 
i2c_core               31892  1 i2c_piix4
btusb                  19736  3 
joydev                 18368  0 
evdev                  17696  17 
bluetooth              61924  11 bnep,sco,rfcomm,l2cap,btusb
ieee80211_crypt_tkip    17024  0 
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
ac                     12292  0 
button                 14224  0 
battery                18436  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
usb_storage            81728  0 
pata_acpi              12160  0 
libusual               27156  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
pata_atiixp            12800  0 
sg                     39732  0 
ehci_hcd               43276  0 
ohci_hcd               31888  0 
ata_generic            12932  0 
ahci                   37132  2 
r8169                  35972  0 
usbcore               148848  9 wacom,uvcvideo,btusb,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
libata                177312  4 pata_acpi,pata_atiixp,ata_generic,ahci
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

```

Experimenting some more with Xorg... I've added the "mouse" part (even though those devices don't exist).

```

razor1394@scorpia:~$ cat /etc/X11/xorg.conf
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

#Section "InputDevice"
#	Identifier	"Synaptics Pad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Type" "stylus"
Option "USB" "on"
#Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
Option "Device" "/dev/input/by-path/pci-0000:00:13.2-usb-0:2:1.0-event-mouse"
Option "Button2" "3" # make side-switch a right button
Option "TopX" "225"
Option "TopY" "225"
Option "BottomX" "26300"
Option "BottomY" "16375"
EndSection

Section "InputDevice"
Identifier "touch"
Driver "wacom"
Option "Type" "touch"
Option "USB" "on"
#Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
Option "Device" "/dev/input/by-path/pci-0000:00:13.2-usb-0:2:1.0-event-"
Option "TopX" "200"
Option "TopY" "225"
Option "BottomX" "4000"
Option "BottomY" "3875"
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Type" "eraser"
#Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
Option "Device" "/dev/input/by-path/pci-0000:00:13.2-usb-0:2:1.0-event-mouse"
Option "USB" "on"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen 		"Default Screen"
#	Inputdevice	"Synaptics Pad"
	Inputdevice "stylus"	"SendCoreEvents"
	Inputdevice "touch"	"SendCoreEvents"
	Inputdevice "eraser"	"SendCoreEvents"
EndSection

#Section "Module"
#	Load	"glx"
#EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"radeon"
EndSection

```

```

razor1394@scorpia:~$ modinfo wacom
filename:       /lib/modules/2.6.27-9-generic/kernel/drivers/input/tablet/wacom.ko
license:        GPL
description:    USB Wacom Graphire and Wacom Intuos tablet driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
license:        GPL
description:    USB Wacom Graphire and Wacom Intuos tablet driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
srcversion:     7D31C6DE2D31EFEC6D14C25
alias:          usb:v056Ap0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C5d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B7d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B5d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B0d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0045d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0044d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0043d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C0d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0038d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0037d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0035d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0034d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0069d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0064d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0063d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0062d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0061d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0016d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0014d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0000d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586

```

```

razor1394@scorpia:~$ modinfo -d wacom
USB Wacom Graphire and Wacom Intuos tablet driver
USB Wacom Graphire and Wacom Intuos tablet driver

```

---

### Post by RaZoR1394 on 2008-12-21
Now It's different?

```

razor1394@scorpia:~$ ls /dev/input/by-path/
pci-0000:00:12.2-usb-0:3.5.1:1.0-event-kbd    pci-0000:00:12.2-usb-0:3.5.1:1.1-mouse  platform-i8042-serio-0-event-kbd    platform-i8042-serio-1-mouse
pci-0000:00:12.2-usb-0:3.5.1:1.1-event-mouse  pci-0000:00:13.2-usb-0:2:1.0-event-     platform-i8042-serio-1-event-mouse

```

Using a new config but no joy:

```

razor1394@scorpia:~$ cat /etc/X11/xorg.conf
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

#Section "InputDevice"
#	Identifier	"Synaptics Pad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Type" "stylus"
Option "USB" "on"
#Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
Option "Device" "/dev/input/by-path/pci-0000:00:12.2-usb-0:3.5.1:1.1-event-mouse"
Option "Button2" "3" # make side-switch a right button
Option "TopX" "225"
Option "TopY" "225"
Option "BottomX" "26300"
Option "BottomY" "16375"
EndSection

Section "InputDevice"
Identifier "touch"
Driver "wacom"
Option "Type" "touch"
Option "USB" "on"
#Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
Option "Device" "/dev/input/by-path/pci-0000:00:13.2-usb-0:2:1.0-event-"
Option "TopX" "200"
Option "TopY" "225"
Option "BottomX" "4000"
Option "BottomY" "3875"
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Type" "eraser"
#Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
Option "Device" "/dev/input/by-path/pci-0000:00:12.2-usb-0:3.5.1:1.1-event-mouse"
Option "USB" "on"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen 		"Default Screen"
#	Inputdevice	"Synaptics Pad"
	Inputdevice "stylus"	"SendCoreEvents"
	Inputdevice "touch"	"SendCoreEvents"
	Inputdevice "eraser"	"SendCoreEvents"
EndSection

#Section "Module"
#	Load	"glx"
#EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"radeon"
EndSection

```

---

### Post by RaZoR1394 on 2008-12-21
Info about the Wacom part from "lsusb -v".

```

Bus 006 Device 003: ID 056a:0093 Wacom Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x056a Wacom Co., Ltd
  idProduct          0x0093 
  bcdDevice            3.73
  iManufacturer           1 Tablet
  iProduct                2 ISD-V4
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     143
          Report Descriptor: (length is 143)
            Item(Global): Usage Page, data= [ 0x01 ] 1
                            Generic Desktop Controls
            Item(Local ): Usage, data= [ 0x02 ] 2
                            Mouse
            Item(Main  ): Collection, data= [ 0x01 ] 1
                            Application
            Item(Global): Report ID, data= [ 0x01 ] 1
            Item(Local ): Usage, data= [ 0x01 ] 1
                            Pointer
            Item(Main  ): Collection, data= [ 0x00 ] 0
                            Physical
            Item(Global): Usage Page, data= [ 0x09 ] 9
                            Buttons
            Item(Local ): Usage Minimum, data= [ 0x01 ] 1
                            Button 1 (Primary)
            Item(Local ): Usage Maximum, data= [ 0x02 ] 2
                            Button 2 (Secondary)
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0x01 ] 1
            Item(Global): Report Count, data= [ 0x02 ] 2
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Count, data= [ 0x01 ] 1
            Item(Global): Report Size, data= [ 0x06 ] 6
            Item(Main  ): Input, data= [ 0x03 ] 3
                            Constant Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Usage Page, data= [ 0x01 ] 1
                            Generic Desktop Controls
            Item(Local ): Usage, data= [ 0x30 ] 48
                            Direction-X
            Item(Local ): Usage, data= [ 0x31 ] 49
                            Direction-Y
            Item(Global): Logical Minimum, data= [ 0x81 ] 129
            Item(Global): Logical Maximum, data= [ 0x7f ] 127
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Global): Report Count, data= [ 0x02 ] 2
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
            Item(Main  ): End Collection, data=none
            Item(Global): Usage Page, data= [ 0x0d ] 13
                            Digitizer
            Item(Local ): Usage, data= [ 0x02 ] 2
                            Pen
            Item(Main  ): Collection, data= [ 0x01 ] 1
                            Application
            Item(Global): Report ID, data= [ 0x02 ] 2
            Item(Local ): Usage, data= [ 0x20 ] 32
                            Stylus
            Item(Main  ): Collection, data= [ 0x00 ] 0
                            Physical
            Item(Local ): Usage, data= [ 0x42 ] 66
                            Tip Switch
            Item(Local ): Usage, data= [ 0x44 ] 68
                            Barrel Switch
            Item(Local ): Usage, data= [ 0x45 ] 69
                            Eraser
            Item(Local ): Usage, data= [ 0x3c ] 60
                            Invert
            Item(Local ): Usage, data= [ 0x00 ] 0
                            Undefined
            Item(Local ): Usage, data= [ 0x32 ] 50
                            In Range
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0x01 ] 1
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Report Count, data= [ 0x06 ] 6
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Count, data= [ 0x02 ] 2
            Item(Main  ): Input, data= [ 0x03 ] 3
                            Constant Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Usage Page, data= [ 0x01 ] 1
                            Generic Desktop Controls
            Item(Local ): Usage, data= [ 0x30 ] 48
                            Direction-X
            Item(Global): Logical Maximum, data= [ 0xc8 0x66 ] 26312
            Item(Global): Physical Maximum, data= [ 0xc8 0x66 ] 26312
            Item(Global): Unit, data= [ 0x11 ] 17
                            System: SI Linear, Unit: Centimeter
            Item(Global): Unit Exponent, data= [ 0x0d ] 13
                            Unit Exponent: 13
            Item(Global): Report Size, data= [ 0x10 ] 16
            Item(Global): Report Count, data= [ 0x01 ] 1
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x31 ] 49
                            Direction-Y
            Item(Global): Logical Maximum, data= [ 0x88 0x40 ] 16520
            Item(Global): Physical Maximum, data= [ 0x88 0x40 ] 16520
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Physical Maximum, data= [ 0x00 ] 0
            Item(Global): Unit, data= [ 0x00 ] 0
                            System: None, Unit: (None)
            Item(Global): Unit Exponent, data= [ 0x00 ] 0
                            Unit Exponent: 0
            Item(Global): Usage Page, data= [ 0x0d ] 13
                            Digitizer
            Item(Local ): Usage, data= [ 0x30 ] 48
                            Tip Pressure
            Item(Global): Logical Maximum, data= [ 0xff 0x00 ] 255
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
            Item(Local ): Usage, data= [ 0x00 ] 0
                            Undefined
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Main  ): Feature, data= [ 0x12 ] 18
                            Data Variable Absolute No_Wrap Non_Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               7
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      59
          Report Descriptor: (length is 59)
            Item(Global): Usage Page, data= [ 0x0d ] 13
                            Digitizer
            Item(Local ): Usage, data= [ 0x04 ] 4
                            Touch Screen
            Item(Main  ): Collection, data= [ 0x01 ] 1
                            Application
            Item(Local ): Usage, data= [ 0x22 ] 34
                            Finger
            Item(Main  ): Collection, data= [ 0x00 ] 0
                            Physical
            Item(Local ): Usage, data= [ 0x42 ] 66
                            Tip Switch
            Item(Local ): Usage, data= [ 0x32 ] 50
                            In Range
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0x01 ] 1
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Report Count, data= [ 0x02 ] 2
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Count, data= [ 0x01 ] 1
            Item(Global): Report Size, data= [ 0x06 ] 6
            Item(Main  ): Input, data= [ 0x03 ] 3
                            Constant Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Usage Page, data= [ 0x01 ] 1
                            Generic Desktop Controls
            Item(Local ): Usage, data= [ 0x30 ] 48
                            Direction-X
            Item(Global): Logical Maximum, data= [ 0xff 0x0f ] 4095
            Item(Global): Physical Maximum, data= [ 0x64 0x66 ] 26212
            Item(Global): Unit, data= [ 0x11 ] 17
                            System: SI Linear, Unit: Centimeter
            Item(Global): Unit Exponent, data= [ 0x0d ] 13
                            Unit Exponent: 13
            Item(Global): Report Size, data= [ 0x10 ] 16
            Item(Global): Report Count, data= [ 0x01 ] 1
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x31 ] 49
                            Direction-Y
            Item(Global): Physical Maximum, data= [ 0x24 0x40 ] 16420
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
            Item(Main  ): End Collection, data=none
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8
Device Status:     0x0001
  Self Powered

```

---

### Post by Favux on 2008-12-21
OK, now I'm getting confused.   Here is what I get with dmesg | grep Wacom:
```
[   31.299615] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input11
[   31.366595] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.1/input/input12
[   31.421224] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

```
You see, it's detecting the input, and yours is not.  You have the module loaded, but no input detected.  Have you tried reverting the the input paths in the uploaded xorg.conf?

You are on 8.10 Intrepid, right?  Have you tried uninstalling the Touchkit?  Maybe it's messing things up somehow.

---

### Post by Kinst on 2008-12-21
I think you're supposed to do /dev/input/wacom because it redirects automatically to whatever the wacom input device is currently assigned to.

---

### Post by Favux on 2008-12-21
Hi Kinst,

I remember reading somewhere that there was a symbolic link or something made by wacom, so what you're suggesting should/could work.  The problem I'm having is that I've yet to see an xorg.conf that was done that way.

I did a little more investigating and "/dev/input/wacom" does seem to work for folks with seperate Wacom USB graphics tablets that they plug into their computer.  I tried it on my TX2000 laptop and it does **not** work for my tablet pc with inbuilt Wacom tablet.

---

### Post by RaZoR1394 on 2008-12-21
> **Favux said:**
> OK, now I'm getting confused.   Here is what I get with dmesg | grep Wacom:
```
[   31.299615] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input11
[   31.366595] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.1/input/input12
[   31.421224] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

```
You see, it's detecting the input, and yours is not.  You have the module loaded, but no input detected.  Have you tried reverting the the input paths in the uploaded xorg.conf?

You are on 8.10 Intrepid, right?  Have you tried uninstalling the Touchkit?  Maybe it's messing things up somehow.

Yes I'm using Intrepid 8.10 32bit. Yes I have tried reverting the input paths and also removed TouchKit drivers before that.

The good news is that I have made radeonhd work pretty ok. Correct resolution on both internal and external 22" VGA screen. Although VGA makes it look not so good but I could live with it. And as an analogue picture is processed in the GPU and not in the screen motherboard I don't think there is more I can do than change VGA cable. This tablet should really have had HDMI.

Another bad news is that all USB devices I plug in either through USB hub, docking station or directly gives the computer a lot of problems during the Linux booting process. If I remove everything except keyboard and mouse I can often boot fine but the keyboard and mouse stop working shortly after I've logged into Gnome. There are a a lot of USB errors in dmesg when this happens, some about "bad cable" but I don't think this applies here. I have seen most of the errors (like device descriptor error) on all my computers. Most have gotten better with a new kernel.

---

### Post by Favux on 2008-12-21
Hi RaZoR1394,

OK, that's new information.  Might I suggest while you're trying to get the tablet working not plugging in all the USB devices and hubs.

Many other folks have gotten their TX2500 to work.  Most of them follow the gali98 tutorial I reference earlier and then use the xorg.conf I gave you.

Why don't we go back to basics.  You've uninstalled the touchkit stuff completely.  Are you willing to try uninstalling the wacom stuff completely too?  Use the xorg.conf I gave you and follow gali98's tutorial exactly (copy and paste)?  Leave all the usb stuff unplugged.  And do not run the second monitor!!!  One thing at a time.

HAL (hardware abstraction layer, new in Intrepid) should handle the mouse/touchpad and keyboard.  The reason that the keyboard isn't commented out in the xorg.conf I gave you is that HAL breaks single key key binding.  If you want to enable your "Q" key for screen rotation you have to continue to use your keyboard through xorg.conf.  If not you can comment it out.

---

### Post by RaZoR1394 on 2008-12-22
> **Favux said:**
> Hi RaZoR1394,

OK, that's new information.  Might I suggest while you're trying to get the tablet working not plugging in all the USB devices and hubs.

Many other folks have gotten their TX2500 to work.  Most of them follow the gali98 tutorial I reference earlier and then use the xorg.conf I gave you.

Why don't we go back to basics.  You've uninstalled the touchkit stuff completely.  Are you willing to try uninstalling the wacom stuff completely too?  Use the xorg.conf I gave you and follow gali98's tutorial exactly (copy and paste)?  Leave all the usb stuff unplugged.  And do not run the second monitor!!!  One thing at a time.

HAL (hardware abstraction layer, new in Intrepid) should handle the mouse/touchpad and keyboard.  The reason that the keyboard isn't commented out in the xorg.conf I gave you is that HAL breaks single key key binding.  If you want to enable your "Q" key for screen rotation you have to continue to use your keyboard through HAL.  If not you can comment it out.

I have gotten this to work, at least the pen and touch part with the help of the gali98 guide and this one [http://ubuntuforums.org/showpost.php?p=5471693&postcount=7](http://ubuntuforums.org/showpost.php?p=5471693&postcount=7) although I found the gali98 guide confusing. I'm using the config from xyexz. The key was to use the kernel driver from the compile of 0.8.2. The wacom kernel driver provided with Intrepid seems to malfunction. Once I had replaced the kernel driver I got new files under /dev/input/by-path. I had to replace the Xorg driver as well.

However the cursor is really jumpy and touching works when it feels like.

My /var/log/Xorg.0.log is full of this garbage:

```

wacom: rel event recv'd (3)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (3)!
wacom: rel event recv'd (3)!

```

Even though almost all user space apps were marked as YES/OK during ./configure none have been installed so I have to use them from the src or prebuilt dir. Wacdump seems to work fine but I cannot launch wacomcpl.

After the last boot when I first got the the wacom working and before that none of your files under by-path were present but now they seem to be so I'm going to try your config (AGAIN) and do a CTRL-ALT-BACKSPACE.

---

### Post by RaZoR1394 on 2008-12-22
Pen works a lot better with your config, both tracking, touch and right click. Eraser is however not working in Gournal or Xournal.

Wacdump and cat won't work against the files under by-path or by-id. Maybe they are occupied?

---

### Post by Favux on 2008-12-22
Hi RaZoR1394,

Great!

So it was a "nonfunctioning" wacom kernel, interesting.  Loic2 and mesilliac should know.  When you said you installed 0.8.2 from the LWP's deb's, I thought that included the kernel.  Gali98 comes through again!

Anyway the jumping erratic pen etc is what you get when you've activated Wacom (and the pen, etc.) but before you've calibrated them through wacomcpl as gali98's shows you how.  Have you created a .xinitrc in your /home/user name directory?  If you haven't you will loose calibration from wacomcpl after a reboot.

I talk to MartinJochimsen about eraser in Xournal and Gimp etc. on this thread:
[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")
If you need more let me know.

> Wacdump and cat won't work against the files under by-path or by-id. Maybe they are occupied? 
I've run into this problem too.  I do not know what's happening.  Maybe a bug in wacom-tools?  If you find out let me know, please.

Good job.

---

### Post by Favux on 2008-12-22
RaZoR1394,

Out of curiosity, would the following from mesilliac have made any difference?

> Some people do need the latest 0.8.1-6 linuxwacom drivers... they fix a bug where touching the pen to the tablet freezes input (essentially making the tablet useless in intrepid). If you don't have this bug you probably don't need them. Anyway, the linuxwacom drivers come with precompiled binaries so all you need to do is:

* double click the linuxwacom-0.8.1-6.tar.bz2 file and extract it to your desktop (you can delete these later)
* open a terminal (Accessories > Terminal)
* type the following:
Code:

cd Desktop/linuxwacom-0.8.1-6/prebuilt
sudo ./uninstall
sudo ./install

* Restart X by logging out, then logging in again

If this messes anything up for you, you can always go back to the default by running in a terminal:
Code:

sudo aptitude reinstall xserver-xorg-input-wacom wacom-tools

Just wanted to answer that because I know I've been worried about it in the past.

---

### Post by RaZoR1394 on 2008-12-22
Probably, but I don't want to use a beta (0.8.1-6) when there's a more fresh final (0.8.2). Available.

Screen calibration is ok for me, a tiny bit out of alignment but it works good enough. Touchscreen is not working at all.

I'm running keyboard and mouse straight into the tablet and I have not had a problem for at least 1 hour. However that's not optimal because I have to unplug mouse, keyboard and dock when taking the laptop with me. The dock works perfect with my tx1020ea.

```

razor1394@scorpia:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-82
stepping	: 1
cpu MHz		: 600.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4398.11
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-82
stepping	: 1
cpu MHz		: 600.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4398.49
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate

razor1394@scorpia:~$ cat /proc/cpuinfo | grep sse3
razor1394@scorpia:~$

```

According to this page

[http://www.notebookcheck.net/AMD-Turion-X2-Ultra-Notebook-Prozessor.10129.0.html](http://www.notebookcheck.net/AMD-Turion-X2-Ultra-Notebook-Prozessor.10129.0.html)

Turion X2 Ultra cpu:s have sse3...

Nothing critical, I'm just a bit confused. The important part is AMD VT.

The IEC598 (SPDIF) switch is now mysteriously gone. It was right there under switches in the mixer. I have never used either optical or coax with my tx1020ea but I'm pretty sure it should work. I need it now for my receiver.

I have both a coax cable and a 3,5mm optical -> TOSLINK.


Thanks for all the help and happy holidays.

---

### Post by Favux on 2008-12-22
Sorry, I meant substituting 0.8.2 for 0.8.1-6.  Anyway you basically seem good to go!

Happy holidays.

---

### Post by RaZoR1394 on 2008-12-22
USB errors back again...

```

[  142.036575] usb 3-4: reset high speed USB device using ehci_hcd and address 5
[  157.184568] usb 3-4: device descriptor read/64, error -110
[  172.436629] usb 3-4: device descriptor read/64, error -110
[  172.764622] usb 3-4: reset high speed USB device using ehci_hcd and address 5
[  187.912641] usb 3-4: device descriptor read/64, error -110
[  203.169133] usb 3-4: device descriptor read/64, error -110
[  203.496098] usb 3-4: reset high speed USB device using ehci_hcd and address 5
[  213.929451] usb 3-4: device not accepting address 5, error -110
[  214.064612] usb 1-2: new full speed USB device using ohci_hcd and address 8
[  214.233068] usb 1-2: configuration #1 chosen from 1 choice
[  214.237196] hub 1-2:1.0: USB hub found
[  214.239033] hub 1-2:1.0: 4 ports detected
[  214.332566] usb 3-4: reset high speed USB device using ehci_hcd and address 5
[  224.768633] usb 3-4: device not accepting address 5, error -110
[  224.771766] sd 9:0:0:0: Device offlined - not ready after error recovery
[  224.904082] usb 4-1: new full speed USB device using ohci_hcd and address 2
[  225.074180] usb 4-1: configuration #1 chosen from 1 choice
[  225.082977] input: Razer Razer Lachesis as /devices/pci0000:00/0000:00:13.0/usb4/4-1/4-1:1.0/input/input18
[  225.125705] input,hidraw5: USB HID v1.00 Mouse [Razer Razer Lachesis] on usb-0000:00:13.0-1
[  225.131343] input: Razer Razer Lachesis as /devices/pci0000:00/0000:00:13.0/usb4/4-1/4-1:1.1/input/input19
[  225.185180] input,hidraw6: USB HID v1.00 Keyboard [Razer Razer Lachesis] on usb-0000:00:13.0-1
[  225.265366] usb 1-2.1: new low speed USB device using ohci_hcd and address 9
[  225.381082] usb 1-2.1: configuration #1 chosen from 1 choice
[  225.389886] input: Gaming Keyboard as /devices/pci0000:00/0000:00:12.0/usb1/1-2/1-2.1/1-2.1:1.0/input/input20
[  225.457247] input,hidraw7: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:12.0-2.1
[  225.469482] input: Gaming Keyboard as /devices/pci0000:00/0000:00:12.0/usb1/1-2/1-2.1/1-2.1:1.1/input/input21
[  225.523086] input,hiddev98,hidraw8: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:12.0-2.1
[  225.601482] usb 1-2.4: new full speed USB device using ohci_hcd and address 10
[  225.735535] usb 1-2.4: configuration #1 chosen from 1 choice
[  225.746701] input: G15 Keyboard G15 Keyboard as /devices/pci0000:00/0000:00:12.0/usb1/1-2/1-2.4/1-2.4:1.0/input/input22
[  225.806642] input,hiddev99,hidraw9: USB HID v1.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:12.0-2.4
[  225.808604] usb 3-4: USB disconnect, address 5
[  225.920573] usb 3-4: new high speed USB device using ehci_hcd and address 11

```

---

### Post by RaZoR1394 on 2008-12-22
Ok it turns out that the ES632AA quickdock is not compatible with my tx2690eo however it works fine with tx1020ea (including good picture when connecting to the dock vga port and usb).

Now I'm connected with VGA to the port on the tx2690eo laptop itself and It's much better.

So it seems I'll need to get a new quickdock for about 100$.

More importantly would be to get the 3,5mm optical jack working. There is no red light coming out of it at all.

Any ideas?

---

### Post by Favux on 2008-12-22
Hi again RaZoR1394,

> Ok it turns out that the ES632AA quickdock is not compatible with my tx2690eo
Well that may explain some of your output.  I might go back over some of it, keeping an unstable dock connection in mind.

> More importantly would be to get the 3,5mm optical jack working. There is no red light coming out of it at all.  Any ideas? 
Nope, sorry.  It's not something I've investigated.  Let me know what you find out.

---

### Post by RaZoR1394 on 2008-12-23
Ok so I just disabled the line in /etc/modprobe/alsa-base I applied to get audio working for this tablet and after reboot IEC958 is available (two switches) but there is still no red light and sound from laptop speakers is off course gone.

The line I put at the bottom is:

options snd-hda-intel index=0 model=toshiba position_fix=1

and I took it from here (gali98)

[http://ubuntuforums.org/showthread.php?t=972552&highlight=hp+tx2500](http://ubuntuforums.org/showthread.php?t=972552&highlight=hp+tx2500)

However it seems to be half-working. Because when I crank up the main volume and switch IEC958 on and off I hear a pop from my 7.1 speakers connected to my Pioneer receiver.

I'm going to try the acer line from the same thread.

---

### Post by RaZoR1394 on 2008-12-23
The "acer" line does the same, sound works through speakers but spdif gets disabled.

Intrepid is using 1.0.17 and Jaunty is using 1.0.18.

This is the changelog... from [http://www.alsa-project.org/](http://www.alsa-project.org/)

for 1.0.18 since 1.0.17

```

HDA Intel driver

    ALSA: hda - Align BDL position adjustment parameter 
    ALSA: hda_intel: ALSA HD Audio patch for Intel Ibex Peak DeviceIDs 
    ALSA: hda - support new AMD HDMI Audio (1002:970f) 
    ALSA: hda_intel: enable snoop for nvidia HDA controller 
    ALSA: hda - disable delayed period-ack with bdl_pos_adj=0 
    ALSA: hda - check page continuity 
    ALSA: hda - Fix VIA recording problem 
    ALSA: hda - allow probing of 4 codecs 
    ALSA: Fix for reading RIRB buffer on NVIDIA aza controller with AMD Phenom cpu 
    ALSA: hda - Add infrastructure for dynamic stream allocation 

```

for 1.0.18a since 1.0.18

```

HDA Intel driver

    ALSA: hda - Add reboot notifier 
    ALSA: hda - Remove old codec-probe limitation 
    ALSA: hda - simplify hda_bus ops callbacks 
    ALSA: hda - Make codec-probing more robust 
    ALSA: hda - Fix probe errors on Dell Studio Desktop 

```

Here is a thread I'm following first:

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

otherwise I will resort to the master kernel thread and if that shows no result it looks like I will be moving over to Jaunty.

---

### Post by Favux on 2008-12-23
Hi Razor,

Yeah, I've looked at the ALSA stuff, without joy.  There's some pulse audio stuff in pre-release, maybe something will be there.

My bet is you're going to Jaunty.  You're braver than I am.  Remember the new kernel will break linuxwacom and you'll have to reinstall.

---

### Post by RaZoR1394 on 2008-12-23
I got spdif working by following the Pulsaudio update and reconfigure thread. Very good guide I must say.

I have installed linux 2.6.28-rc9 as well now but there is no big need for it right now.

I used this app from the master kernel thread, [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

This thread could be interesting for those who want to change firmware on the DVDRW drive.

[http://forum.rpc1.org/viewtopic.php?f=2&t=44504&start=0&st=0&sk=t&sd=a](http://forum.rpc1.org/viewtopic.php?f=2&t=44504&start=0&st=0&sk=t&sd=a)

Windows only as usual...

---

### Post by RaZoR1394 on 2008-12-24
I have been looking at a new dock and the HP page for Sweden says I need KN745AA. The only way to order that is by phone and they have closed during holidays (probably open 26th don't know) but It's half the price than big retailers. Smells fishy to me. No word about stock status either.

I can find the KN744AA dock on Ebay with shipping for about the same price of the KN745AA without shipping from HP Sweden. The only store in Sweden except HP themselves selling the product and having it in stock want double the price.

Both the KN745AA and KN744AA are part of the Quickdock 2.0 series. I have no idea about the differences of these docks. Maybe the KN745AA is a bug fix? The one I have now is Quickdock 1.0.

There are some disturbing reviews about the KN744AA dock on the net...

[http://www.amazon.com/review/product/B001COCG9G](http://www.amazon.com/review/product/B001COCG9G)

[http://www.shopping.hp.com/product/computer/categories/docking_solutions/1/accessories/KN744AA%2523ABA;HHOJSID=XpfhJLWNMxpMDbs1dpzhKDhRjGNnPLMyLPNf3Jy82KDzyyLQ0DhN!979183832?tab=reviews&](http://www.shopping.hp.com/product/computer/categories/docking_solutions/1/accessories/KN744AA%2523ABA;HHOJSID=XpfhJLWNMxpMDbs1dpzhKDhRjGNnPLMyLPNf3Jy82KDzyyLQ0DhN!979183832?tab=reviews&)

Some problems described there sound just like mine.

Component output has been removed with the Quickdock 2.0 series as well.

Do you think it would work with KN744AA?

---

### Post by Favux on 2008-12-24
Hi RaZoR1394,

I'd steer clear of the KN744AA for now.  I think what you want is a live salesperson on the phone that you can get a name and id # from and then ask about the cord length issues, etc.  And how do you feel about only VGA out?  Does the KN745AA have HD out?

I was vaguely thinking about a dock now that I've got my Pinnacle tuner and new printer.  I'll look some more.

---

### Post by Favux on 2008-12-24
No KN745AA at all on US web site.  A picture pops up with no further information.  You have S video out on the TX2500 right?   Dock only has VGA?  So does the dock have any advantages over a USB hub and a S-video cable?
I still think it is better to contact someone at HP to answer more detailed questions.  Among other laptops it says the KN744AA#ABA is compatible with TX1000 and TX2000.  Nothing about TX2500.  So we assume TX2000 includes TX2500?

---

### Post by RaZoR1394 on 2008-12-24
Yes the KN744AA and KN745AA does not have component as they are Quickdock 2.0 models.

The Quickdock 2.0 does however have two power inlets instead of just one. I have no idea of why.

Here is the Quick setup for the Quickdock 2.0 - [http://h10032.www1.hp.com/ctg/Manual/c01621850.pdf](http://h10032.www1.hp.com/ctg/Manual/c01621850.pdf)

The biggest advantage is efficiency. When leaving all that has to be done is to disconnect the expansion port 3 cable. In my case the eSATA express-card as well but that's all.

Well I was going to write about the fact that you can use the pen when the laptop screen is off and paint on the external screen just like an external Wacom when I pressed my nail against the screen and noticed it worked just like the pen so I guess the touchscreen part is solved as well, at least temporary.

---

### Post by Favux on 2008-12-24
Ah ha.  So touchscreen is working.

I cleaned up the xorg.conf a little bit, to better use as a sample.  You might want to look at it.

Did you get .xinitrc working?  I'm including my .xinitrc so you can see the Capacity parameter for touch.  Values are 1-5.  This should help get touch more sensitive.

---

### Post by RaZoR1394 on 2008-12-27
Hi thanks for the configuration file. Unfortunately I moved to Jaunty right before you posted your last message in this thread. Jaunty behaves very differently. As soon as there is something inappropriate in xorg.conf I get stuck at the splash screen, that means not even thrown back into terminal mode. The only driver that works is radeon and radeonhd and 2d rendering is so slow that It's unbearable. It made me jump to another distro but that one had so many problem I wondered if it was really a final I got. So I made a clean install of Jaunty alpha 2 and the problem was still present.

CTRL-ALT-BACKSPACE is also disabled in Jaunty. You have to enable it manually.

On the good side. I have no problems with USB with the dock and it seems that the bad picture problem with the dock was just a matter of pressing the AUTO (calibration) button on the TFT screen.

---

### Post by Favux on 2008-12-27
Hi RaZoR1394,

Very interesting.  I wonder if a new version of Xorg's Xserver is responsible? One that is continuing to deprecate xorg.conf.  We (tablet users) sort of thought we got a commitment to make things more tablet friendly.  Going back to Gutsy or Hardy function-wise.  Hopefully this is just because it is alpha.

Sounds like at least the new kernel is more functional for you.

---

### Post by Favux on 2009-05-03
Hi RaZoR1394,

I thought I'd let you know, since you're in Jaunty, that MisteR2 has cracked rotation with the swivel hinge.  The signal turns out to be handled by the HP-WMI kernel module.  He contacted the maintainer Matthew Garrett who discovered it was mixed in with the docking event.  So he separated it out for us and provided a patch that MisteR2 has posted on page 11, posts #104 and #106 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=11](http://ubuntuforums.org/showthread.php?t=996830&page=11)  MisteR2 also cobbled a .fdi to go along with it.

I assume you got a the new dock for your TX2500.

---

