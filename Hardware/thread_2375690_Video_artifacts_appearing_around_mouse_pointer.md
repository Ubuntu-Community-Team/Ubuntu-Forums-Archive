---
title: "Video artifacts appearing around mouse pointer"
date: 2017-10-26
forum: Hardware
---

### Post by accounts0 on 2017-10-26
I'm on Ubuntu 16.04.3, which was installed from the 'server' iso then installed Kubuntu, etc. Updates are current.

I'm having occasional graphics problems, I haven't been able to determine what exactly triggers it. It happens maybe 75% of the time.

I've pasted output of lshw [1], & a screenshot of the video artifacts [2]. They happen around the mouse cursor & manifest as garbled horizontal lines across the screen.

Sometimes there are many at once, rendering the screen unreadable, but usually they seem to go back to normal on their own after maybe 4 or 5 instances. This I don't understand at all, since I'm not moving anything over the parts of the screen when the artifacts correct themselves, seemingly nothing that would trigger a refresh of the affected pixels.

I imagine this has to do with the video driver(s). I know there's 2 graphics devices on this laptop, buT I don't know anything about it- eg. which one is in use, how to switch to the other one, what drivers I'm using, & how to make all that up-to-date & configured properly for use over HDMI like I'm doing. Usually it 'just works' except now for some reason.

I don't remember if this has been happening all the way back since I first installed it. It could be that I just overlooked it since after a several lines it corrects. I guess it hasn't bothered me until now, & has likely been happening the whole time.

Help is appreciated. 


EDIT:
So annoying [3]. Wishing this problem were solved.


[1]
[http://sebsauvage.net/paste/?f26109db10fcddf0#25pKdKI9fMi6eqDjR8FxSct4KWxTVQhkJ138+lIo3rE=](http://sebsauvage.net/paste/?f26109db10fcddf0#25pKdKI9fMi6eqDjR8FxSct4KWxTVQhkJ138+lIo3rE=)

[2]
[https://imgur.com/a/h0ycD](https://imgur.com/a/h0ycD)

[3]
[https://imgur.com/a/Y1MUn](https://imgur.com/a/Y1MUn)

---

### Post by accounts0 on 2017-10-31
So... today it's not happening anymore. I have a script that does an aptitude upgrade every logon, but it's usually done & disappeared by the time I get to doing anything on my desktop so I never see what it actually does. I wonder what got updated such that it's solved now...

---

### Post by accounts0 on 2017-11-05
Again today though. Was a nice run without for a few days. Don't get what's wrong- no pattern emerging. :-(

---

### Post by mörgæs on 2017-11-08
You have a Skylake CPU which can't be expected to work well with old software like 16.04. 

I suggest that you try Xubuntu 17.10 in a live boot. Is there any change?

---

### Post by accounts0 on 2017-11-09
> **mörgæs said:**
> You have a Skylake CPU which can't be expected to work well with old software like 16.04.

I was under the impression that choosing the most current "LTS" release would prevent exactly this kind of issue. I even went with the "xx.x.3" variant just for this reason.

I'll try your suggestion re: a Live CD. Thanks for taking the time to reply.

---

### Post by accounts0 on 2017-12-13
Just got around to trying the 17.10 LiveCD tonight, as was suggested earlier. Did not go well. 

It booted fine & both HDMI & laptop screen worked up to the point where you can choose to "Try" or "Install". In my case I clicked "Try", at which point both screens displayed a black screen with a flashing cursor in the upper left. The DVD stopped reading, & it just sat there for like 5 minutes before I gave up.

---

### Post by mörgæs on 2017-12-15
The lshw output to which you linked has been removed. Please post it again here in CODE tags.

---

### Post by accounts0 on 2017-12-15
> **mörgæs said:**
> The lshw output to which you linked has been removed. Please post it again here in CODE tags.

```
user@Hostname:~$ sudo lshw
[sudo] password for user: 
voyageri                  
    description: Notebook
    product: Inspiron 5559 (06B2)
    vendor: Dell Inc.
    serial: H3TRN72
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 vsyscall32
    configuration: boot=normal chassis=docking family=Inspiron sku=06B2 uuid=44454C4C-3300-1054-8052-C8C04F4E3732
  *-core
       description: Motherboard
       product: 052K07
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: /H3TRN72/CN1296363N0479/
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 1.2.9
          date: 06/21/2017
          size: 64KiB
          capacity: 15MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cache:0
          description: L1 cache
          physical id: 41
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 42
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: 43
          slot: L2 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 44
          slot: L3 Cache
          size: 4MiB
          capacity: 4MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 45
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2496MHz
          capacity: 3100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 threads=4
     *-memory
          description: System Memory
          physical id: 46
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT41GS6BFR8A-PB
             vendor: SK Hynix
             physical id: 0
             serial: 12151215
             slot: DIMM A
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT41GS6BFR8A-PB
             vendor: SK Hynix
             physical id: 1
             serial: 12121212
             slot: DIMM B
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Sky Lake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Sky Lake Integrated Graphics
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:277 memory:d1000000-d1ffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:122 memory:d2210000-d221ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.13.0-19-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: VIA Labs, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 90.70
                   capabilities: usb-2.10
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: USB Receiver
                      vendor: Logitech
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 12.03
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
                 *-usb:1
                      description: Keyboard
                      product: Microsoft
                      vendor: Microsoft
                      physical id: 4
                      bus info: usb@1:1.4
                      version: 7.04
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: GenesysLogic
                   physical id: 3
                   bus info: usb@1:3
                   version: 92.24
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Mass storage device
                      product: External USB 3.0
                      vendor: TOSHIBA
                      physical id: 3
                      bus info: usb@1:3.3
                      logical name: scsi2
                      version: 2.03
                      serial: 2015033100063
                      capabilities: usb-2.10 scsi
                      configuration: driver=uas maxpower=500mA speed=480Mbit/s
                    *-disk
                         description: SCSI Disk
                         product: nal USB 3.0
                         vendor: TO Exter
                         physical id: 0.0.0
                         bus info: scsi@2:0.0.0
                         logical name: /dev/sdc
                         version: 0203
                         serial: 2015033100063
                         size: 232GiB (250GB)
                         capabilities: partitioned partitioned:dos
                         configuration: ansiversion=6 logicalsectorsize=512 sectorsize=4096 signature=29bfuser88
                       *-volume
                            description: Windows NTFS volume
                            physical id: 1
                            bus info: scsi@2:0.0.0,1
                            logical name: /dev/sdc1
                            version: 3.1
                            serial: d629969b-bffb-7343-bbc1-3ec0fda6fc41
                            size: 232GiB
                            capacity: 232GiB
                            capabilities: primary ntfs initialized
                            configuration: clustersize=4096 created=2017-01-02 11:18:59 filesystem=ntfs label=WD Scorpio 250GB 5400 rpm modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-usb:2
                   description: Generic USB device
                   product: USB2.0-CRW
                   vendor: Generic
                   physical id: 6
                   bus info: usb@1:6
                   version: 39.60
                   serial: 20100201396000000
                   capabilities: usb-2.00
                   configuration: driver=rtsx_usb maxpower=500mA speed=480Mbit/s
              *-usb:3
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.13.0-19-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
              *-usb
                   description: Video
                   product: Intel(R) RealSense(TM) 3D Camera (Front F200)
                   vendor: Intel(R) RealSense(TM) 3D Camera (Front F200)
                   physical id: 3
                   bus info: usb@2:3
                   version: 27.80
                   serial: 042150653105
                   capabilities: usb-3.00
                   configuration: driver=uvcvideo maxpower=440mA speed=5000Mbit/s
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:d2230000-d2230fff
        *-generic:1
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:16 memory:d222f000-d222ffff
        *-generic:2
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:17 memory:d222e000-d222efff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:279 memory:d222d000-d222dfff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:276 memory:d2228000-d2229fff memory:d222c000-d222c0ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:d222b000-d222b7ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:c0000000-d00fffff
           *-display
                description: Display controller
                product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 81
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:278 memory:c0000000-cfffffff memory:d0000000-d003ffff ioport:e000(size=256) memory:d0040000-d005ffff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:d2100000-d21fffff
           *-network DISABLED
                description: Wireless interface
                product: Wireless 3160
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 83
                serial: 2c:6e:85:1a:8a:1a
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-19-generic firmware=17.608620.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:281 memory:d2100000-d2101fff
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:d2000000-d20fffff
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 07
                serial: 84:7b:eb:19:0e:b1
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:275 ioport:d000(size=256) memory:d2004000-d2004fff memory:d2000000-d2003fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory
             description: Memory controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: driver=intel_pmc_core latency=0
             resources: irq:0 memory:d2224000-d2227fff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:280 memory:d2220000-d2223fff memory:d2200000-d220ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d222a000-d222a0ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Crucial_CT256MX1
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MU01
             serial: 14340D00CB8D
             size: 238GiB (256GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=44a59517-8e21-4917-83eb-3d79cdab8055 logicalsectorsize=512 sectorsize=4096
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: cc30-2c7a
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI System Partition
           *-volume:1
                description: EFI partition
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot
                version: 1.0
                serial: a579adc9-1740-42d5-b06c-2c845de5ae34
                size: 488MiB
                capabilities: extended_attributes large_files ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2017-12-14 22:01:18 mount.fstype=ext2 mount.options=rw,relatime,block_validity,barrier,user_xattr,acl,stripe=4 mounted=2017-12-14 22:01:18 state=mounted
           *-volume:2
                description: LVM Physical Volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: RzV03E-jFeT-ZzSX-Uf0T-iUZb-l8qu-FMBNNL
                size: 237GiB
                capabilities: multi lvm2
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000LM024 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 0004
             serial: S314J90H236411
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=000242d7
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /mnt/DS
                version: 1.0
                serial: 1f4ecf47-efb0-431c-a3ce-152c9a548c42
                size: 931GiB
                capacity: 931GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2017-01-20 22:22:12 filesystem=ext4 label=DS lastmountpoint=/mnt/DS modified=2017-12-14 22:01:19 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-12-14 22:01:19 state=mounted
  *-battery
       product: DELL 78V9D62
       vendor: Panasonic
       physical id: 1
       version: 02/24/2016
       serial: 0892
       slot: Sys. Battery Bay
       capacity: 37290mWh
       configuration: voltage=14.8V
user@Hostname:~$ 

```

---

### Post by sccman on 2017-12-15
What is the output of:

```
sudo apt install --fix-broken
```

and

```
sudo dmesg | tail
```

---

### Post by accounts0 on 2017-12-16
> **sccman said:**
> What is the output of:

```
sudo apt install --fix-broken
```
```
[FONT=monospace][COLOR=#000000]$ sudo apt install --fix-broken[/COLOR]
[sudo] password for user:  
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
[/FONT]
```

> **sccman said:**
> ```
sudo dmesg | tail
```
```
$ sudo dmesg | tail
[ 1809.321925] audit: type=1400 audit(1513482079.878:188): apparmor="ALLOWED" operation="connect" profile="/usr/sbin/nmbd" pid=9395 comm="nmbd" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@2F746D702F65736574732E736F636B0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" peer="unconfined"
[ 1809.322859] audit: type=1400 audit(1513482079.879:189): apparmor="ALLOWED" operation="connect" profile="/usr/sbin/nmbd" pid=9395 comm="nmbd" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@2F746D702F65736574732E736F636B0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" peer="unconfined"
[ 1809.323559] audit: type=1400 audit(1513482079.879:190): apparmor="ALLOWED" operation="connect" profile="/usr/sbin/nmbd" pid=9395 comm="nmbd" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@2F746D702F65736574732E736F636B0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" peer="unconfined"
[ 1809.324408] audit: type=1400 audit(1513482079.880:191): apparmor="ALLOWED" operation="connect" profile="/usr/sbin/nmbd" pid=9395 comm="nmbd" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@2F746D702F65736574732E736F636B0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" peer="unconfined"
[ 1809.325199] audit: type=1400 audit(1513482079.881:192): apparmor="ALLOWED" operation="connect" profile="/usr/sbin/nmbd" pid=9395 comm="nmbd" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@2F746D702F65736574732E736F636B0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" peer="unconfined"
[ 1809.325701] audit: type=1400 audit(1513482079.882:193): apparmor="ALLOWED" operation="connect" profile="/usr/sbin/nmbd" pid=9395 comm="nmbd" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@2F746D702F65736574732E736F636B0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" peer="unconfined"
[ 1809.930374] audit: type=1400 audit(1513482080.486:194): apparmor="ALLOWED" operation="connect" profile="/usr/sbin/smbd" pid=9396 comm="smbd" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@2F746D702F65736574732E736F636B0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" peer="unconfined"
[ 1809.931198] audit: type=1400 audit(1513482080.487:195): apparmor="ALLOWED" operation="mknod" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/9396" pid=9396 comm="smbd" requested_mask="c" denied_mask="c" fsuid=0 ouid=0                                                                             
[ 1809.931210] audit: type=1400 audit(1513482080.487:196): apparmor="ALLOWED" operation="open" profile="/usr/sbin/smbd" name="/run/samba/msg.lock/9396" pid=9396 comm="smbd" requested_mask="wc" denied_mask="wc" fsuid=0 ouid=0                                                                            
[ 2041.789090] logitech-hidpp-device 0003:046D:4002.0004: HID++ 2.0 device connected. 

```

---

### Post by accounts0 on 2017-12-21
I dare say I may have come upon a solution. Haven't noticed the problem for maybe 2 days now after having made the following change in Chrome's settings.

I've set "Settings>Appearance>Use system title bar and borders" to "Off", & "Settings>Appearance>Themes" to "Classic".

So far so good. Will now consider this "Solved", & will revisit if the condition reverts.

---

