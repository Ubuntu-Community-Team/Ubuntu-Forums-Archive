---
title: "please help me get touchpad multitouch gestures back 16.04.5"
date: 2018-08-11
forum: Hardware
---

### Post by teklife on 2018-08-11
i love keyboard shortcuts and gestures; sometime during my older install of 16.04, i noticed that the multitouch gestures i used to use were suddenly missing, 3 finger tap and hold for switcher, 4 finger scroll for show/hide launcher, etc. 

i tried to google for this but cannot find anything, i have followed links from ubuntu wiki's own page for this ([https://wiki.ubuntu.com/Multitouch/TouchpadSupport](https://wiki.ubuntu.com/Multitouch/TouchpadSupport)) but still no solution, so i have done several reinstalls, hoping to get this functionality back, and still nothing, so i did a complete wipe and fresh install, not even using the /home partition, and still, nothing.

i find it hard to believe that this is something that was removed during one of the 16.04 point release updates, it just seems impossible, but then again we have GNOME always removing stuff on us, so, is this something that has been removed? 

if not i want it back, but how? 

i'm not hardcore geek enough to know, but i have tried everything else i could think of before coming here to seek help, and hopefully it's something stupidly simple, but still, why has this very useful(to me) functionality gone away?

these lovely gestures used to work flawlessly on my lenovo yoga 700 11sk with a Synaptics TM2714-002 touchpad.

thanks y'all.

---

### Post by mörgæs on 2018-08-12
Have you only been using 16.04? If a bug or regression has been introduced here then chances are very slim that it will be fixed. 

Does 18.04 have better support?

---

### Post by teklife on 2018-08-12
i have installed budgie, mate and ubuntu 18.04 all were extremely slow on my decently spec'd computer, and all sorts of other bugs(graphics was a total disaster). i did install unity on every install of 18.04 (fresh installs) and it was so painfully slow that even if the multitouch gestures worked well, it would otherwise be 'bang your head against the wall un-usable' and not at all worth it, so i have reluctantly had to reinstall 16.04 and the speed is snappy, and everything feels extremely polished and comfortable and easy to use, with the exception of the multitouch gestures which i am trying to figure out why do they no longer work. i really don't want to have to install 16.04.1 or earlier just to have the gestures, but i may have to if i am to find where did this bug start, but i am hoping some guru here just knows what to check.

---

### Post by mörgæs on 2018-08-13
If people should have a chance troubleshooting your 18.04 (I hope it means 18.04.1) installation best is to begin with a complete hardware description. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags.

---

### Post by teklife on 2018-08-14
thank you kindly for your reply, i did input that code into the terminal but the result merely said "USB" in CAPS. 

as for the release, as per the title of this post, i am running a freshly installed 16.04.5 on [COLOR=#000000] lenovo yoga 700 11sk with a Synaptics TM2714-002 touchpad. i hope that is of some use to you.[/COLOR]

---

### Post by mörgæs on 2018-08-14
> **teklife said:**
> thank you kindly for your reply, i did input that code into the terminal but the result merely said "USB" in CAPS. 


Did you notice that my suggestion mentioned lshw.txt?

> **teklife said:**
> 
as for the release, as per the title of this post, i am running a freshly installed 16.04.5 on [COLOR=#000000] lenovo yoga 700 11sk with a Synaptics TM2714-002 touchpad. i hope that is of some use to you.[/COLOR]

It's not, because I don't have any specific knowledge on the topic. I neither use Budgie, Mate nor Ubuntu (only X/Lubuntu) and I only use 18.04. 

What I do have is general experience in isolating, diagnosing, avoiding and possibly solving errors in a GNU/Linux system. If you want an exact fix and the fix has to be based upon 16.04.5 then it's better to wait for another poster.

---

### Post by teklife on 2018-08-17
> **mörgæs said:**
> Did you notice that my suggestion mentioned lshw.txt?



yes i did, well, maybe i'm misunderstanding something, at least what i did was copied and pasted into the terminal this command exactly, "sudo lshw -sanitize > lshw.txt" and the only output was "USB" and for just a fraction of a second before disappearing, the text didn't stay so i could copy or screenshoot it for you.

thanks for your help anyway friendly Lubuntu user ;)):P.

---

### Post by mörgæs on 2018-08-18
The command created the file lshw.txt.
Please post it in CODE tags.

---

### Post by teklife on 2018-08-18
oh ok, i didn't know where did the file get saved to, but i found it in my home directory eventually.

and without further ado:
```
computer    description: Notebook
    product: 80QE (LENOVO_MT_80QE_BU_idea_FM_Lenovo YOGA 700-11ISK)
    vendor: LENOVO
    version: Lenovo YOGA 700-11ISK
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=IDEAPAD frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_80QE_BU_idea_FM_Lenovo YOGA 700-11ISK uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Lenovo YOGA 700-
       vendor: LENOVO
       physical id: 0
       version: SDK0J40709 WIN
       serial: [REMOVED]
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: DDCN20WW(V1.04)
          date: 09/21/2015
          size: 128KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) m5-6Y54 CPU @ 1.10GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) m5-6Y54 CPU @ 1.10GHz
          serial: [REMOVED]
          slot: U3E1
          size: 2622MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 8
             slot: L3 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: 5
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM Synchronous 1600 MHz (0.6 ns)
             product: K4E6E304EE-EGCF
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM Synchronous 1600 MHz (0.6 ns)
             product: K4E6E304EE-EGCF
             vendor: Samsung
             physical id: 2
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: [empty]
             physical id: 3
             slot: ChannelB-DIMM1
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
             resources: irq:124 memory:a0000000-a0ffffff memory:90000000-9fffffff ioport:3000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 08
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:a1120000-a1127fff
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
             resources: irq:122 memory:a1100000-a110ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.15.0-29-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB OPTICAL MOUSE
                   vendor: PIXART
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: Video
                   product: Lenovo EasyCamera
                   vendor: SunplusIT Inc
                   physical id: 3
                   bus info: usb@1:3
                   version: 36.01
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: USB hub
                   product: USB 2.0 Hub
                   vendor: Terminus Technology Inc.
                   physical id: 5
                   bus info: usb@1:5
                   version: 1.11
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Human interface device
                      product: Touchscreen
                      vendor: ELAN
                      physical id: 1
                      bus info: usb@1:5.1
                      version: 10.13
                      capabilities: usb-2.01
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Bluetooth wireless interface
                      vendor: Intel Corp.
                      physical id: 2
                      bus info: usb@1:5.2
                      version: 0.01
                      capabilities: bluetooth usb-2.00
                      configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:3
                   description: Generic USB device
                   product: USB2.0-CRW
                   vendor: Generic
                   physical id: 7
                   bus info: usb@1:7
                   version: 39.60
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=rtsx_usb maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.15.0-29-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:1
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:a1132000-a1132fff
        *-generic:2
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
             resources: irq:16 memory:a1133000-a1133fff
        *-generic:3
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
             resources: irq:17 memory:a1134000-a1134fff
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
             resources: irq:127 memory:a1135000-a1135fff
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
             resources: irq:123 memory:a1130000-a1131fff memory:a1138000-a11380ff ioport:3080(size=8) ioport:3088(size=4) ioport:3060(size=32) memory:a1136000-a11367ff
        *-pci
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
             resources: irq:17 memory:a1000000-a10fffff
           *-network
                description: Wireless interface
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 99
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-29-generic firmware=29.1044073957.0 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:128 memory:a1000000-a1001fff
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
        *-memory UNCLAIMED
             description: Memory controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:a112c000-a112ffff
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
             resources: irq:142 memory:a1128000-a112bfff memory:a1110000-a111ffff
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
             resources: memory:a1137000-a11370ff ioport:3040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: RTHMB256VBM4MWDL
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 9
             serial: [REMOVED]
             size: 238GiB (256GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=c61c51b1-882c-4452-9d76-dfc254a7f3f0 logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 255MiB
                capacity: 259MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat label=SYSTEM_DRV mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:1
                description: reserved partition
                vendor: Windows
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                serial: [REMOVED]
                capacity: 15MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: [REMOVED]
                size: 58GiB
                capacity: 58GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2018-07-28 11:46:35 filesystem=ntfs label=Windows name=Basic data partition state=clean
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: [REMOVED]
                size: 3399MiB
                capacity: 3429MiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2016-09-28 11:34:23 filesystem=ntfs label=LENOVO name=Basic data partition state=clean
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@1:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: [REMOVED]
                size: 995MiB
                capacity: 999MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-09-28 11:14:10 filesystem=ntfs label=WINRE_DRV modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@1:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: [REMOVED]
                size: 18GiB
                capacity: 18GiB
                capabilities: boot ntfs initialized
                configuration: clustersize=4096 created=2016-09-28 11:14:11 filesystem=ntfs label=LENOVO_PART modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:6
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 7
                bus info: scsi@1:0.0.0,7
                logical name: /dev/sda7
                version: FAT32
                serial: [REMOVED]
                size: 967MiB
                capacity: 999MiB
                capabilities: precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat label=LRS_ESP name=Basic data partition
           *-volume:7
                description: EXT4 volume
                vendor: Linux
                physical id: 8
                bus info: scsi@1:0.0.0,8
                logical name: /dev/sda8
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 21GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2018-08-12 00:15:06 filesystem=ext4 lastmountpoint=/ modified=2018-08-12 01:30:27 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-08-12 01:30:27 state=mounted
           *-volume:8
                description: Linux swap volume
                vendor: Linux
                physical id: 9
                bus info: scsi@1:0.0.0,9
                logical name: /dev/sda9
                version: 1
                serial: [REMOVED]
                size: 7998MiB
                capacity: 7999MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:9
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: a
                bus info: scsi@1:0.0.0,10
                logical name: /dev/sda10
                logical name: /media/ss/A8A1-8DA9
                version: FAT32
                serial: [REMOVED]
                size: 49GiB
                capacity: 49GiB
                capabilities: fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
           *-volume:10
                description: EXT4 volume
                vendor: Linux
                physical id: b
                bus info: scsi@1:0.0.0,11
                logical name: /dev/sda11
                logical name: /media/ss/03abcf4c-68af-49d3-b5f4-7adb1ae6e81c
                version: 1.0
                serial: [REMOVED]
                size: 38GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-10-30 13:07:01 filesystem=ext4 lastmountpoint=/media/ss/03abcf4c-68af-49d3-b5f4-7adb1ae6e81c modified=2018-08-12 23:13:00 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2018-08-12 23:13:00 state=mounted
           *-volume:11
                description: EXT4 volume
                vendor: Linux
                physical id: c
                bus info: scsi@1:0.0.0,12
                logical name: /dev/sda12
                logical name: /home
                version: 1.0
                serial: [REMOVED]
                size: 39GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2018-08-06 01:34:09 filesystem=ext4 lastmountpoint=/home modified=2018-08-12 01:30:27 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2018-08-12 01:30:27 state=mounted
  *-battery
       description: Zinc Air Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 08/08/2010
       serial: [REMOVED]
       slot: Fake
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: [REMOVED]
       capacity: 75mWh
```

---

### Post by mörgæs on 2018-08-19
Now a week has passed and the thread has not attracted posts from people with specific knowledge, and as mentioned above I don't have either.

I hope somebody can use the contents of the thread including the lshw output to get your 16.04.5 install fixed, if you really want to carry on with this one. It seems like 16.04.1 would have solved the problem (just remember to update all packages after install). 

Lshw shows that your hardware is Skylake based. Googling yields many posts describing useful boot options for Skylake which come in handy if you give 18.04.1 a try again. Lshw also shows that several updates to the BIOS have been released since the one you are using but I don't know if they are important to your problem or not.

Good luck with whichever path you decide to follow.

---

### Post by teklife on 2018-08-21
ok thanks for your help. no amount of googling has led to any answer yet, i don't think most people use gestures and keyboard shortcuts as much as i do, oh well, life goes on.

---

