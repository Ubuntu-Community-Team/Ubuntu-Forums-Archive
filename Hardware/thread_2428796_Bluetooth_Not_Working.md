---
title: "Bluetooth Not Working"
date: 2019-10-09
forum: Hardware
---

### Post by daniel-patrick on 2019-10-09
I have Ubuntu 18.04.3 LTS installed on an HP 250 G7 laptop, however the Bluetooth won't switch on.

**No Bluetooth Found**
Plug in a dongle to use Bluetooth.

How can I solve this issue please?

---

### Post by SeijiSensei on 2019-10-09
Check that it's not disabled in the BIOS and that you did not inadvertently turn if off via an Fn-key combination.

---

### Post by MartyBuntu on 2019-10-09
Does the laptop have a physical BT/Wifi switch?

---

### Post by daniel-patrick on 2019-10-10
[COLOR=#000000]"Check that it's not disabled in the BIOS and that you did not inadvertently turn if off via an Fn-key combination."
It's enabled from the BIOS.

[/COLOR][COLOR=#000000]"Does the laptop have a physical BT/Wifi switch?"
No, it's doesn't.[/COLOR]

---

### Post by SeijiSensei on 2019-10-11
According to [http://h10032.www1.hp.com/ctg/Manual/c06207912](http://h10032.www1.hp.com/ctg/Manual/c06207912) it has an "airplane mode" key combination. Maybe that's the culprit?

In Ubuntu, open a terminal and enter "sudo lshw".  Do you see a similar entry to this one?  (This is a Lenovo so your results will likely be different.)

```

                 *-usb
                      description: Bluetooth wireless interface
                      product: Broadcom Bluetooth 2.1 Device
                      vendor: Broadcom Corp
                      physical id: 6
                      bus info: usb@1:1.6
                      version: 4.72
                      serial: C01885A549A0
                      capabilities: bluetooth usb-2.00
                      configuration: driver=btusb speed=12Mbit/s

```

---

### Post by jimmyrus on 2019-10-14
> **daniel-patrick said:**
> [COLOR=#000000]"Check that it's not disabled in the BIOS and that you did not inadvertently turn if off via an Fn-key combination."
It's enabled from the BIOS.

[/COLOR][COLOR=#000000]"Does the laptop have a physical BT/Wifi switch?"
No, it's doesn't.[/COLOR]
Can you get to a terminal and run "sudo rfkill list", and post the output?

---

### Post by daniel-patrick on 2019-10-15
After running the command **sudo lshw**

```
root@MLT-0093:~# sudo lshw
    mlt-0093                    
    description: Notebook
    product: HP 250 G7 Notebook PC (6BP85EA#ABU)
    vendor: HP
    version: Type1ProductConfigId
    serial: 
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=103C_5336AN HP 200 sku=6BP85EA#ABU uuid=096A3181-9E08-11E9-8102-80E82CC6EA7E
  *-core
       description: Motherboard
       product: 8532
       vendor: HP
       physical id: 0
       version: 70.30
       serial: PHVVLB2MYCHBBT
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.19
          date: 05/06/2019
          size: 128KiB
          capacity: 12MiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-8265U CPU @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-8265U CPU @ 1.60GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1385MHz
          capacity: 3900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2400 MHz (0.4 ns)
             product: M471A1K43DB1-CTD
             vendor: Samsung
             physical id: 0
             serial: 32A493D8
             slot: Bottom-Slot 1(left)
             size: 8GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR Synchronous [empty]
             physical id: 1
             slot: Bottom-Slot 2(right)
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:129 memory:a0000000-a0ffffff memory:80000000-9fffffff ioport:5000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:a1410000-a1417fff
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:a1420000-a1420fff
        *-generic:2
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 30
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:16 memory:a1421000-a1421fff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 30
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:125 memory:a1400000-a140ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.0.0-31-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb
                   description: Video
                   product: HP Webcam
                   vendor: Quanta
                   physical id: 5
                   bus info: usb@1:5
                   version: 0.14
                   serial: 0x0001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.0.0-31-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 30
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:a141c000-a141dfff memory:a1422000-a1422fff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 30
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:138 memory:a1423000-a1423fff
        *-storage
             description: RAID bus controller
             product: 82801 Mobile SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 30
             width: 32 bits
             clock: 66MHz
             capabilities: storage msix pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:16 memory:a141e000-a141ffff memory:a1427000-a14270ff ioport:5080(size=8) ioport:5088(size=4) ioport:5060(size=32) memory:a1426000-a14267ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:4000(size=4096) memory:a1300000-a13fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eno1
                version: 15
                serial: 80:e8:2c:c6:ea:7e
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:16 ioport:4000(size=256) memory:a1304000-a1304fff memory:a1300000-a1303fff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:3000(size=4096) memory:a1200000-a12fffff
           *-network
                description: Wireless interface
                product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlo1
                version: 00
                serial: 80:91:33:46:d8:e5
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8821ce ip=172.23.12.71 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:139 ioport:3000(size=256) memory:a1200000-a120ffff
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.4
             bus info: pci@0000:00:1d.4
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:a1100000-a11fffff
           *-storage
                description: Non-Volatile memory controller
                product: Toshiba America Info Systems
                vendor: Toshiba America Info Systems
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pciexpress pm msi msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:a1100000-a1103fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 30
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:140 memory:a1418000-a141bfff memory:a1000000-a10fffff
        *-serial:0 UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 30
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a1424000-a14240ff ioport:5040(size=32)
        *-serial:1 UNCLAIMED
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
             resources: memory:fe010000-fe010fff
     *-scsi
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW GUE1N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: UE00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: HT03041
       vendor: 333-27-33-A
       physical id: 1
       version: 0
       serial: 02264 05/26/2019
       slot: Primary
       capacity: 41050mWh
       configuration: voltage=11.3V
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: OEM Define 3
       capacity: 75mWh



```

The Airplane Mode is **F12**, however to no avail.


And, this is the output after running the command **sudo rfkill list**

```

root@MLT-0093:~# sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by jimmyrus on 2019-10-15
Doesn't look like you have bluetooth at all, or the hardware is dead or turned off. Not showing up under a hw list, or on rfkill. Should at least see the device as blocked even if its not working. Try this in a terminal and reboot.
```
[FONT=Consolas]sudo echo 'AutoEnable=true' >/etc/bluetooth/main.conf && /etc/init.d/bluetooth restart
```
[/FONT][FONT=inherit]Does your usb dongle work bluetooth? Also try running "dmesg | egrep -i 'blue|firm|net'" and see what you get, or redir the command into a file and look in it. Maybe device firmware file isnt loading, especially if you have broadcomm hardware. Did you consider loading version 19 instead of 18.04? Might fix things.[COLOR=#242729][FONT=Arial][/FONT][/COLOR]
[/FONT]

---

### Post by daniel-patrick on 2019-10-16
> **jimmyrus said:**
> Doesn't look like you have bluetooth at all, or the hardware is dead or turned off. Not showing up under a hw list, or on rfkill. Should at least see the device as blocked even if its not working. Try this in a terminal and reboot.
```
[FONT=Consolas]sudo echo 'AutoEnable=true' >/etc/bluetooth/main.conf && /etc/init.d/bluetooth restart[/FONT]
```[FONT=Consolas]
[/FONT][FONT=inherit]Does your usb dongle work bluetooth? Also try running "dmesg | egrep -i 'blue|firm|net'" and see what you get, or redir the command into a file and look in it. Maybe device firmware file isnt loading, especially if you have broadcomm hardware. Did you consider loading version 19 instead of 18.04? Might fix things.
[/FONT]

```

user@MLT-0093:~$ dmesg | egrep -i 'blue|firm|net
> 

```

I ran the command **dmesg | egrep -i 'blue|firm|net **, but nothing happened.


```
root@MLT-0093:~# sudo echo 'AutoEnable=true' >/etc/bluetooth/main.conf && /etc/init.d/bluetooth restart
[ ok ] Restarting bluetooth (via systemctl): bluetooth.service

```

Still didn't work. I would like to get it working on 18.04, that's why I didn't try it on version 19.

---

### Post by jimmyrus on 2019-10-16
> **daniel-patrick said:**
> ```

user@MLT-0093:~$ dmesg | egrep -i 'blue|firm|net
> 

```

I ran the command **dmesg | egrep -i 'blue|firm|net **, but nothing happened.


```
root@MLT-0093:~# sudo echo 'AutoEnable=true' >/etc/bluetooth/main.conf && /etc/init.d/bluetooth restart
[ ok ] Restarting bluetooth (via systemctl): bluetooth.service

```

Still didn't work. I would like to get it working on 18.04, that's why I didn't try it on version 19.
Ok and I asked if your blutooth dongle worked so does it? Because everything you posted says your bluetooth hardware is dead or turned off since none of these commands are finding anything at all bluetooth related. Going to 19 may make things work since itll have updated drivers that'd be the first thing I try.

---

### Post by daniel-patrick on 2019-10-16
> **jimmyrus said:**
> Ok and I asked if your blutooth dongle worked so does it? Because everything you posted says your bluetooth hardware is dead or turned off since none of these commands are finding anything at all bluetooth related. Going to 19 may make things work since itll have updated drivers that'd be the first thing I try.

Yes, the Bluetooth dongle works fine because I've tried it on another laptop with Ubuntu version 18.04 and it works fine.

The only difference is the laptop I tried it on that works is an HP 250 G6 laptop. So, for some reason it doesn't work on an HP 250 G7 laptop. 

I find this to be very strange.

---

### Post by jimmyrus on 2019-10-16
> **daniel-patrick said:**
> Yes, the Bluetooth dongle works fine because I've tried it on another laptop with Ubuntu version 18.04 and it works fine.

The only difference is the laptop I tried it on that works is an HP 250 G6 laptop. So, for some reason it doesn't work on an HP 250 G7 laptop. 

I find this to be very strange.
wait are you saying that the bluetooth dongle doesn't work? thought your internal bluetooth wasnt working and that you had to use the dongle instead. did you try a different usb port?

---

### Post by jimmyrus on 2019-10-16
yea, but rfkill list doesn't show any bluetooth devices, just his wifi.

---

### Post by daniel-patrick on 2019-10-17
> **jimmyrus said:**
> wait are you saying that the bluetooth dongle doesn't work? thought your internal bluetooth wasnt working and that you had to use the dongle instead. did you try a different usb port?

The Bluetooth mouse works fine. It's something from Ubuntu or the drivers that are incorrect.

What I'm saying is that I tried it on two different laptops. On one model it works and the other it doesn't. Both are of the HP brand.

_**Laptop Models**_

HP 250 **G6** with Ubuntu 18.14 installed - Works
HP 250 **G7** with Ubuntu 18.14 installed - Doesn't work

---

