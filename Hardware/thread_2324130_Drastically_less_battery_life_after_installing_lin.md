---
title: "Drastically less battery life after installing linux"
date: 2016-05-11
forum: Hardware
---

### Post by Matthew_Jonat on 2016-05-11
Hey guys,

My apologies if this is an issue that has been mentioned before but I have done some research already and have not found much and what I have found doesnt seem to be really working...anyways, here goes.

So I have had my laptop over a year now and for most of that time it has solely been a windows machine but I decided it would be fun to use linux for web development so I installed it and I do like it. I currently dual boot. Linux =  Coding and Windows = Gaming.

This isn't my first laptop and if anything I have noticed that the battery life is one of the first things to go but I was actually very impressed with this laptop as the battery life basically stayed the same for the whole year...dropping slightly but impressively for a PC...not by that much. So then I start using linux not really thinking that this would be an issue and then after a couple months of having linux installed and using it fairly regularly my battery life on a full charge went down from around 2.5 hours to maybe an hour. It might not be Linux doing this but its a bit of an odd coincidence if it isn't. 

At a guess windows has the correct drivers (most likely written by HP and put into windows before selling the machine) and does some smart power routing or something that linux isnt aware of as its probably quite custom to this machine.

My machine is a hp pavilion. I can give more information but at this point I am not really sure what would be needed to investigate this further.

Many thanks!

Matt

---

### Post by james208 on 2016-05-11
Linux can use a fair bit more battery life than Windows. On my HP laptop, I'd get around 7-8 hours on Windows and now I get 5-6 on Ubuntu. One thing that helps me is putting it into suspend when ever you aren't actively using it, and obviously turning down brightness and off Bluetooth (unless you happen to use Bluetooth, I never do)

---

### Post by weatherman2 on 2016-05-11
"Linux" doesn't use more battery power than any other operating system, if configured correctly.

The issue can be that the correct Linux drivers are not installed or are not configured correctly, often the graphics driver.  (If the manufacturer provides an "Additional Driver," it's usually a good idea to use it or at least try it.)

Unfortunately, some laptops work better in Linux than others.  It somewhat depends on how well the laptop manufacturer and/or the component manufacturers have chosen to support Linux.  I have had good luck with Dell and Acer laptops, perhaps because they sell some versions of their laptops with Linux installed, so of course they would make sure there is Linux driver support for the hardware.

If your laptop is not well supported in Linux, troubleshooting the issue can be time consuming.  The first thing to try is a web search for your laptop's exact model number (or family) and "Ubuntu" or "Linux" and see if others have noticed issues even on other distros besides Ubuntu.  You'll obviously have better luck for laptops that have been around longer with more time for others to have posted about past issues.  Anyway, if you're lucky, someone else may have already troubleshooted the issue for you and/or can offer some tips.  If not, your best bet here is to post more specifics are your laptop (the output of "sudo lshw" might be a good start).

One test I like to do of laptop power consumption is to put the laptop on a "watt" meter and see how much power it consumes at idle, then, if possible, do the same test in both Linux and Windows.  (Note that the screen consumes a lot of power, so try to have it on at the same brightness in both cases, so you can do a good A-B comparison.)  The two laptops I now use regularly consume the same idle power under WIndows that they do in Ubuntu.  That's good enough for me.  (Not to say Ubuntu's power management is just as good when you are actually using the battery - more that all the drivers are installed correctly, most likely.)

I sometimes refurbish old laptops, and if I find Linux just doesn't work well on them, I sometimes won't waste much time trying - I just put Windows back on them and get rid of them.  (One old Toshiba laptop I ran into about a year ago consumed about 28 watts at idle in Windows but about 38 watts at idle in the latest Ubuntu.  I could find no obvious extra drivers to install or tweaks, so I put Windows back on it.)  For my own laptops, I always make sure ahead of time that anything I buy has good Linux compatibility.  Some laptops just aren't.  Blame the manufacturers.

---

### Post by anon24 on 2016-05-11
Join the club, I went from my battery lasting about an hour to two hours in Windows to lasting fifteen minutes or less in Ubuntu. It sucks hard.

---

### Post by Linuxisfast on 2016-05-11
If you have nvidia card, install driver via hardware driver applet and then shut the card off in nvidia-settings. Install TLP from software center and your battery life will be as good as Windows. My ThinkPad and ASUS laptops have similar battery life as in Windows.

---

### Post by Matthew_Jonat on 2016-05-11
Thanks guys useful info here although I think I might have miss-said something....its not that in linux specifically my battery does not last as long. Its that after installing and using linux a lot my battery life has drastically gone down weather im in windows or linux....the overall time is less.


I guess what I really wanted to know was how to correctly configure the drivers...


Someone asked for the output of sudo lshw so here it is:


```

description: Computer
    width: 64 bits
    capabilities: smbios-2.8 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7913MiB
     *-cpu
          product: Intel(R) Core(TM) i5-4288U CPU @ 2.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 3099MHz
          capacity: 3100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Haswell-ULT Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:b2000000-b23fffff memory:a0000000-afffffff ioport:6000(size=64)
        *-multimedia:0
             description: Audio device
             product: Haswell-ULT HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:b2610000-b2613fff
        *-usb:0
             description: USB controller
             product: 8 Series USB xHCI HC
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:42 memory:b2600000-b260ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-22-generic xhci-hcd
                physical id: 0
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-22-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=9 speed=480Mbit/s
              *-usb
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Sunplus Innovation Technology Inc.
                   physical id: 6
                   bus info: usb@2:6
                   version: 0.14
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
        *-communication
             description: Communication controller
             product: 8 Series HECI #0
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:46 memory:b2618000-b261801f
        *-multimedia:1
             description: Audio device
             product: 8 Series HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:47 memory:b2614000-b2617fff
        *-pci:0
             description: PCI bridge
             product: 8 Series PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: 8 Series PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:5000(size=4096) memory:b1000000-b1ffffff ioport:b0000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: 8 Series PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:4000(size=4096) memory:b2500000-b25fffff
           *-network
                description: Wireless interface
                product: RTL8723BE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlo1
                version: 00
                serial: 74:29:af:92:ce:f3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8723be driverversion=4.4.0-22-generic firmware=N/A ip=192.168.1.119 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 ioport:4000(size=256) memory:b2500000-b2503fff
        *-pci:3
             description: PCI bridge
             product: 8 Series PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:3000(size=4096) memory:b2400000-b24fffff
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eno1
                version: 08
                serial: 38:63:bb:a6:4d:75
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:44 ioport:3000(size=256) memory:b2404000-b2404fff memory:b2400000-b2403fff
        *-usb:1
             description: USB controller
             product: 8 Series USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:b261c000-b261c3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb:0
                      description: Video
                      product: HP Truevision HD
                      vendor: Chicony Electronics Co., Ltd.
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 69.39
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
                 *-usb:1
                      description: Bluetooth wireless interface
                      product: Bluetooth Radio
                      vendor: Realtek
                      physical id: 7
                      bus info: usb@1:1.7
                      version: 2.00
                      serial: 00e04c000001
                      capabilities: bluetooth usb-2.10
                      configuration: driver=btusb maxpower=500mA speed=12Mbit/s
        *-isa
             description: ISA bridge
             product: 8 Series LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:6088(size=8) ioport:6094(size=4) ioport:6080(size=8) ioport:6090(size=4) ioport:6060(size=32) memory:b261b000-b261b7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b2619000-b26190ff ioport:6040(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1500LM006 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0001
             serial: S35UJ9BFB08538
             size: 1397GiB (1500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=9731e7ff-5179-4715-8a42-4802cf4f9c65 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: f4ce-ac64
                size: 648MiB
                capacity: 649MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-08-26 19:25:22 filesystem=ntfs label=WINRE modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: aa53-3d6d
                size: 245MiB
                capacity: 259MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: e9d83fdd-3775-43ab-97b4-917750aa6a6d
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: fabebee1-7b49-374f-8753-81c6201fb56e
                size: 1281GiB
                capacity: 1281GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-08-26 15:32:19 filesystem=ntfs label=Windows name=Basic data partition state=clean
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: 5c68-e8bb
                size: 911MiB
                capacity: 912MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2015-12-11 13:01:43 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: a0bd7608-a004-eb46-b093-b714ee219416
                size: 21GiB
                capacity: 21GiB
                capabilities: precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-08-26 19:42:00 filesystem=ntfs label=RECOVERY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:6
                description: EXT4 volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /
                version: 1.0
                serial: 287e5c10-1c8c-4c09-b924-36445b087ce8
                size: 85GiB
                capacity: 85GiB
                capabilities: boot journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-02-03 14:47:14 filesystem=ext4 lastmountpoint=/ modified=2016-05-12 10:13:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-05-12 10:13:32 state=mounted
           *-volume:7
                description: Linux swap volume
                vendor: Linux
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                version: 1
                serial: 23ac181b-5e8d-4255-b942-95c68706255f
                size: 8120MiB
                capacity: 8121MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW  GUB0N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: UB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```


I havent tried what someone else mentioned about googling my laptop plus serial so im off too do that now...if ii find anything useful i will report back here.


Thanks again guys!

---

### Post by weatherman2 on 2016-05-12
> **Matthew_Jonat said:**
> Thanks guys useful info here although I think I might have miss-said something....its not that in linux specifically my battery does not last as long. Its that after installing and using linux a lot my battery life has drastically gone down weather im in windows or linux....the overall time is less.


I guess what I really wanted to know was how to correctly configure the drivers...



Well, then that is different.  Laptop batteries don't last forever; they all gradually hold less charge over time.  It could be yours simply needs to be replaced and that the reduced life in any operating system has nothing at all to do with Linux.

Your laptop is what - about three years old?  That's about average for mid-life.  Your battery might really be going downhill at that age, especially if you discharge and re-charge it every day.  (I always keep my laptops plugged in when I have AC power and don't run off the battery every day.)

I'd check eBay for a replacement battery - even generic (new) replacements can work well and not cost much.

---

### Post by Matthew_Jonat on 2016-05-12
What you say is entirely possible but I think its a bit much of a coincidence that the battery was doing amazingly well until i install and start using the laptop with linux regularly and only then the battery starts to crap out?

I generally would have my laptop plugged in but its just on the odd long journey i would maybe get the laptop out to watch a movie or something...

My theory is that there is a driver installed on windows that says to the hardware...if the battery is full, don't put any power through the battery anymore and just give it straight to the system...the battery is "cut out of the loop" whereas in linux there isnt a driver doing this so the power is constantly going through the battery, using it more and therefore degrading it.

The only thing that draws me to this conclusion is that I have had several laptops before and pretty much used them all in the same way when it comes to this and the battery normally would have degraded a lot more than mine had up until the point I installed linux...

---

### Post by weatherman2 on 2016-05-12
Actually, the BIOS or firmware controls the charging of the battery, when to stop charging, etc.  The operating system has nothing to do with it.  There is no driver I'm aware of that would change that on a conventional laptop.  The OS can monitor the charge rate and inform the user but that's about it.

Driver issues would cause excessive power use (and therefore drain a battery's charge faster), not cause issues with charging itself.

---

### Post by Matthew_Jonat on 2016-05-12
Well if that is correct then I guess I am barking up the wrong tree and would be wrong about everything haha...

Unless anybody has anything to say to the contrary i guess that solves the issue...

Cheers!

---

