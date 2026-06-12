---
title: "cardreader does not recignize sdcard"
date: 2014-10-25
forum: Hardware
---

### Post by Ubi_one_2014 on 2014-10-25
upon inserting mu 16Gb sdcard into the cardreader results to nothing

no reaction of kde ( kubuntu )
the card does work, bacause i tested it in an XBMC device, and that device gave an 16Gb extra memory card as storage

i want to format the sdcard.

my specifications:

Kubuntu 14.04 latest updates
kernel kubuntu:~# uname -r3.14.22-031422-generic

lshw:
```
lshw
kubuntu                   
    description: Portablecomputer
    product: Inspiron 5721 (Inspiron 5721)
    vendor: Dell Inc.
    version: A08
    serial: 75Y90X1
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=portable family=103C_5335KV sku=Inspiron 5721 uuid=44454C4C-3500-1059-8039-B7C04F305831
  *-core
       description: Moederbord
       product: 0YTJR9
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: .75Y90X1.CN1296634I0039.
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A08
          date: 05/20/2013
          size: 128KiB
          capacity: 4544KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-3227U CPU @ 1.90GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-3227U CPU @ 1.90GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1900MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx f16c lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: b
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: 8
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-memory
          description: System Memory
          physical id: 23
          slot: Systeem- of moederbord
          size: 6GiB
        *-bank:0
             description: SODIMM DDR3 Synchroon 1600 MHz (0,6 ns)
             product: HMT325S6CFR8C-PB
             vendor: Hynix/Hyundai
             physical id: 0
             serial: 0F7E1FBA
             slot: JDIMM1
             size: 2GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchroon 1600 MHz (0,6 ns)
             product: HMT351S6EFR8A-PB
             vendor: Hynix/Hyundai
             physical id: 1
             serial: 297DB16E
             slot: JDIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:3000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:40 memory:c0600000-c060ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:44 memory:c0614000-c061400f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:c0619000-c06193ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:c0610000-c0613fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) ioport:c0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 05
                serial: 74:86:7a:0c:e4:a5
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.178.12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:41 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:c0500000-c05fffff
           *-network DISABLED
                description: Wireless interface
                product: Centrino Wireless-N 2230
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: c4
                serial: 60:6c:66:3d:95:eb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.14.22-031422-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:45 memory:c0500000-c0501fff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:c0618000-c06183ff
        *-isa
             description: ISA bridge
             product: HM76 Express Chipset LPC Controller
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
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:3088(size=8) ioport:3094(size=4) ioport:3080(size=8) ioport:3090(size=4) ioport:3060(size=32) memory:c0617000-c06177ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0615000-c06150ff ioport:3040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000LM024 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2AR2
             serial: S2WZJA0D313320
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=28c482b1-d372-4fd7-a57e-b34efabac2db sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: 9a29-95b9
                size: 486MiB
                capacity: 486MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 6d247bb2-b728-47b4-bb7c-4bdd7c6947f9
                size: 925GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-11-08 13:31:30 filesystem=ext4 lastmountpoint=/ modified=2014-10-18 19:12:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-10-18 19:12:05 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: e9843d50-07a2-4f4d-af7e-e2dc69742573
                size: 6011MiB
                capacity: 6012MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW DU-8A5HH
             vendor: PLDS
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: SD11
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@3:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=00091129
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: e59cd024-5c07-4dab-9511-9ff383fbe0b4
                size: 931GiB
                capacity: 931GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-10-18 11:31:03 filesystem=ext4 modified=2014-10-18 11:31:29 mounted=2014-10-18 11:31:17 state=clean
  *-battery
       description: Lithium-ion Battery
       product: DELL 4DMNG31N
       vendor: Simplo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 60000mWh
       configuration: voltage=11,1V



```

---

### Post by J_Me on 2014-10-25
Put the SDcard in the slot and post the output of
```
mount
```

---

### Post by Ubi_one_2014 on 2014-10-26
$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)

---

### Post by Dennis N on 2014-10-26
If the card uses the exfat filesystem, you may need to install a couple of extra packages:

Install **exfat-utils** and **exfat-fuse** packages from the Ubuntu repos.
```
sudo apt-get install exfat-utils exfat-fuse
```

Reboot your computer.

---

### Post by Ubi_one_2014 on 2014-10-26
i got it solved by upgrading to kernel 3.17.1

@kubuntu:~$ uname -r
3.17.1-031701-generic

an other extra benefit, is that my mouse behaves better than under kernel 3.14.22

thanks for all assitstance

Ubuntu is the best distro

---

