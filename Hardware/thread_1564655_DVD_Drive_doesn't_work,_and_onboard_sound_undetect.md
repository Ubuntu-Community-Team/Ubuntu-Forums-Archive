---
title: "DVD Drive doesn't work, and onboard sound undetected"
date: 2010-08-30
forum: Hardware
---

### Post by Gralamin on 2010-08-30
So I'm having two issues, in my latest install.

First, my DVD drive doesn't work, however:

```
gralamin@odin-linux:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD A  DH20A4H
       vendor: ATAPI
       physical id: 0
       bus info: scsi@7:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: QP5A
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```
Obviously shows it.

Second, I am using the [onboard sound of my Motherboard]("http://www.asus.com/product.aspx?P_ID=ZcmQJBZe92MltsOo") for 5.1 surrond sound. However:

```
gralamin@odin-linux:~$ lspci -v | less
...
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Device 82ea
        Flags: bus master, fast devsel, latency 0, IRQ 3
        Memory at fb8f8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
...

```
Has it shown, but alsamixer and gnome-volume-control cannot detect it. I've tried using [A script](http://www.stchman.com/alsa_update.html) to update alsa, but it hasn't helped.

I was going to try getting any ASUS drivers for the sound in Linux off the DVD, but obviously I have not been able to. I also cannot figure out how to successfully make the drivers listed on ASUS site.

Any help will be appreciated.

Edit: I ran alsa-info.sh, and this is the result:
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Aug 31 01:01:12 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.32-21-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.16
Utilities version:  1.0.16


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
02:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3a3e
	Subsystem: 1043:82ea
--
02:00.1 0403: 1002:aa50
	Subsystem: 1043:aa50


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=3stack
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:207: no soundcards found...

ARECORD

arecord: device_list:207: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
sco
bridge
stp
bnep
l2cap
btusb
bluetooth
usb_storage
binfmt_misc
ppdev
fglrx
fbcon
tileblit
font
bitblit
softcursor
lp
vga16fb
parport
vgastate
asus_atk0110
pata_marvell
usbhid
hid
dm_raid45
mvsas
libsas
scsi_transport_sas
ohci1394
floppy
ieee1394
ahci
sky2
xor


!!ALSA/HDA dmesg
!!------------------


```

---

