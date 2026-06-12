---
title: "Thinkpad 600e Common Problem Help"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by Bojangles352 on 2006-01-30
Alright, I've got 5.10, and it installed pretty easily on my 600e, but I've got the regular sound and ethernet problems (but not the resolution one). I've searched everywhere and done everything anyone has said, but nothing seems to work, so I decided that maybe I could get some one on one help or something. I can deal without the sound, so although I'd like to get it to work, I'd rather get Internet to work more. I have the Xircom 10/100 EtherJet, and I'm pretty sure it's being identified by the computer. I can post the grub files or anything if they would help. Any help is greatly appreciated.

---

### Post by morphodone on 2006-01-30
do you see your device in - System > Administration > Networking

if so, have you tried to configure the connection there?

---

### Post by Bojangles352 on 2006-01-30
eth0 is active with a Static IP.

---

### Post by morphodone on 2006-01-30
[QUOTE=Bojangles352]eth0 is active with a Static IP.[/QUOTE]

have you tried a dynamic ip - dhcp?

can you ping your router (if you have one)?

---

### Post by Bojangles352 on 2006-01-31
I tried DHCP and it said activating for awhile and just ended, I'm not sure if anything happened. It went back to Static after a restart. I don't have a router. I remember some thread here that had steps to follow to find out why it wouldn't work, but I can't seem to find it.

---

### Post by morphodone on 2006-02-01
[QUOTE=Bojangles352]I tried DHCP and it said activating for awhile and just ended, I'm not sure if anything happened. It went back to Static after a restart. I don't have a router. I remember some thread here that had steps to follow to find out why it wouldn't work, but I can't seem to find it.[/QUOTE]

If you don't have a router I assume you are plugged into your broadband modem directly.  If that is the case, then you cannot specify a static ip address.  The ip address is assigned to you by your internet service provider.

Here are some console commands that might help.

```

ifconfig eth0 - displays all information about the eth0 interface
ifconfig eth0 up - turn on eth0 interface
ifconfig eth0 down - shut down eth0 interface
sudo dhclient - should accept a dhcp address from your modem

```

Sometimes I like console commands versus the gnome network manager.

---

### Post by mips on 2006-02-01
Do a search for Thinkpad 600 or just 600 in this forum and you will find answers to get the LAN & Sound working.

---

### Post by Bojangles352 on 2006-02-01
I tried DHCP before and it said everything was denied or something. I'll try again soon to see if anything's changed. Also, I've tried everything I've found on these forums but none of it helped.

---

### Post by mips on 2006-02-01
Have you tried [http://www.ubuntuforums.org/showthread.php?t=123642&highlight=600e](http://www.ubuntuforums.org/showthread.php?t=123642&highlight=600e) for the sound ?

I know you said you tried everything.

For the LAN:
[http://www.ubuntuforums.org/showthread.php?t=116155](http://www.ubuntuforums.org/showthread.php?t=116155)
[http://www.ubuntuforums.org/showthread.php?t=122083](http://www.ubuntuforums.org/showthread.php?t=122083)
[http://www.ubuntuforums.org/showthread.php?t=82011](http://www.ubuntuforums.org/showthread.php?t=82011)

---

### Post by Bojangles352 on 2006-02-01
[QUOTE=mips]Have you tried [http://www.ubuntuforums.org/showthread.php?t=123642&highlight=600e](http://www.ubuntuforums.org/showthread.php?t=123642&highlight=600e) for the sound ?

I know you said you tried everything.

For the LAN:
[http://www.ubuntuforums.org/showthread.php?t=116155](http://www.ubuntuforums.org/showthread.php?t=116155)
[http://www.ubuntuforums.org/showthread.php?t=122083](http://www.ubuntuforums.org/showthread.php?t=122083)
[http://www.ubuntuforums.org/showthread.php?t=82011](http://www.ubuntuforums.org/showthread.php?t=82011)[/QUOTE]
I've read all those, is it possible I put the code in the wrong place? 
My /boot/grub/menu.lst:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/mapper/Ubuntu-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd		/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro single
initrd		/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin  
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 acpi=off apm=on pci=noacpi pnpbios=off
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

```
I've tried the code below "End Debian..." above that line, as well. I also read somewhere to try acpi=force, which I've also tried.
My /etc/modules:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sound
ad1848
uart401
snd-cs4236

```
My /etc/hotplug/blacklist:
```

#
# Listing a module here prevents the hotplug scripts from loading it.
# Usually that'd be so that some other driver will bind it instead,
# no matter which driver happens to get probed first.  Sometimes user
# mode tools can also control driver binding.
#
# Syntax:  driver name alone (without any spaces) on a line. Other
# lines are ignored.
#

# uhci ... usb-uhci handles the same pci class
usb-uhci
# usbcore ... module is loaded implicitly, ignore it otherwise
usbcore

#evbug is a debug tool and should be loaded explicitly
evbug

# these drivers are very simple, the HID drivers are usually preferred
usbmouse
usbkbd

# replaced by e100
eepro100

# replaced by tulip
de4x5

# replaced by tmscsim
am53c974

# watchdog drivers should be loaded only if a watchdog daemon is installed
acquirewdt
advantechwdt
alim1535_wdt
alim7101_wdt
cpu5wdt
eurotechwdt
i810_tco
i8xx_tco
i810-tco
ib700wdt
indydog
machzwd
mixcomwd
pcwd
pcwd_pci
pcwd_usb
sa1100_wdt
sbc60xxwdt
sc1200wdt
sc520_wdt
scx200_wdt
shwdt
softdog
w83627hf_wdt
w83877f_wdt
wafer5823wdt
wdt285
wdt977
wdt
wdt_pci

# causes no end of confusion by creating unexpected network interfaces
eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
i2c_i801
snd-cs46xx
cs46xx

```
My /etc/modprobe.d/alsa-base:
```
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7
# Load optional modules above their base modules
install snd modprobe --ignore-install snd && { modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 && { /lib/alsa/modprobe-post-install snd-emu10k1 ; modprobe --quiet snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx && { /lib/alsa/modprobe-post-install snd-via82xx ; modprobe --quiet snd-seq ; }
# Cause a script to be run after *-synth module initialization
install snd-emu8000-synth modprobe --ignore-install snd-emu8000-synth && /lib/alsa/modprobe-post-install snd-emu8000-synth
install snd-emu10k1-synth modprobe --ignore-install snd-emu10k1-synth && /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
install snd-ad1816a modprobe --ignore-install snd-ad1816a && /lib/alsa/modprobe-post-install snd-ad1816a
install snd-ad1848 modprobe --ignore-install snd-ad1848 && /lib/alsa/modprobe-post-install snd-ad1848
install snd-ali5451 modprobe --ignore-install snd-ali5451 && /lib/alsa/modprobe-post-install snd-ali5451
install snd-als100 modprobe --ignore-install snd-als100 && /lib/alsa/modprobe-post-install snd-als100
install snd-als4000 modprobe --ignore-install snd-als4000 && /lib/alsa/modprobe-post-install snd-als4000
install snd-armaaci modprobe --ignore-install snd-armaaci && /lib/alsa/modprobe-post-install snd-armaaci
install snd-asihpi modprobe --ignore-install snd-asihpi && /lib/alsa/modprobe-post-install snd-asihpi
install snd-atiixp modprobe --ignore-install snd-atiixp && /lib/alsa/modprobe-post-install snd-atiixp
install snd-au1x00 modprobe --ignore-install snd-au1x00 && /lib/alsa/modprobe-post-install snd-au1x00
install snd-au8810 modprobe --ignore-install snd-au8810 && /lib/alsa/modprobe-post-install snd-au8810
install snd-au8820 modprobe --ignore-install snd-au8820 && /lib/alsa/modprobe-post-install snd-au8820
install snd-au8830 modprobe --ignore-install snd-au8830 && /lib/alsa/modprobe-post-install snd-au8830
install snd-azt2320 modprobe --ignore-install snd-azt2320 && /lib/alsa/modprobe-post-install snd-azt2320
install snd-azt3328 modprobe --ignore-install snd-azt3328 && /lib/alsa/modprobe-post-install snd-azt3328
install snd-ca0106 modprobe --ignore-install snd-ca0106 && /lib/alsa/modprobe-post-install snd-ca0106
install snd-cmi8330 modprobe --ignore-install snd-cmi8330 && /lib/alsa/modprobe-post-install snd-cmi8330
install snd-cmipci modprobe --ignore-install snd-cmipci && /lib/alsa/modprobe-post-install snd-cmipci
install snd-cs4231 modprobe --ignore-install snd-cs4231 && /lib/alsa/modprobe-post-install snd-cs4231
install snd-cs4232 modprobe --ignore-install snd-cs4232 && /lib/alsa/modprobe-post-install snd-cs4232
install snd-cs4236 modprobe --ignore-install snd-cs4236 && /lib/alsa/modprobe-post-install snd-cs4236
install snd-cs4281 modprobe --ignore-install snd-cs4281 && /lib/alsa/modprobe-post-install snd-cs4281
install snd-cs46xx modprobe --ignore-install snd-cs46xx && /lib/alsa/modprobe-post-install snd-cs46xx
install snd-darla20 modprobe --ignore-install snd-darla20 && /lib/alsa/modprobe-post-install snd-darla20
install snd-darla24 modprobe --ignore-install snd-darla24 && /lib/alsa/modprobe-post-install snd-darla24
install snd-dt019x modprobe --ignore-install snd-dt019x && /lib/alsa/modprobe-post-install snd-dt019x
install snd-echo3g modprobe --ignore-install snd-echo3g && /lib/alsa/modprobe-post-install snd-echo3g
install snd-emu10k1x modprobe --ignore-install snd-emu10k1x && /lib/alsa/modprobe-post-install snd-emu10k1x
install snd-ens1370 modprobe --ignore-install snd-ens1370 && /lib/alsa/modprobe-post-install snd-ens1370
install snd-ens1371 modprobe --ignore-install snd-ens1371 && /lib/alsa/modprobe-post-install snd-ens1371
install snd-es1688 modprobe --ignore-install snd-es1688 && /lib/alsa/modprobe-post-install snd-es1688
install snd-es18xx modprobe --ignore-install snd-es18xx && /lib/alsa/modprobe-post-install snd-es18xx
install snd-es1938 modprobe --ignore-install snd-es1938 && /lib/alsa/modprobe-post-install snd-es1938
install snd-es1968 modprobe --ignore-install snd-es1968 && /lib/alsa/modprobe-post-install snd-es1968
install snd-es968 modprobe --ignore-install snd-es968 && /lib/alsa/modprobe-post-install snd-es968
install snd-fm801 modprobe --ignore-install snd-fm801 && /lib/alsa/modprobe-post-install snd-fm801
install snd-fm801-tea575x modprobe --ignore-install snd-fm801-tea575x && /lib/alsa/modprobe-post-install snd-fm801-tea575x
install snd-gina20 modprobe --ignore-install snd-gina20 && /lib/alsa/modprobe-post-install snd-gina20
install snd-gina24 modprobe --ignore-install snd-gina24 && /lib/alsa/modprobe-post-install snd-gina24
install snd-gusclassic modprobe --ignore-install snd-gusclassic && /lib/alsa/modprobe-post-install snd-gusclassic
install snd-gusextreme modprobe --ignore-install snd-gusextreme && /lib/alsa/modprobe-post-install snd-gusextreme
install snd-gusmax modprobe --ignore-install snd-gusmax && /lib/alsa/modprobe-post-install snd-gusmax
install snd-harmony modprobe --ignore-install snd-harmony && /lib/alsa/modprobe-post-install snd-harmony
install snd-hda-intel modprobe --ignore-install snd-hda-intel && /lib/alsa/modprobe-post-install snd-hda-intel
install snd-hdsp modprobe --ignore-install snd-hdsp && /lib/alsa/modprobe-post-install snd-hdsp
install snd-hdspm modprobe --ignore-install snd-hdspm && /lib/alsa/modprobe-post-install snd-hdspm
install snd-ice1712 modprobe --ignore-install snd-ice1712 && /lib/alsa/modprobe-post-install snd-ice1712
install snd-ice1724 modprobe --ignore-install snd-ice1724 && /lib/alsa/modprobe-post-install snd-ice1724
install snd-indigo modprobe --ignore-install snd-indigo && /lib/alsa/modprobe-post-install snd-indigo
install snd-indigodj modprobe --ignore-install snd-indigodj && /lib/alsa/modprobe-post-install snd-indigodj
install snd-indigoio modprobe --ignore-install snd-indigoio && /lib/alsa/modprobe-post-install snd-indigoio
install snd-intel8x0 modprobe --ignore-install snd-intel8x0 && /lib/alsa/modprobe-post-install snd-intel8x0
install snd-interwave modprobe --ignore-install snd-interwave && /lib/alsa/modprobe-post-install snd-interwave
install snd-interwave-stb modprobe --ignore-install snd-interwave-stb && /lib/alsa/modprobe-post-install snd-interwave-stb
install snd-korg1212 modprobe --ignore-install snd-korg1212 && /lib/alsa/modprobe-post-install snd-korg1212
install snd-layla20 modprobe --ignore-install snd-layla20 && /lib/alsa/modprobe-post-install snd-layla20
install snd-layla24 modprobe --ignore-install snd-layla24 && /lib/alsa/modprobe-post-install snd-layla24
install snd-maestro3 modprobe --ignore-install snd-maestro3 && /lib/alsa/modprobe-post-install snd-maestro3
install snd-mia modprobe --ignore-install snd-mia && /lib/alsa/modprobe-post-install snd-mia
install snd-miro modprobe --ignore-install snd-miro && /lib/alsa/modprobe-post-install snd-miro
install snd-mixart modprobe --ignore-install snd-mixart && /lib/alsa/modprobe-post-install snd-mixart
install snd-mona modprobe --ignore-install snd-mona && /lib/alsa/modprobe-post-install snd-mona
install snd-mpu401 modprobe --ignore-install snd-mpu401 && /lib/alsa/modprobe-post-install snd-mpu401
install snd-msnd-pinnacle modprobe --ignore-install snd-msnd-pinnacle && /lib/alsa/modprobe-post-install snd-msnd-pinnacle
install snd-mtpav modprobe --ignore-install snd-mtpav && /lib/alsa/modprobe-post-install snd-mtpav
install snd-nm256 modprobe --ignore-install snd-nm256 && /lib/alsa/modprobe-post-install snd-nm256
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2
install snd-opti92x-ad1848 modprobe --ignore-install snd-opti92x-ad1848 && /lib/alsa/modprobe-post-install snd-opti92x-ad1848
install snd-opti92x-cs4231 modprobe --ignore-install snd-opti92x-cs4231 && /lib/alsa/modprobe-post-install snd-opti92x-cs4231
install snd-opti93x modprobe --ignore-install snd-opti93x && /lib/alsa/modprobe-post-install snd-opti93x
install snd-pc98-cs4232 modprobe --ignore-install snd-pc98-cs4232 && /lib/alsa/modprobe-post-install snd-pc98-cs4232
install snd-pcsp modprobe --ignore-install snd-pcsp && /lib/alsa/modprobe-post-install snd-pcsp
install snd-pcxhr modprobe --ignore-install snd-pcxhr && /lib/alsa/modprobe-post-install snd-pcxhr
install snd-pdaudiocf modprobe --ignore-install snd-pdaudiocf && /lib/alsa/modprobe-post-install snd-pdaudiocf
install snd-pdplus modprobe --ignore-install snd-pdplus && /lib/alsa/modprobe-post-install snd-pdplus
install snd-portman2x4 modprobe --ignore-install snd-portman2x4 && /lib/alsa/modprobe-post-install snd-portman2x4
install snd-powermac modprobe --ignore-install snd-powermac && /lib/alsa/modprobe-post-install snd-powermac
install snd-pxa2xx-ac97 modprobe --ignore-install snd-pxa2xx-ac97 && /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
install snd-rme32 modprobe --ignore-install snd-rme32 && /lib/alsa/modprobe-post-install snd-rme32
install snd-rme96 modprobe --ignore-install snd-rme96 && /lib/alsa/modprobe-post-install snd-rme96
install snd-rme9652 modprobe --ignore-install snd-rme9652 && /lib/alsa/modprobe-post-install snd-rme9652
install snd-s3c2410 modprobe --ignore-install snd-s3c2410 && /lib/alsa/modprobe-post-install snd-s3c2410
install snd-sa11xx-uda1341 modprobe --ignore-install snd-sa11xx-uda1341 && /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
install snd-sb16 modprobe --ignore-install snd-sb16 && /lib/alsa/modprobe-post-install snd-sb16
install snd-sb8 modprobe --ignore-install snd-sb8 && /lib/alsa/modprobe-post-install snd-sb8
install snd-sbawe modprobe --ignore-install snd-sbawe && /lib/alsa/modprobe-post-install snd-sbawe
install snd-serialmidi modprobe --ignore-install snd-serialmidi && /lib/alsa/modprobe-post-install snd-serialmidi
install snd-serial-u16550 modprobe --ignore-install snd-serial-u16550 && /lib/alsa/modprobe-post-install snd-serial-u16550
install snd-sgalaxy modprobe --ignore-install snd-sgalaxy && /lib/alsa/modprobe-post-install snd-sgalaxy
install snd-sonicvibes modprobe --ignore-install snd-sonicvibes && /lib/alsa/modprobe-post-install snd-sonicvibes
install snd-sscape modprobe --ignore-install snd-sscape && /lib/alsa/modprobe-post-install snd-sscape
install snd-sun-amd7930 modprobe --ignore-install snd-sun-amd7930 && /lib/alsa/modprobe-post-install snd-sun-amd7930
install snd-sun-cs4231 modprobe --ignore-install snd-sun-cs4231 && /lib/alsa/modprobe-post-install snd-sun-cs4231
install snd-sun-dbri modprobe --ignore-install snd-sun-dbri && /lib/alsa/modprobe-post-install snd-sun-dbri
install snd-trident modprobe --ignore-install snd-trident && /lib/alsa/modprobe-post-install snd-trident
install snd-usb-audio modprobe --ignore-install snd-usb-audio && /lib/alsa/modprobe-post-install snd-usb-audio
install snd-usb-usx2y modprobe --ignore-install snd-usb-usx2y && /lib/alsa/modprobe-post-install snd-usb-usx2y
install snd-vx222 modprobe --ignore-install snd-vx222 && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxp440 modprobe --ignore-install snd-vxp440 && /lib/alsa/modprobe-post-install snd-vxp440
install snd-vxpocket modprobe --ignore-install snd-vxpocket && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront modprobe --ignore-install snd-wavefront && /lib/alsa/modprobe-post-install snd-wavefront
install snd-ymfpci modprobe --ignore-install snd-ymfpci && /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

```


Also, the card worked on the laptop with Windows 98, so it should still be working.

---

### Post by grumpymole on 2006-02-02
One other option to try is to swap the dma1 and dma2 settings around in the long line in /etc/modprobe.d/alsa-base.  I have seen some other people in the past say that they had to do this.  To do this set dma2=1 and dma1=0.

For the kernel params, one quick way to check is when you reboot, look for the kernel line after the grub countdown.  You should she acpi=off etc.

Also, could you describe more precisely what the state of your (non)sound is?  Do you get a speaker icon in the task bay/tray? 

Regards

Warren

---

### Post by Bojangles352 on 2006-02-03
There's a speaker icon in the tray with an "x" by it. When clicked it says "Error: The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured..." when clicked again, it reads, "Error: No volume control elements and/or devices found."

Also, it doesn't appear switching the dma settings has worked, but it's getting kinda late, so I'll wait until tomorrow to test everything.

---

### Post by Bojangles352 on 2006-02-05
Alright, I think I figured out what's wrong (I created a whole new line in Grub instead of editing the first string), but now Ubuntu won't boot. I changed
```

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd		/initrd.img-2.6.12-9-386
savedefault
boot
``` 

to boot from /dev/hd1. I'll try and change it with a LiveCD in a bit.

---

### Post by Bojangles352 on 2006-02-12
Alright, sorry for this triple post, but I seem to be able to connect (I'm receiving packets like crazy) but I can't actually do anything. I don't have an ip (dhconfig doesn't do anything) and I can't connect to any sites or use GAIM. Any ideas?

---

### Post by Bojangles352 on 2006-05-01
It's been a few months and still not working, just wondering if there've been any new developments.

---

### Post by mips on 2006-05-02
I would really like to help but have run out of ideas.

[http://www.ubuntuforums.org/showthread.php?t=141605](http://www.ubuntuforums.org/showthread.php?t=141605)

Have you considered trying the latest Dapper Ubuntu/Kubuntu/Xubuntu ?
[https://lists.ubuntu.com/archives/ubuntu-announce/2006-April/000072.html](https://lists.ubuntu.com/archives/ubuntu-announce/2006-April/000072.html)

---

