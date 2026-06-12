---
title: "SIS graphics: 14.04 works fine, but 14.10 won't detect my monitor"
date: 2014-11-11
forum: Hardware
---

### Post by oldsmobile_mike on 2014-11-11
Kind of a Linux noob, haven't used it in years, but hoping to get back into it.  My test system is a 10-year-old Averatec 6220 laptop, 2GB RAM, Athlon 64 3000+ processor, 80GB hard drive, Intel integrated graphics.

Installed Lubuntu 14.04 about a month ago, ran great, detected all the hardware correctly, drivers, etc., no issues.  Played around with it for a few weeks and got the notification to update to 14.10.  Thinking I always like to be on the "latest and greatest", I performed the upgrade.  After reboot my monitor settings would only give me the option of 640x480 or "Auto", not the 1280x800 I should've had.

Thinking something went wrong in the upgrade, I downloaded the DVD for 14.10 and installed it fresh, but same problem.  Monitor only had two modes: 640x480 and Auto.  Then I installed the full version of Ubuntu 14.04, it ran slowly but detected my screenmodes correctly.

So after a few more reinstalls, I think I've narrowed it down:  Lubuntu and Ubuntu 14.04 detect my Intel integrated graphics and work fine, but 14.10 only gives the option of 640x480 or Auto.  So, what changed between these two versions, and how can I fix it?  I'm vaguely aware of something called xorg.conf, but am basically a Linux noob, so please dumb down any tips, thanks!  :-)

---

### Post by mörgæs on 2014-11-18
First let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by oldsmobile_mike on 2014-11-18
```

computer
    description: Notebook
    product: 6240 Series
    vendor: AVERATEC
    version: 0101
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: chassis=notebook uuid=[REMOVED]
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: A1011SMS V1.10 12/06/04
          date: 12/06/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int17printer acpi usb agp i2oboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: Mobile AMD Athlon(tm) 64 Processor 3000+
          serial: [REMOVED]
          slot: CPU 1
          size: 1600MHz
          capacity: 2010MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good nopl cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:dfe00000-dfefffff memory:cfd00000-dfcfffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:d0000000-d7ffffff memory:dfee0000-dfefffff ioport:cc00(size=128)
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2/3 SMBus controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:c00(size=32)
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=64 maxlatency=11 mingnt=52
             resources: ioport:e400(size=256) ioport:e000(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=64 maxlatency=11 mingnt=52
             resources: irq:18 ioport:e800(size=256) ioport:ec00(size=128)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:20 memory:dfffd000-dfffdfff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:21 memory:dfffe000-dfffefff
        *-usb:2
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64 maxlatency=80
             resources: irq:23 memory:dffff000-dfffffff
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
             resources: irq:19 ioport:d800(size=256) memory:dfffc000-dfffcfff memory:dffc0000-dffdffff
        *-pcmcia
             description: CardBus bridge
             product: CB1410 Cardbus Controller
             vendor: ENE Technology Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:17 memory:80000000-80000fff ioport:1000(size=256) ioport:1400(size=256) memory:84000000-87ffffff memory:88000000-8bffffff
        *-network:1
             description: Wireless interface
             product: RT2500 Wireless 802.11bg
             vendor: Ralink corp.
             physical id: e
             bus info: pci@0000:00:0e.0
             logical name: wlan0
             version: 01
             serial: [REMOVED]
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt2500pci driverversion=3.16.0-25-generic firmware=N/A ip=[REMOVED] latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
             resources: irq:18 memory:dfffa000-dfffbfff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HTS721080G9AT00
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: A51A
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=7696608e
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 72GiB
                capacity: 72GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-10-24 20:55:21 filesystem=ext4 lastmountpoint=/ modified=2014-11-18 17:18:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-11-18 17:18:35 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1918MiB
                capacity: 1918MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1918MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVDRW SOSW-852S
             vendor: Slimtype
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: PES2
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc

```

Any suggestions?  Thanks!

---

### Post by mörgæs on 2014-11-18
No Intel graphics here, but SIS.

The bug for these GPU's was fixed in 14.04. If it has returned then it's a regression which needs to be investigated further. Could you try 15.04 (development version), please? Could you also post the output from **apt-cache policy xserver-xorg-video-sis **using 14.10?


Here's a little more about SIS cards: 
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

### Post by oldsmobile_mike on 2014-11-18
Hi mörgæs,

Thanks for the link!  That's definitely the problem I'm having.  I followed the instructions posted by javier-ejsf to create an xorg.conf file.  Using a copy & paste of his code I was able to get 1280x768.  Still not the correct 1280x800, and it seems slower (by comparison to how it worked under 14.04, anyway).  Any ideas where I would find the correct xorg.conf file?  Alternatively, where can I download 15.04 from?  Here's a little more info on my system:

```

sudo lshw -C video

  *-display UNCLAIMED
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:d0000000-d7ffffff memory:dfee0000-dfefffff ioport:cc00(size=128)

```

Thanks!

---

### Post by mörgæs on 2014-11-18
Here: [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

An xorg.conf shouldn't be necessary to begin with. Please post the output mentioned above when you have the time.

---

### Post by oldsmobile_mike on 2014-11-18
Thanks, I just found it on Google, downloading it now.  Without any xorg.conf file all I get is 640x480.  I did not have this problem under 14.04, as it worked fine without xorg.conf.  Under 14.10 with the file from that thread I can do 1280x768, but not 1280x800.  Which command should I post the output from?

---

### Post by oldsmobile_mike on 2014-11-18
I tried following instructions to create a new xorg.conf file.  This is what I got now...

```

averatec@averatec-6240-Series:~$ apt-cache show xserver-xorg-video-sis
N: Unable to locate package xserver-xorg-video-sis
E: No packages found

averatec@averatec-6240-Series:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 720, maximum 1280 x 768
default connected 1280x720+0+0 0mm x 0mm
   1280x720        0.0* 
   1024x768       61.0  
   800x600        61.0  
   640x480        60.0  
   1280x768        0.0  

averatec@averatec-6240-Series:~$ sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:d0000000-d7ffffff memory:dfee0000-dfefffff ioport:cc00(size=128)

```

---

### Post by oldsmobile_mike on 2014-11-18
As a test I booted off a live CD of 15.04.  I was only able to do 1280x768 resolution.  Then I booted off my live CD of 14.04 and was able to get 1280x800.  I didn't need to change anything, it defaulted right to the correct resolution.  Something is definitely broken in the newer versions...

---

### Post by mörgæs on 2014-11-19
Does the output in #8 come from 14.10?

---

### Post by oldsmobile_mike on 2014-11-19
> **mörgæs said:**
> Does the output in #8 come from 14.10?

Yes.  That's using the xorg.conf file I copied out of the previous thread.  If I don't use that I only get 640x480 resolution.

---

### Post by mörgæs on 2014-11-19
I just got this from Temüjin:

> The SiS video driver was dropped in Utopic, probably because it did not build against Xserver 1.16.x

Patches for that are now in git: [http://cgit.freedesktop.org/xorg/driver/xf86-video-sis/](http://cgit.freedesktop.org/xorg/driver/xf86-video-sis/)



So for now the options are a) stay with 14.04 or b) install 14.10 and use an xorg.conf.

---

### Post by oldsmobile_mike on 2014-11-19
> **mörgæs said:**
> I just got this from Temüjin:




So for now the options are a) stay with 14.04 or b) install 14.10 and use an xorg.conf.

Oh, well that's unfortunate!  Can you point me in the right direction for any tips to build a proper xorg.conf file?  I've googled a few but am not having much success.  I like some of the other new features of 14.10 and would prefer to stick with it, but would like to be able to use my proper screenmode (1280x800) as well.  Also is there any downside (performance-wise, etc.) to using an xorg.conf?  Thanks!

---

### Post by mörgæs on 2014-11-19
Sorry, don't know.

---

### Post by oldsmobile_mike on 2014-11-19
**YES.  I figured it out.  :D**

After significant research here's the steps I did:

sudo apt-add-repository ppa: xorg-edgers
sudo apt-get install xserver-xorg-video-sis

delete any xorg.conf files from /etc/X11

Reboot

It appears to be a version of the SiS display driver specifically for 14.10.  System came back up running the correct 1280x800 screenmode.  I still need to test it a little more but all appears good.

More info here:  [http://www.ubuntuupdates.org/package/xorg-edgers/utopic/main/base/xserver-xorg-video-sis](http://www.ubuntuupdates.org/package/xorg-edgers/utopic/main/base/xserver-xorg-video-sis)

Thanks so much for your help, I hope this info helps others in the future!

---

### Post by matt_symes on 2014-11-19
Hi

@oldsmobile_mike.

This may help me out as well. 

Any chance you could post the output of the command below to see if it will please :)

```
lspci -nnk | grep -iA2 vga
```

It needs the capital A above.

Kind regards

---

### Post by oldsmobile_mike on 2014-11-19
@matt_symes - Sure, here you go!

```

01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:0111]

```

---

### Post by matt_symes on 2014-11-19
Hi

> **oldsmobile_mike said:**
> @matt_symes - Sure, here you go!

```

01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] [661/741/760]("tel:661/741/760") PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:0111]

```

Cheers buddy :) 

You have the same vga controller as me.
 
I had the pretty much the same issue. 

Alright under 14.04 but could not get anything better than 800x600 under a dev version of 14.10.

I've had to use a custom xorg.conf since I got these boxes but I can't complain as they were a gift.

This thread will hopefully save me some time so cheers to all who contributed.

Kind regards

---

### Post by oldsmobile_mike on 2014-11-19
Glad to help!  Post back if the above steps I posted fix the problem for you, too! :)

---

### Post by maurrox on 2015-01-01
> **oldsmobile_mike said:**
> **YES.  I figured it out.  :D**

After significant research here's the steps I did:

sudo apt-add-repository ppa: xorg-edgers
sudo apt-get install xserver-xorg-video-sis

delete any xorg.conf files from /etc/X11

Reboot


This is perfect to me ... thank's a lot!!

For beginner before sudo apt-add-repository ppa: xorg-edgers 
sudo apt-get update

--- --- ------ --- ------ --- ---
Old notebook Aspire 3503WLMi whit Lubuntu 14.04 

lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330] Subsystem: Acer Incorporated [ALI] Device [1025:0082]

---

### Post by Agret on 2015-06-29
> **oldsmobile_mike said:**
> **YES.  I figured it out.  :D**

After significant research here's the steps I did:

sudo apt-add-repository ppa:xorg-edgers
sudo apt-get install xserver-xorg-video-sis

delete any xorg.conf files from /etc/X11

Reboot

I just did a ton of apt-get update and apt-get upgrade and then did a dist upgrade and now i'm on Vivid (15.04)

I've added the ppa and performed an apt-get update and here is my output trying to install the sis video driver

> probit@linuxsvr:~$ sudo apt-get install xserver-xorg-video-sis
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xserver-xorg-video-sis

---

### Post by oldsmobile_mike on 2015-10-19
Hate to drag up my old thread here but I just updated this laptop to 15.04 and am getting the "unable to locate package xserver-xorg-video-sis" error message trying to install it through the terminal.

I manually downloaded it from some site I found on Google, but when I try to run it from the desktop I get the message "Error: Dependency is not satisfiable: xorg-video-abi-15" (I think this is the Trusty version, it's all I could find).

Any suggestions?  Thanks!

---

### Post by Yellow Pasque on 2015-10-21
If you can't find a .deb package of the 0.10.8 release, you can build your own:
```
sudo apt-get install build-essential xorg-dev
cd ~/   #or whatever directory you want to use for this build
wget http://xorg.freedesktop.org/releases/individual/driver/xf86-video-sis-0.10.8.tar.bz2
tar xjf xf86-video-sis-0.10.8.tar.bz2
cd xf86-video-sis-0.10.8/
./configure --prefix=/usr/local
make
sudo make install
```

---

### Post by mörgæs on 2016-10-11
Bump to keep the thread open. Advice for 14.04 is still valid, especially for SIS.

---

### Post by mörgæs on 2016-12-31
Testing [this hardware]("https://ubuntuforums.org/showthread.php?t=2215422&p=12994894&viewfull=1#post12994894") again under Lubuntu 16.04.1 yielded the following results: 

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024     77.00*

```

As can be seen I couldn't get the widescreen resolution of 1920x1080 from 14.04 but 1280x1024 is also acceptable. The old hardware is still useable.

---

