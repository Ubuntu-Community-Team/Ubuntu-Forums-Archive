---
title: "AFT PRO 77U USB drives not working"
date: 2018-05-19
forum: Hardware
---

### Post by Welly Wu on 2018-05-19
I installed Ubuntu 18.04.0 64 bit LTS GNU/Linux on my mid-2017 AVA Direct gaming desktop PC. I have an ATech PRO 77U which features four Super Speed USB 3.1 Type-A ports and I can't mount a USB drive when I plug in a USB thumb drive or hard disk drive. Please help.

```
wellywu@AVADirect:~$ sudo lsusb
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 004: ID 03f0:c611 Hewlett-Packard 
Bus 005 Device 003: ID 147e:1001 Upek TCS5B Fingerprint sensor
Bus 005 Device 002: ID 046d:0a5c Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0bda:0401 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 11b0:3114 ATECH FLASH TECHNOLOGY 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 22d9:0416  
Bus 001 Device 002: ID 0bda:5401 Realtek Semiconductor Corp. RTL 8153 USB 3.0 hub with gigabit ethernet
Bus 001 Device 007: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 005: ID 046d:c32b Logitech, Inc. 
Bus 001 Device 004: ID 046d:c332 Logitech, Inc. 
Bus 001 Device 012: ID 174c:5106 ASMedia Technology Inc. ASM1051 SATA 3Gb/s bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
wellywu@AVADirect:~$ sudo lshw
avadirect                   
    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-3.1 dmi-3.1 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=E05F652F-5524-E711-9BDD-6045CB9E8AD6
  *-core
       description: Motherboard
       product: CROSSHAIR VI HERO
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
       serial: 170499331101979
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 6004
          date: 04/17/2018
          size: 64KiB
          capacity: 15MiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
```

```
*-cpu
          description: CPU
          product: AMD Ryzen 5 1600X Six-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 32
          bus info: cpu@0
          version: AMD Ryzen 5 1600X Six-Core Processor
          serial: Unknown
          slot: AM4
          size: 1915MHz
          capacity: 4100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb hw_pstate sme vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr ibpb arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov succor smca cpufreq
          configuration: cores=6 enabledcores=6 threads=12
```

```
*-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.15.0-20-generic xhci-hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 4.15
                   capabilities: usb-3.10
                   configuration: driver=hub slots=8 speed=10000Mbit/s
                 *-usb:0
                      description: Mass storage device
                      product: PRO77U SS
                      vendor: AFT
                      physical id: 3
                      bus info: usb@2:3
                      logical name: scsi9
                      version: 1.17
                      serial: 201506301317
                      capabilities: usb-3.00 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=800mA speed=5000Mbit/s
                    *-disk:0
                         description: SCSI Disk
                         product: PRO77U SS     -0
                         vendor: AFT
                         physical id: 0.0.0
                         bus info: scsi@9:0.0.0
                         logical name: /dev/sdd
                         version: 1.00
                         serial: 2012062914345300
                         capabilities: removable
                         configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
                       *-medium
                            physical id: 0
                            logical name: /dev/sdd
                    *-disk:1
                         description: SCSI Disk
                         product: PRO77U SS     -1
                         vendor: AFT
                         physical id: 0.0.1
                         bus info: scsi@9:0.0.1
                         logical name: /dev/sde
                         version: 1.00
                         serial: 2012062914345300
                         capabilities: removable
                         configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
                       *-medium
                            physical id: 0
                            logical name: /dev/sde
                    *-disk:2
                         description: SCSI Disk
                         product: PRO77U SS     -2
                         vendor: AFT
                         physical id: 0.0.2
                         bus info: scsi@9:0.0.2
                         logical name: /dev/sdf
                         version: 1.00
                         serial: 2012062914345300
                         capabilities: removable
                         configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
                       *-medium
                            physical id: 0
                            logical name: /dev/sdf
                    *-disk:3
                         description: SCSI Disk
                         product: PRO77U SS     -3
                         vendor: AFT
                         physical id: 0.0.3
                         bus info: scsi@9:0.0.3
                         logical name: /dev/sdg
                         version: 1.00
                         serial: 2012062914345300
                         capabilities: removable
                         configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
                       *-medium
                            physical id: 0
                            logical name: /dev/sdg
```

Please help if you can. Thanks.

---

### Post by Welly Wu on 2018-05-19
Upon closer investigation, it appears that FAT32 and NTFS non-encrypted USB drives do mount correctly using my AFT PRO-77U. However, a majority of my LUKS encrypted USB drives are not detected and they do not show up in GNOME Disks Utility and they do not mount with the exception of my "Penguin" 4GB USB 3.0 thumb drive which does when connected to the AFT PRO-77U. When I plug in these same LUKS encrypted USB drives to my two gaming notebook PCs running the same version of Ubuntu, they mount automatically. Is there any way to pinpoint this problem in order to troubleshoot it further? What kind of technical information can I add to this thread to be of greater help?

---

