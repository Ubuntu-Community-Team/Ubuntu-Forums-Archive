---
title: "GeForce 8200 GS 2nd Video Card Help"
date: 2010-09-24
forum: Hardware
---

### Post by nitric on 2010-09-24
Hey Guys, I've got a desktop with on-board video and a GeForce 8400 gs.

I tried installing Ubuntu with the GeForce in however it would not load the live CD and the alt CD would get stuck partitioning at 33%, I tried CD's and USB and figured I would try installing without the GeForce installed, (have had video issues with linux before figured it was worth a shot) and using the on-board video (intel) the Ubuntu live USB loaded and installed and I'm using it now, however my GeForce is a much better video card with duel outputs and I would love to get it working again, I downloaded the latest drivers from nVidia (NVIDIA-Linux-x86-256.53.run) and dropped down to the console and installed them, but after switching my bios back to use the GeForce my monitors stay blank.

not a total linux noob but this one is driving me crazy!:confused:

---

### Post by PresenceofMind on 2010-09-24
Is your desktop a dual boot? If so, does it run on Windows without any problems?

Just wanted to know if your card is faulty.

---

### Post by nitric on 2010-09-24
card was working fine and i had my onboard disabled in the bios when I was running windows just a few days ago, then i started trying to install ubuntu and when it wasn't working i took out the video card and set my on-board to be the main video card, when I switch it back to the GeForce, the bios screen loads and everything is working on the video card until it gets to booting ubuntu then just black.

---

### Post by nitric on 2010-09-24
ok new information was just messing around with drivers latest still installed but now boot's normalish till it gets to

> ---[ end trace f8f46e50d60cbb37 ]---
nvidia: module license 'NVIDIA' taints kernel.
nvidia 0000:04:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
nvidia 0000:04:00.0: setting latency timer to 64
vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes=none: owns=io+mem
NVRM: loading NVIDIA UNIX x86 Kernel Module 195.36.24 Thu Apr 22 09:18:20 PDT 2010

if that helps at all, there's also a ton of random stuff above it but i figured it wasn't as helpful.

Edit, at this point it has been frozen at the end here for a while...

---

### Post by nitric on 2010-09-24
Ok after about 50 min being stuck at that I had to hard-shutdown my system because ctrl+alt+del wouldn't work, and I didn't change anything and now am back to a black screen with a little flashing white bar at the top (like it's waiting to type stuff out)... very confused :P

---

### Post by nitric on 2010-09-24
lshw prints out (lshw -html>[http://dl.dropbox.com/u/6920165/lshw.html]("http://dl.dropbox.com/u/6920165/lshw.html"))

```
bill-desktop              
    description: Desktop Computer
    product: HP d220 MT (DW984A)
    vendor: Hewlett-Packard
    serial: MXD44901YY
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: chassis=desktop cpus=1 uuid=9FCA389F-4548-D911-BD1C-517B4801761B
  *-core
       description: Motherboard
       product: 0888h
       vendor: Lite-On Tech.
       physical id: 0
       version: A06
       serial: 21792474403445
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1.12 (05/28/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: mPGA-478
          QUOTsize: 2800MHz
          capacity: 4GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 8KiB
             capacity: 1MiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KiB
             capacity: 1MiB
             clock: 25MHz (40.0ns)
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 2005MiB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-e7ffffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-d7ffffff(prefetchable) memory:dff80000-dfffffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e400(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e800(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ec00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:dff7bc00-dff7bfff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=8192) memory:d9c00000-dfdfffff memory:a9a00000-c9afffff(prefetchable)
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: a
                bus info: pci@0000:03:0a.0
                logical name: eth0
                version: 01
                serial: 00:0f:fe:13:b6:90
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.72 latency=32 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:19 memory:dfdfe000-dfdfffff memory:dfd00000-dfd1ffff(prefetchable)
           *-pci
                description: PCI bridge
                product: PEX8112 x1 Lane PCI Express-to-PCI Bridge
                vendor: PLX Technology, Inc.
                physical id: b
                bus info: pci@0000:03:0b.0
                version: aa
                width: 32 bits
                clock: 66MHz
                capabilities: pci pm msi pciexpress bus_master cap_list
                resources: ioport:c000(size=4096) memory:d9c00000-dfcfffff memory:a9a00000-c9afffff(prefetchable)
              *-display
                   description: VGA compatible controller
                   product: G98 [GeForce 8400 GS]
                   vendor: nVidia Corporation
                   physical id: 0
                   bus info: pci@0000:04:00.0
                   version: a1
                   width: 64 bits
                   clock: 33MHz
                   capabilities: pm msi pciexpress bus_master cap_list rom
                   configuration: driver=nvidia latency=0
                   resources: irq:21 memory:de000000-deffffff memory:b0000000-bfffffff(prefetchable) memory:dc000000-ddffffff ioport:cc00(size=128) memory:dfce0000-dfcfffff(prefetchable)
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: d
                bus info: pci@0000:03:0d.0
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
                resources: irq:22 ioport:d800(size=32)
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: d.1
                bus info: pci@0000:03:0d.1
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: irq:0 ioport:dc00(size=8)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16) memory:80000000-800003ff
           *-disk:0
                description: ATA Disk
                product: ST3802110A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5LR5DFAN
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d8420
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 16b3d3d9-2601-4f6f-a06b-874b99b37508
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-09-23 19:35:38 filesystem=ext4 lastmountpoint=/&#65533;j$v&#65533;+c&#65533;h&#65533;&#65533;&#65533;&#65533;>&#65533;p^G&#65533;h &#65533;&#65533;h/&#65533;d^G&#65533;!&#65533;1&#65533;&#65533;1&#65533;&#65533;&#65533;+c&#65533;&#65533;^G&#65533;^G&#65533;]k modified=2010-09-23 19:45:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-09-24 15:14:46 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3152MiB
                   capacity: 3152MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3152MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-3520AW
                vendor: _NEC
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 3.04
                serial: [_NEC    DVD_RW ND-3520AW3.0405040500
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: Maxtor 6B200P0
                vendor: Maxtor
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: BAH4
                serial: B41EK92H
                size: 189GiB (203GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e5bae5ba
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: ec1442e9-e1b7-774a-b90a-0044bdd975ab
                   size: 189GiB
                   capacity: 189GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2005-04-30 14:10:07 filesystem=ntfs label=Big *** Drive state=clean
           *-disk:2
                description: ATA Disk
                product: Maxtor 6Y200P0
                vendor: Maxtor
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/sdc
                version: YAR4
                serial: Y65VZTTE
                size: 189GiB (203GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=33e85e33
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: 463955d7-a9fe-f840-983b-13263e632757
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=512 created=2009-02-18 14:40:29 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.1.0,2
                   logical name: /dev/sdc2
                   version: 3.1
                   serial: 3eb58c5c-d1cb-a441-b623-3ad1a2f54fbb
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=512 created=2003-01-17 00:06:25 filesystem=ntfs label=Personal state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@1:0.1.0,3
                   logical name: /dev/sdc3
                   version: 3.1
                   serial: facc7089-0cda-694f-a14b-187cfbfbffce
                   size: 121GiB
                   capacity: 121GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=512 created=2003-01-17 00:38:28 filesystem=ntfs label=Warez state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:c00(size=32)

```

---

### Post by n1unqn on 2010-09-24
I installed 10.04 from the windows download install and it runs fine and picked up my nVidia card no problems. I had to login as root though for it to finish the driver install tough.

---

### Post by nitric on 2010-09-24
> **n1unqn said:**
> I installed 10.04 from the windows download install and it runs fine and picked up my nVidia card no problems. I had to login as root though for it to finish the driver install tough.

I want to get rid of windows though and have a native linux installation, with wubi (the windows installer) it creates a very large image file on the windows partition and loads linux from that durring boot (at least that's what it did last time I used it probably around 8.10) and I don't want that, I want to get rid of windows... also, your hardware is probably different from mine, so congrats! your nvidia card worked!!! it's often the case however in my case it is not... :(

anyone else have any ideas on what might be going on? I already tried booting with my sound card removed incase there was some IRQ conflict or something... silly linux!!! this is reminding me of when I was a kid installing redhat and other distros playing around back in the late 90's :P

---

### Post by n1unqn on 2010-09-24
Looking at your lshw you say you have a 8200gs but it thinks you have a 8400gs maybe this is the source of the problem?

---

### Post by nitric on 2010-09-24
yeah just looked at the card and the sticker on the back says 8400gs :P for some reason I thought it was an 8200 however the drivers I downloaded from the nvidia website are supposed to work for the entire 8 series so that shouldn't be the problem (I was just mistaken on the exact model) thanks for pointing that out though! ;)

---

### Post by n1unqn on 2010-09-24
Go to SYSTEM > ADMINISTRATION do you see an icon called NVIDIA X SERVER SETTINGS ?

IF YOU DO
click on it and check it says your driver installed correctly I had to do something as root before mine worked and it told me what to do there.

IF YOU DONT
try installing the recommended nvidia driver through SYSTEM > ADMINISTRATION > HARDWARE DRIVERS

---

### Post by nitric on 2010-09-24
> **n1unqn said:**
> Go to SYSTEM > ADMINISTRATION do you see an icon called NVIDIA X SERVER SETTINGS ?

IF YOU DO
click on it and check it says your driver installed correctly I had to do something as root before mine worked and it told me what to do there.

IF YOU DONT
try installing the recommended nvidia driver through SYSTEM > ADMINISTRATION > HARDWARE DRIVERS

I ran that and it said

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

when I run sudo nvidia-xconfig i get 

> WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


if I shutdown and set my bios to use the geforce as the primary graphics card it doesn't do anything new, if I use my on-board it starts in low-graphics mode and I have to reset my config to get back into ubuntu.

EDIT: I also tried doing the gdm stop that I did to install the drivers and dropped down to the console and ran sudo nvidia-xconfig and it was the same thing.

---

### Post by nitric on 2010-09-24
I found some more information and ran

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

then added
> 
# Come on nVidia!!!
blacklist intel_agp
blacklist agpgart
blacklist amd76x_edac
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv 

and it worked!!! I am now using my geforce however I now have a new problem :P Ubuntu is only running in Low-graphics mode!!!! when I start up NVIDIA X Server Settings I get the same error as before

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I ran sudo nvidia-xconfig

> Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

restarting and it's still in Low-Graphics Mode...

still working on it! :P

---

### Post by nitric on 2010-09-24
Here's the message I get when I start Ubuntu:
> 
**Ubuntu is running in low-graphics mode**

The following error was encountered. You may need to update your configuration to solve this.

(EE) Sep 24 17:40:00 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the system's kernel log for additional error messages and consult the NVIDIA README for details.

(EE) NVIDIA(0): ***Aporting ***
(EE) Screen(s) found, but none have usable configuration.

Going to try re-installing the NVIDIA drivers... brb :P

---

### Post by nitric on 2010-09-24
Just re-installed the drivers and getting the same low-graphics mode error... hrm... getting closer

also, my monitors are pretty old and have a max resolution of 1024x768, I assumed (yes I know *** U me :P) that the default resolution would be that but if it's not how do I setup my config to work???:confused:

---

### Post by nitric on 2010-09-24
when to System>Admin>Hardware Drivers and swtiched from

NVIDIA accelerated graphiccs driver (version current) [Recommended]

to

NVIDIA accelerated graphics driver (version 173)

and now it doesn't say it's in low-graphics mode however it boots into 640x480 resolution and the NVIDIA X Server Settings doesn't have anywhere to change this....

need more suggestions!!!

---

### Post by nitric on 2010-09-24
In the NVIDIA X Server Setting

> X Server Display Configuration

it says:

Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.

---

### Post by nitric on 2010-09-24
Ok I found this:

[https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-settings/+bug/539196]("https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-settings/+bug/539196")

But I am new to the launchpad thing and have no idea how to install that fix??? help? :D

---

### Post by nitric on 2010-09-24
I found some more stuff to check on that page and ran

apt-cache policy nvidia-settings

> nvidia-settings:
  Installed: 195.36.08-0ubuntu2
  Candidate: 195.36.08-0ubuntu2
  Version table:
 *** 195.36.08-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status


which the bug report said it was fixed in 195.36.08-0ubuntu2 but mine is still not working???:confused:

---

### Post by nitric on 2010-09-25
I added:

option "twinview"

to my xorg.conf file and now I have my duel monitors working again, the 2nd monitor that I just got working is at 1024x768 while my main monitor is still at 640x480 and the X Server Display Configuration tab in the NVIDIA X Server Setting is still giving me the same error "Failed to query NoScanout for screen 0."

getting closer... I think :P

---

### Post by Quadari on 2010-09-25
Hi Nitric,

I appear to be having almost exactly the same problem you are.  I had a heck of a time actually getting the 8400GS to work on my system.  I just managed to do that, but now it only seems to want to load in low graphics mode.

Just getting it to work was enough of a battle for me tonight, but I think I'll try to tackle the low-graphics issue tomorrow, so if you have any updates or figure anything out definitely let us know!

Thanks.

---

### Post by nitric on 2010-09-25
Ok so I have figured out something interesting that takes a little explaining, I have a duel-monitor setup and when I first got my video card working the setup was like this

Monitor 1 (Left monitor) had the "2nd" desktop on it and was at 1024x768.

Monitor 2 (Right monitor) had the "Primary" desktop on it (Applications Places System at the top) and was at 640x480.

If I wanted to move the mouse from the Primary desktop I had to move it to the right to go to the left monitor so I was like, easy fix and switched the cables...

NOW

Monitor 1 (Left monitor) has the Primary desktop on it and is at 1024x768.

Monitor 2 (Right monitor) has the 2nd desktop on it and is at 640x480.

From this I've concluded that it's not the port on the card that is restricting the monitor resolution to 640x480 but the monitor, does this make sense?

I still get the same error in NVIDIA X Server Settings -> X Server Display Configuration: "Failed to query NoScanout for screen 0."

---

### Post by nitric on 2010-09-25
I have the monitor
[http://www.unicomplabs.com/Lcd/sampo_pd-70fa2.asp](http://www.unicomplabs.com/Lcd/sampo_pd-70fa2.asp)
except it's black and use to be a touch screen
(the glass inside broke and so I got 2 of them for free! I removed the glass and they have been great 15" flatscreens for a long time!)

---

### Post by nitric on 2010-09-25
I replaced the cable connecting Monitor 2 to the computer and now Both are working at 1024x768 however, I still get the same error in NVIDIA X Server Settings -> X Server Display Configuration: "Failed to query NoScanout for screen 0." :P but it's progress!

---

### Post by nitric on 2010-09-25
Also I believe I have the correct settings and driver installed... BAH! :P

$ apt-cache policy nvidia-settings
nvidia-settings:
  Installed: 195.36.08-0ubuntu2
  Candidate: 195.36.08-0ubuntu2
  Version table:
 *** 195.36.08-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status

$ apt-cache policy nvidia-173
nvidia-173:
  Installed: 173.14.22-0ubuntu11
  Candidate: 173.14.22-0ubuntu11
  Version table:
 *** 173.14.22-0ubuntu11 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Packages
        100 /var/lib/dpkg/status

$ uname -a
Linux desktop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

My sudo lshw -html > [http://dl.dropbox.com/u/6920165/lshw.html](http://dl.dropbox.com/u/6920165/lshw.html) again.

I hope I can get this fixed!!! <3 Ubuntu!

---

### Post by Quadari on 2010-09-25
So I managed to fix my issue.  I'm not sure if this helps you, but it turns out that I was having a conflict between the cx18 driver that drives my Hauppauge HVR-1600 tuner card, and the Nvidia driver.  The fix is actually pretty simple.  I didn't come up with it, so credit goes to the first poster in the thread that did, but here's my summary of what worked for me:

[http://ubuntuforums.org/showpost.php?p=9888147&postcount=29](http://ubuntuforums.org/showpost.php?p=9888147&postcount=29)


Hope that helps for you....

---

### Post by nitric on 2010-09-25
Hey Thanks, I tried that and unfortunately for me it did not work, still trying to figure out this NVIDIA Settings problem!! :P

---

### Post by nitric on 2010-09-27
Anyone else have any more ideas? I mean both are running 1024x768 so it's not terrible but I'd like to have access to the config screen, I also haven't tried my TV out yet which worked before and would be cool to have working again!

---

### Post by Fafler on 2010-09-27
Theres a bug report it here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/523108](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/523108)

As for the whole 8200/8400 thing, 8200 doesn't exist as a stand alone card. It's part of certain Nvidia chipsets.

And TV out, by the way, you cannot have more than two monitors connected at any time, so no TV out while using both LCD monitors.

---

### Post by nitric on 2010-09-27
> **Fafler said:**
> Theres a bug report it here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/523108](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/523108)

As for the whole 8200/8400 thing, 8200 doesn't exist as a stand alone card. It's part of certain Nvidia chipsets.

And TV out, by the way, you cannot have more than two monitors connected at any time, so no TV out while using both LCD monitors.

That bug report hasn't been fixed if you look at [https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-settings/+bug/539196](https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-settings/+bug/539196) it's the same problem but says it's been fixed however if you look at a previous post of mine I have the "correct" nvidia-settings and driver installed (195.36.08-0ubuntu2 and 173.14.22-0ubuntu11 respectively), also I said sorry about the 8200/8400 thing it was a "typo" on my behalf :P and yeah I know in windows I would just disable my 2nd monitor when I would switch to TV out however since my nvidia-settings doesn't want to work properly I don't know if my TV will work, I haven't tested it yet but it's been a long weekend :P

Anyone have any productive suggestions?

---

### Post by nitric on 2010-10-12
Just an update for anyone who comes accross this thread, Updating from Ubuntu 10.04 to 10.10 fixed my problem, I can now configure both monitors and switched from Nvidia driver v 173 to the latest (recommended) drivers :D Thanks everyone who helped me get this working before!!!

---

