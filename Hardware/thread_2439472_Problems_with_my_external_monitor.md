---
title: "Problems with my external monitor"
date: 2020-03-28
forum: Hardware
---

### Post by blackers2 on 2020-03-28
Hello everyone, I'm here to tell you about my external monitor problem that I couldn't solve despite several tried solutions.
This problem exists since the installation of Ubuntu.
Disclaimer: I'm new to Linux and English is not my native language. If there are things that are not clear, please tell me.

I have a Razer Blade laptop with an external monitor attached. Hardware info at the end of the message.

Here are the symptoms:
No problems on the laptop screen. However, pixels on the monitor are blinking randomly. After a while, the monitor shuts down as if it's losing signal, and then turns on again after two seconds.
Here is a video, sorry for the quality but I can't do better with my phone.
[https://youtu.be/KS-hFLDEv0g](https://youtu.be/KS-hFLDEv0g)

You can see the pixels blinking on the black background, then the screen goes off and on again.

You'll immediately think it's a hardware problem but:
-Everything works perfectly with windows.
-I tried with another cable and another monitor, and I got the same problem.

Here's what I tried:

Every possible refresh rates with xrandr ;

options in /etc/default/grub: i915.modeset=1, nomodeset and others

various configuration files in /etc/X11/xorg.conf.d/

I've tried a lot of things and I don't remember everything. But nothing worked, or even improved the problem.

My temporary solution:

alternate between 50 and 60Hz with "xrandr --output DP-1 --mode 1920x1080 -r [frequency]" until the screen stabilizes.
After 3 or 4 tries, it stabilizes and I have no more problems. But as soon as it goes back to standby or I turn it off and on, the problem comes back and I have to redo my solution.

Here are some hardware infos :

uname -a
```
Linux RazerBlade 5.3.0-42-generic #34~18.04.1-Ubuntu SMP Fri Feb 28 13:42:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

sudo lshw
```
razerblade                  
    description: Ordinateur portable
    produit: Blade Stealth (RZ09-02393F31)
    fabriquant: Razer
    version: 4.06
    numéro de série: BY1751A44300178
    bits: 64 bits
    fonctionnalités: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=laptop family=1A586757 sku=RZ09-02393F31 uuid=48B128CF-07FE-4445-B6CD-97246C8E1AE2
  *-core
       description: Carte mère
       produit: Blade Stealth
       fabriquant: Razer
       identifiant matériel: 0
     *-firmware
          description: BIOS
          fabriquant: Razer
          identifiant matériel: 0
          version: 3.02
          date: 02/22/2018
          taille: 64KiB
          capacité: 15MiB
          fonctionnalités: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: Mémoire Système
          identifiant matériel: 25
          emplacement: Carte mère
          taille: 15GiB
          fonctionnalités: ecc
          configuration: errordetection=ecc
        *-bank:0
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2016-09-03 00:48+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2016-09-03 00:48+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719) 2133 MHz (0,5 ns) [vide]
             identifiant matériel: 0
             emplacement: ChannelA-DIMM0
             horloge: 2133MHz (0.5ns)
        *-bank:1
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2016-09-03 00:48+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2016-09-03 00:48+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719) [vide]
             identifiant matériel: 1
             emplacement: ChannelA-DIMM1
        *-bank:2
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2016-09-03 00:48+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2016-09-03 00:48+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719) 2133 MHz (0,5 ns) [vide]
             identifiant matériel: 2
             emplacement: ChannelB-DIMM0
             horloge: 2133MHz (0.5ns)
        *-bank:3
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2016-09-03 00:48+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2016-09-03 00:48+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2018-07-12 13:19+0000X-Generator: Launchpad (build 18719) [vide]
             identifiant matériel: 3
             emplacement: ChannelB-DIMM1
     *-cache:0
          description: L1 cache
          identifiant matériel: 2c
          emplacement: L1 Cache
          taille: 256KiB
          capacité: 256KiB
          fonctionnalités: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          identifiant matériel: 2d
          emplacement: L2 Cache
          taille: 1MiB
          capacité: 1MiB
          fonctionnalités: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          identifiant matériel: 2e
          emplacement: L3 Cache
          taille: 8MiB
          capacité: 8MiB
          fonctionnalités: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          produit: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
          fabriquant: Intel Corp.
          identifiant matériel: 2f
          information bus: cpu@0
          version: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
          emplacement: U3E1
          taille: 1800MHz
          capacité: 4005MHz
          bits: 64 bits
          horloge: 100MHz
          fonctionnalités: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          produit: Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
          fabriquant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 08
          bits: 32 bits
          horloge: 33MHz
          configuration: driver=skl_uncore
          ressources: irq:0
        *-display
             description: VGA compatible controller
             produit: UHD Graphics 620
             fabriquant: Intel Corporation
             identifiant matériel: 2
             information bus: pci@0000:00:02.0
             nom logique: /dev/fb0
             version: 07
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pciexpress msi pm vga_controller bus_master cap_list rom fb
             configuration: depth=32 driver=i915 latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
             ressources: mémoireE/S:2f0-2ef mémoireE/S:2f0-2ef irq:136 mémoire:2ffe000000-2ffeffffff mémoire:2fc0000000-2fcfffffff portE/S:f000(taille=64) mémoire:c0000-dffff
        *-usb
             description: USB controller
             produit: Sunrise Point-LP USB 3.0 xHCI Controller
             fabriquant: Intel Corporation
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             ressources: mémoireE/S:2f0-2ef irq:125 mémoire:2fff010000-2fff01ffff
           *-usbhost:0
                produit: xHCI Host Controller
                fabriquant: Linux 5.3.0-42-generic xhci-hcd
                identifiant matériel: 0
                information bus: usb@1
                nom logique: usb1
                version: 5.03
                fonctionnalités: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Vidéo
                   produit: USB Camera
                   fabriquant: 11918920-0079P402
                   identifiant matériel: 1
                   information bus: usb@1:1
                   version: 0.06
                   fonctionnalités: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: Périphérique audio
                   produit: UMC1820
                   fabriquant: BEHRINGER
                   identifiant matériel: 2
                   information bus: usb@1:2
                   version: 1.00
                   numéro de série: 76AD01FE
                   fonctionnalités: usb-2.00 audio-control
                   configuration: driver=snd-usb-audio speed=480Mbit/s
              *-usb:2
                   description: Interface sans fil Bluetooth
                   fabriquant: Atheros Communications, Inc.
                   identifiant matériel: 6
                   information bus: usb@1:6
                   version: 0.01
                   fonctionnalités: bluetooth usb-2.01
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:3
                   description: Concentrateur USB
                   produit: USB 2.0 Hub
                   fabriquant: Terminus Technology Inc.
                   identifiant matériel: 7
                   information bus: usb@1:7
                   version: 1.11
                   fonctionnalités: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Clavier
                      produit: USB Keyboard
                      fabriquant: Logitech
                      identifiant matériel: 1
                      information bus: usb@1:7.1
                      version: 87.00
                      fonctionnalités: usb-1.10
                      configuration: driver=usbhid maxpower=98mA speed=1Mbit/s
                 *-usb:1
                      description: Périphérique USB générique
                      produit: SAMSUNG_Android
                      fabriquant: SAMSUNG
                      identifiant matériel: 2
                      information bus: usb@1:7.2
                      version: 4.00
                      numéro de série: 42002029d2bc859b
                      fonctionnalités: usb-2.00
                      configuration: driver=usbfs maxpower=96mA speed=480Mbit/s
              *-usb:4
                   description: Clavier
                   produit: Razer Blade Stealth
                   fabriquant: Razer
                   identifiant matériel: 8
                   information bus: usb@1:8
                   version: 2.00
                   fonctionnalités: usb-2.00
                   configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
              *-usb:5
                   description: Périphérique d'interface homme/machine
                   produit: Touchscreen
                   fabriquant: ELAN
                   identifiant matériel: 9
                   information bus: usb@1:9
                   version: 57.04
                   fonctionnalités: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                produit: xHCI Host Controller
                fabriquant: Linux 5.3.0-42-generic xhci-hcd
                identifiant matériel: 1
                information bus: usb@2
                nom logique: usb2
                version: 5.03
                fonctionnalités: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:0
             description: Signal processing controller
             produit: Sunrise Point-LP Thermal subsystem
             fabriquant: Intel Corporation
             identifiant matériel: 14.2
             information bus: pci@0000:00:14.2
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             ressources: mémoireE/S:2f0-2ef irq:18 mémoire:2fff026000-2fff026fff
        *-generic:1
             description: Signal processing controller
             produit: Sunrise Point-LP Serial IO I2C Controller #0
             fabriquant: Intel Corporation
             identifiant matériel: 15
             information bus: pci@0000:00:15.0
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             ressources: irq:16 mémoire:de505000-de505fff
        *-generic:2
             description: Signal processing controller
             produit: Sunrise Point-LP Serial IO I2C Controller #1
             fabriquant: Intel Corporation
             identifiant matériel: 15.1
             information bus: pci@0000:00:15.1
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             ressources: irq:17 mémoire:de504000-de504fff
        *-communication
             description: Communication controller
             produit: Sunrise Point-LP CSME HECI #1
             fabriquant: Intel Corporation
             identifiant matériel: 16
             information bus: pci@0000:00:16.0
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             ressources: mémoireE/S:2f0-2ef irq:135 mémoire:2fff025000-2fff025fff
        *-pci:0
             description: PCI bridge
             produit: Sunrise Point-LP PCI Express Root Port #3
             fabriquant: Intel Corporation
             identifiant matériel: 1c
             information bus: pci@0000:00:1c.0
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:122 mémoire:de200000-de3fffff
           *-network
                description: Interface réseau sans fil
                produit: QCA6174 802.11ac Wireless Network Adapter
                fabriquant: Qualcomm Atheros
                identifiant matériel: 0
                information bus: pci@0000:01:00.0
                nom logique: wlp1s0
                version: 32
                numéro de série: 9c:b6:d0:20:3b:a7
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=5.3.0-42-generic firmware=WLAN.RM.4.4.1-00079-QCARMSWPZ-1 ip=192.168.1.60 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                ressources: irq:138 mémoire:de200000-de3fffff
        *-pci:1
             description: PCI bridge
             produit: Sunrise Point-LP PCI Express Root Port #5
             fabriquant: Intel Corporation
             identifiant matériel: 1c.4
             information bus: pci@0000:00:1c.4
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:123 portE/S:2000(taille=4096) mémoire:c8000000-de0fffff portE/S:2fd0000000(taille=570425344)
        *-pci:2
             description: PCI bridge
             produit: Sunrise Point-LP PCI Express Root Port #9
             fabriquant: Intel Corporation
             identifiant matériel: 1d
             information bus: pci@0000:00:1d.0
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:124 mémoire:de400000-de4fffff
           *-storage
                description: Non-Volatile memory controller
                produit: NVMe SSD Controller SM981/PM981
                fabriquant: Samsung Electronics Co Ltd
                identifiant matériel: 0
                information bus: pci@0000:3b:00.0
                version: 00
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                ressources: irq:16 mémoire:de400000-de403fff
        *-isa
             description: ISA bridge
             produit: Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E
             fabriquant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 21
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa bus_master
             configuration: latency=0
        *-memory NON-RÉCLAMÉ
             description: Memory controller
             produit: Sunrise Point-LP PMC
             fabriquant: Intel Corporation
             identifiant matériel: 1f.2
             information bus: pci@0000:00:1f.2
             version: 21
             bits: 32 bits
             horloge: 33MHz (30.3ns)
             configuration: latency=0
             ressources: mémoire:de500000-de503fff
        *-multimedia
             description: Audio device
             produit: Sunrise Point-LP HD Audio
             fabriquant: Intel Corporation
             identifiant matériel: 1f.3
             information bus: pci@0000:00:1f.3
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             ressources: mémoireE/S:2f0-2ef mémoireE/S:2f0-2ef irq:137 mémoire:2fff020000-2fff023fff mémoire:2fff000000-2fff00ffff
        *-serial NON-RÉCLAMÉ
             description: SMBus
             produit: Sunrise Point-LP SMBus
             fabriquant: Intel Corporation
             identifiant matériel: 1f.4
             information bus: pci@0000:00:1f.4
             version: 21
             bits: 64 bits
             horloge: 33MHz
             configuration: latency=0
             ressources: mémoireE/S:2f0-2ef mémoire:2fff024000-2fff0240ff portE/S:f040(taille=32)
  *-power NON-RÉCLAMÉ
       identifiant matériel: 1
  *-network:0 DÉSACTIVÉ
       description: Ethernet interface
       identifiant matériel: 2
       nom logique: virbr0-nic
       numéro de série: 52:54:00:cc:8d:78
       taille: 10Mbit/s
       fonctionnalités: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
  *-network:1
       description: Ethernet interface
       identifiant matériel: 3
       nom logique: virbr0
       numéro de série: 52:54:00:cc:8d:78
       fonctionnalités: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=no multicast=yes

```

xrandr --prop
```
Screen 0: minimum 320 x 200, current 3520 x 1080, maximum 16384 x 16384
eDP-1 connected 1600x900+0+180 (normal left inverted right x axis y axis) 294mm x 165mm
    _MUTTER_PRESENTATION_OUTPUT: 0 
    EDID: 
        00ffffffffffff004d10931400000000
        121b0104a51d11780ede50a3544c9926
        0f505400000001010101010101010101
        010101010101cd9180a0c00834703020
        350026a5100000180000001000000000
        00000000000000000000000000100000
        000000000000000000000000000000fc
        004c513133335a314a5732360020001e
    scaling mode: Full aspect 
        supported: Full, Center, Full aspect
    max bpc: 12 
        range: (6, 12)
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    non-desktop: 0 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad
   3200x1800     59.98 +  59.96    59.94  
   2880x1620     59.96    59.97  
   2560x1600     59.99    59.97  
   2560x1440     59.99    59.99    59.96    59.95  
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   2048x1152     59.99    59.98    59.90    59.91  
   1920x1200     59.88    59.95  
   1920x1080     60.01    59.97    59.96    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99*   59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 connected primary 1920x1080+1600+0 (normal left inverted right x axis y axis) 543mm x 305mm
    _MUTTER_PRESENTATION_OUTPUT: 0 
    EDID: 
        00ffffffffffff002264411af7010000
        1614010380361e78eacf55a2564c9d23
        125054bfef80d1c0b300a94095009040
        81808140714f1a3680a070381f403020
        35001f312100001b000000fc00484632
        35370a20202020202020000000fd0038
        4b18500e000a202020202020000000ff
        00303232524733514130303530330165
        020322f14d9f1413121e160190040507
        030e230907078301000067030c001000
        28de8c0ad08a20e02d10103e96001f31
        21000018011d8018711c1620582c2500
        1f312100009e023a801871382d40582c
        45001f312100001e011d80d0721c1620
        102c25801f312100009e023a80d07238
        2d40102c45801f312100001e00000031
    Content Protection: Undesired 
        supported: Undesired, Desired, Enabled
    max bpc: 12 
        range: (6, 12)
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    non-desktop: 0 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad
   1920x1080     59.93 +  60.00    50.00*   59.94  
   1920x1080i    60.00    50.00    59.94  
   1600x1200     60.00  
   1680x1050     59.88  
   1400x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1440x576      50.00  
   1024x768      75.03    70.07    60.00  
   1440x480      60.00    59.94  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP-2 disconnected (normal left inverted right x axis y axis)
    Content Protection: Undesired 
        supported: Undesired, Desired, Enabled
    max bpc: 12 
        range: (6, 12)
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    non-desktop: 0 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad
HDMI-1 disconnected (normal left inverted right x axis y axis)
    Content Protection: Undesired 
        supported: Undesired, Desired, Enabled
    max bpc: 12 
        range: (8, 12)
    content type: No Data 
        supported: No Data, Graphics, Photo, Cinema, Game
    Colorspace: Default 
        supported: Default, SMPTE_170M_YCC, BT709_YCC, XVYCC_601, XVYCC_709, SYCC_601, opYCC_601, opRGB, BT2020_CYCC, BT2020_RGB, BT2020_YCC, DCI-P3_RGB_D65, DCI-P3_RGB_Theater
    aspect ratio: Automatic 
        supported: Automatic, 4:3, 16:9
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
    non-desktop: 0 
        range: (0, 1)
    link-status: Good 
        supported: Good, Bad

```
One strange thing is that my monitor is detected in xrandr as DisplayPort but in reality its connected via HDMI.


inxi -G
```
Graphics:  Card: Intel UHD Graphics 620
           Display Server: x11 (X.Org 1.19.6 ) driver: i915 Resolution: 1600x900@59.99hz, 1920x1080@50.00hz
           OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2)
           version: 4.6 Mesa 20.1.0-devel (git-4897e70 2020-03-25 bionic-oibaf-ppa)

```


Thanks for reading.

---

