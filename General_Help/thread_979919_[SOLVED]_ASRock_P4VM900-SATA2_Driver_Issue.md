---
title: "[SOLVED] ASRock P4VM900-SATA2 Driver Issue"
date: 2008-11-12
forum: General Help
---

### Post by erudite on 2008-11-12
I own a ASRock P4VM900-SATA2 Motherboard.  It comes with an inbuilt VIA Delta Chrome Graphics (Card).

However, Ubuntu doesn't seem to contain the drivers and I can't seem to find any.  This means that I cannot do things like watch videos in full screen...  Any help would be appreciated.

---

### Post by starcannon on 2008-11-12
Hi again Erudite,
Please run and post the output of:
```

sudo lshw

```

---

### Post by erudite on 2008-11-12
I can pastebin this if need be.

```
description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4VM900-SATA2
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.10 (09/06/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: CPUSocket
          size: 2400MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-system UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=32 mingnt=2
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32 module=sata_via
           *-disk:0
                description: ATA Disk
                product: SAMSUNG HD753LJ
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 1AA0
                serial: S13UJ1KQ405600
                size: 698GiB (750GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e40ae3f0
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/disk
                   version: 1.0
                   serial: 65f3af65-4c23-41aa-bf6c-20b0998786ec
                   size: 698GiB
                   capacity: 698GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-08-28 18:08:27 filesystem=ext3 modified=2008-11-11 17:49:30 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2008-11-11 17:49:30 state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC WD5000AAKS-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 12.0
                serial: WD-WCAS82663566
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=54425442
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 30a45284-d775-4ca8-ad0f-c964d6941400
                   size: 464GiB
                   capacity: 464GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-09-07 00:38:53 filesystem=ext3 modified=2008-11-11 17:49:29 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-11-11 17:49:29 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   size: 1286MiB
                   capacity: 1286MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 1286MiB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-cdrom:0
                description: DVD writer
                product: DVDRW4216IND-A
                vendor: IOMEGA
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.20
                serial: [IOMEGA  DVDRW4216IND-A  1.2003042200
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD-RAM writer
                product: DVD Writer 1040d
                vendor: HP
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: EH23
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237S PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:19:66:45:c0:65
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.7 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
        *-pci:2
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ae:3f:0d:fc:1a:7c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by starcannon on 2008-11-12
No need to pastebin it, just throw a code tag around it.
{code}your data here{/code}
replace curly braces with square braces.

---

### Post by erudite on 2008-11-12
Done thanks.

---

### Post by starcannon on 2008-11-12
Are you using 8.04 or 8.10?

---

### Post by erudite on 2008-11-12
8.10 however I upgraded from 8.04 and had the same problem with that.

---

### Post by starcannon on 2008-11-12
Okay, well I've not messed with the via driver in 8.10 yet, I see they have a specific driver for it. I am not sure if it will do 3d or not, but it should increase 2d performance to the levels required for video playback... *should* being the key hedge. Keep in mind that VIA and Linux can be a bit slippery, but one way or the other I think we can get you rolling if your ready to roll your sleeves up ;)

Okay, that said, lets get some downloading done:
[http://linux.via.com.tw/support/beginDownload.action?eleid=221&fid=422](http://linux.via.com.tw/support/beginDownload.action?eleid=221&fid=422)

Let me know when you have that on your HDD, please stash it in your home folder.

/home/erudite/85a-43862-u810-2d-bin.tar.gz

then R-click and choose "Extract Here"
Open the new folder named 85a-43862-u810-2d-bin when extraction is complete.
Look at the readme file, and return here with questions regarding the installation instructions and xorg.conf setup. Oh btw:
About your monitor:

[LIST]
[*]Brand/Model
[*]Resolution
[*]Refresh rate
[/LIST]

---

### Post by starcannon on 2008-11-12
My apologies, open "AP Note for VIA IGP support on Ubuntu 8.10.htm" with firefox, the readme file I just looked at was in chinese, so if you require english like me, I think you'll find the html file a bit more useful, its in the folder as well. 

Lol argh, correction, open the ReadMe file with Open Office and it will be in english. /sigh sorry ;) 
And you will want to look at it as well.

---

### Post by erudite on 2008-11-12
haha.  Yea it wouldn't edit with text editor so I used vi in a vein attempt to get it to work and it did luckily.

I did the installation bit but not the configuration bit.

This is what xorg.conf looks like now.  Let me know if it's ok.
```
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

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"gb"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

Section "Device"
	Identifier	"name"
	Driver		"via"
        Entries...
	...

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
EndSection
```

My monitor is Yuraku and the resolution is 1440x900 and the refresh rate is 59.9Hz.

Thanks for the help so far.

---

### Post by starcannon on 2008-11-12
This spot needs cleaned up:
```
Section "Device"
    Identifier    "name"
    Driver        "via"
        Entries...
    ...
EndSection
```It should look like this for now:
```
Section "Device"
    Identifier    "name"
    Driver        "via"
EndSection
```I'll modify this post in a moment so go ahead and clean that bit up then come back and refresh this page.

---

### Post by erudite on 2008-11-12
Ok it now looks like that.

:-)

---

### Post by starcannon on 2008-11-12
Alright well, next step is to see if it likes the default settings, this may dump you to a command line situation if it does not work, in which case you may want to write this next bit down.
In the event your stuck with a black screen or some other non working gui situation:

[LIST=1]
[*]Ctrl+Alt+F1
[*]Login
[*]```
sudo nano /etc/X11/xorg.conf
```
[*]Change ```
Section "Device"
    Identifier    "name"
    Driver        "via"
EndSection
``` to ```
Section "Device"
    Identifier    "name"
    Driver        "vesa"
EndSection
```
[*]For Gnome```
sudo /etc/init.d/gdm restart
``` For KDE i believe its ```
sudo /etc/init.d/kdm restart
``` if I'm wrong about the KDE line you can always just ```
sudo reboot
```
[*]Come back here and we'll work on finding a modeline that it likes, starting with the ones in the readme, and resorting to custom ones if necessary.
[/LIST]

Okay, well lets see if lightening strikes, either press Ctrl+Alt+Backspace or Reboot.

---

### Post by erudite on 2008-11-12
How do you save a file with nano?

After you tell me this I'll do it.

---

### Post by starcannon on 2008-11-12
ah right my bad lol, i'm a bit tired:

Ctrl+X

Then answer: Y

Leave the name the way it is and press: Enter

---

### Post by erudite on 2008-11-12
Yea it works great.

Thanks so much. :-):-):-):-):-)  

Just one last thing...where do I go to get the updates for this driver if I can ever be bothered to update it?

---

### Post by starcannon on 2008-11-12
Thats great! don't forget to mark thread as SOLVED (click on thread tools upper right of screen) and I know its petty but be sure to click my thank you medal ;)

For driver updates your gonna need to keep an eye on the via linux portal at:
[http://linux.via.com.tw/](http://linux.via.com.tw/)

They don't currently have a 3d driver for 8.10 yet, but they seem very active, and are promising one in the near future.

Is video playback working for you?

---

### Post by erudite on 2008-11-12
Thread is marked as solved.

I clicked on the thank you medal for quite a few of your posts.  lol

Thanks for the link.  Thanks for your patience to help me for an hour also.

Forgot to mention, video playback works a treat.  :-D

---

### Post by starcannon on 2008-11-12
It was a pleasure to help you.
Lol i saw the thankyou's haha, and um.. thank you! hehe.

lol cool happy to hear video is good.

---

### Post by salvaleuven on 2009-03-05
Hello, i also own a P4VM900-SATA2 mobo. It seems the VIA drivers are installed correctly, but i cannot activate the advanced desktop effects. It shows a warning message "Desktop effects could not be enabled". Please i do appreciate any help.

---

### Post by erudite on 2009-03-06
Did you install the GFX driver.  If you installed the 2D driver you can't do it.

I'm not sure about the GFX one.

---

### Post by salvaleuven on 2009-03-14
Sorry, i should be more concrete. This is what i've tried:

1, I've installed the gfx driver following the instructions of the readme.txt included in the file (5.74.33.85a-44597.tar.gz)

2. Tried to activate advanced desktop effect, then it shows the warning message.

Thanks for you help

---

### Post by erudite on 2009-03-14
Well if your install went OK then I don't think you can do it.

Sorry.  You will have to get a new motherboard if you want desktop effects.  I got a new mobo and graphics card recently and I've got some nice desktop effects.

:P

---

