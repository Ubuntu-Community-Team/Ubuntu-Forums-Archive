---
title: "ieGeek KVM-Switch goes black after POST"
date: 2016-05-15
forum: Hardware
---

### Post by Werscannt on 2016-05-15
I got an older PC recently and installed Lubuntu 16.04 LTS on it. The plan is to use it alongside a Win 7 Laptop. For the sake of convience I wanted to hook them both on the same display+keyboard and mouse. So I bought the ieGeek 4-Port KVM-Switch (VGA). With the laptop it works like a charm but the PC doesn't.
On boot everything works fine. I can access BIOS, read the POST. After that the screen goes black and stays that way. Not even this loading screen is visible.
[IMG]https://2.bp.blogspot.com/-MHW21Ud-vlo/Vxz-g70brBI/AAAAAAAAFME/c3pIII7Q7JEKHhAoq_F8_DbXe3_FwNMMwCLcB/s1600/02%2BFail%2Bsafe%2Bboot%2Bscreen.png[/IMG]

But the screen is still powered.
Some seconds later is enters power saving mode due to no signal.
I tried several combinations of cables and monitors. They all work with the laptop but not with the PC. I even added an USB-Hub with own power supply to give more power to the switch which gets his power over USB only.
By connecting the PC directly to the screen, mouse and keyboard it works. If I then pull the Cables and insert the switch into the setup it keeps working fine.
I need help to figure out how to get it to work properly.

---

### Post by DuckHook on 2016-05-15
This problem is a common one with KVM swtiches. The problem is not your signal strength, it is the fact that many KVM switches either corrupt the EDID data stream or won't handshake the monitor with the computer at all. Windows queries for EDID in a proprietary way, and KVM switch manufacturers make sure that their switches work with Windows. However, they have little incentive to adhere to open standards, so they don't. The result is what you are seeing: KVM switches that "behave" with Windows, but "misbehave" with Linux. This is not the fault of Linux, but of KVM manufacturers who don't adhere to standards.

The following workaround sometimes works, sometimes doesn't. Your mileage will vary.

**CAUTION**
Monkeying around with video boot parameters will occasionally result in a black or scrambled screen. In the worst case, it can also harm your video card or your monitor. Do not proceed unless you are willing to take this chance. Make sure all important data is backed up before proceeding.

You can try forcing video output to your PC's VGA port:

[LIST=1]
[*]First, take out the KVM switch, hook your monitor directly to PC, and post back to this thread the results of:```
ls -la /sys/class/drm/
```
[*]The device name we are interested in is the part after "card0-". We are looking for something that reads "VGA-n" where "n" is a number. You must note the *exact* device name. For example, sometimes it's VGA-1 and sometimes it's VGA1 (without the dash). Case is also important.
[*]Do:```
sudo nano /etc/default/grub
```
[*]Find the line that has:```
"quiet splash"
```...and add```
video=VGA-n:<your_resolution>e
```...so that it looks like:```
"quiet splash video=VGA-n:<your_resolution>e"
```...Replace "VGA-n" with the actual device name that we established in point 2 above, and replace <your_resolution> with the native resolution of your monitor. Do *not* include the <> brackets. The trailing "e" is critical. That is what tells the kernel to "enable" this port whether it detects any connected monitor or not. An example would look as follows:```
"quiet splash video=VGA-1:1024x768e"
```
[*]Do:```
sudo update-grub
```
[*]Reboot
[/LIST]
If everything still works, then shutdown and plug in the KVM. If it works, please mark this thread *solved*. If not, then obviously more fish need to be fried.

---

### Post by Werscannt on 2016-05-16
Command didn't work.
```
ls -la /sys/class/drm/
ls: Zugriff auf '/sys/class/drm/' nicht möglich: Datei oder Verzeichnis nicht gefunden
```

```
ls -la /sys/class/drm
ls: Zugriff auf '/sys/class/drm' nicht möglich: Datei oder Verzeichnis nicht gefunden
```

Maybe this will help you:

```
ls -la /sys/class/
insgesamt 0
drwxr-xr-x 56 root root 0 Mai 16 10:57 .
dr-xr-xr-x 13 root root 0 Mai 16 10:51 ..
drwxr-xr-x  2 root root 0 Mai 16 10:51 ata_device
drwxr-xr-x  2 root root 0 Mai 16 10:51 ata_link
drwxr-xr-x  2 root root 0 Mai 16 10:51 ata_port
drwxr-xr-x  2 root root 0 Mai 16 10:51 backlight
drwxr-xr-x  2 root root 0 Mai 16 10:51 bdi
drwxr-xr-x  2 root root 0 Mai 16 10:51 block
drwxr-xr-x  2 root root 0 Mai 16 10:51 bsg
drwxr-xr-x  2 root root 0 Mai 16 10:51 devcoredump
drwxr-xr-x  2 root root 0 Mai 16 10:51 devfreq
drwxr-xr-x  2 root root 0 Mai 16 10:51 devfreq-event
drwxr-xr-x  2 root root 0 Mai 16 10:51 dma
drwxr-xr-x  2 root root 0 Mai 16 10:51 dmi
drwxr-xr-x  2 root root 0 Mai 16 10:51 extcon
drwxr-xr-x  2 root root 0 Mai 16 10:51 firmware
drwxr-xr-x  2 root root 0 Mai 16 10:51 gpio
drwxr-xr-x  2 root root 0 Mai 16 10:51 graphics
drwxr-xr-x  2 root root 0 Mai 16 10:51 hidraw
drwxr-xr-x  2 root root 0 Mai 16 10:51 hwmon
drwxr-xr-x  2 root root 0 Mai 16 10:51 i2c-adapter
drwxr-xr-x  2 root root 0 Mai 16 10:51 i2c-dev
drwxr-xr-x  2 root root 0 Mai 16 10:51 input
drwxr-xr-x  2 root root 0 Mai 16 10:51 iommu
drwxr-xr-x  2 root root 0 Mai 16 10:51 leds
drwxr-xr-x  2 root root 0 Mai 16 10:51 mdio_bus
drwxr-xr-x  2 root root 0 Mai 16 10:51 mem
drwxr-xr-x  2 root root 0 Mai 16 10:51 misc
drwxr-xr-x  2 root root 0 Mai 16 10:51 mmc_host
drwxr-xr-x  2 root root 0 Mai 16 10:51 nd
drwxr-xr-x  2 root root 0 Mai 16 10:51 net
drwxr-xr-x  2 root root 0 Mai 16 10:51 pci_bus
drwxr-xr-x  2 root root 0 Mai 16 10:51 phy
drwxr-xr-x  2 root root 0 Mai 16 10:51 powercap
drwxr-xr-x  2 root root 0 Mai 16 10:51 power_supply
drwxr-xr-x  2 root root 0 Mai 16 10:51 ppdev
drwxr-xr-x  2 root root 0 Mai 16 10:51 ppp
drwxr-xr-x  2 root root 0 Mai 16 10:51 printer
drwxr-xr-x  2 root root 0 Mai 16 10:51 pwm
drwxr-xr-x  2 root root 0 Mai 16 10:51 rapidio_port
drwxr-xr-x  2 root root 0 Mai 16 10:51 regulator
drwxr-xr-x  2 root root 0 Mai 16 10:51 rfkill
drwxr-xr-x  2 root root 0 Mai 16 10:51 rtc
drwxr-xr-x  2 root root 0 Mai 16 10:51 scsi_device
drwxr-xr-x  2 root root 0 Mai 16 10:51 scsi_disk
drwxr-xr-x  2 root root 0 Mai 16 10:51 scsi_generic
drwxr-xr-x  2 root root 0 Mai 16 10:51 scsi_host
drwxr-xr-x  2 root root 0 Mai 16 10:51 sound
drwxr-xr-x  2 root root 0 Mai 16 10:51 spi_master
drwxr-xr-x  2 root root 0 Mai 16 10:51 thermal
drwxr-xr-x  2 root root 0 Mai 16 10:51 tpm
drwxr-xr-x  2 root root 0 Mai 16 10:51 tty
drwxr-xr-x  2 root root 0 Mai 16 10:51 vc
drwxr-xr-x  2 root root 0 Mai 16 10:51 virtio-ports
drwxr-xr-x  2 root root 0 Mai 16 10:51 vtconsole
drwxr-xr-x  2 root root 0 Mai 16 10:51 watchdog
```

**Edited for clarity**

...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by DuckHook on 2016-05-16
> **Werscannt said:**
> Command didn't work.:confused:

This is highly unusual! Yours is the first install I've ever seen that is missing those system files. Did you get rid of the KVM and hook the monitor directly to your PC before running the command? Make sure that you actually boot up with the monitor directly connected. Also, for curiosity, try:```
xrandr
```Proceed with my previous instructions anyway using "VGA-1" and your native resolution and see if it works.

How many VGA ports does your card have?

---

### Post by Werscannt on 2016-05-16
I'll try in a minute. At the moment, the PC is connected directly to the monitor.

The result of xrandr:


```
 xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 3344 x 2508
VGA-1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050     59.95*+
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08  


```


Shall I create a report with the System Profiler and Benchmark?

---

### Post by DuckHook on 2016-05-16
I am worried about your install. It makes no sense to have no /sys/class/drm/ directory. I've never seen it before and I have worked on dozens if not hundreds of machines.

In any case, *xrandr* detects a *VGA-1* connection at 1680x1050 resolution, although *xrandr* is sometimes unreliable in reporting proper device names. Your entry should be:```
"quiet splash video=VGA-1:1680x1050e"
```

Don't need benchmark but system profile is always informative.```
sudo lshw -sanitize -numeric
```

---

### Post by Werscannt on 2016-05-17
I did as you said earlier.
My 
```
sudo nano /etc/default/grub
```
now reads
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=VGA-1:1680x1050e"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)


```

It works fine when connected directly to the monitor. The setup with the switch is sadly as in my opening post.

The result of
```
sudo lshw -sanitize -numeric
```
is
```

computer                  
    Beschreibung: Computer
    Breite: 64 bits
    Fähigkeiten: smbios-2.3 vsyscall32
  *-core
       Beschreibung: Motherboard
       Physische ID: 0
     *-memory
          Beschreibung: Systemspeicher
          Physische ID: 0
          Größe: 1935MiB
     *-cpu
          Produkt: AMD Sempron(tm) Processor 3200+
          Hersteller: Advanced Micro Devices [AMD]
          Physische ID: 1
          Bus-Informationen: cpu@0
          Größe: 1GHz
          Kapazität: 1800MHz
          Breite: 64 bits
          Fähigkeiten: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm extapic cr8_legacy 3dnowprefetch vmmcall cpufreq
     *-pci:0
          Beschreibung: Host bridge
          Produkt: K8M800 Host Bridge [1106:204]
          Hersteller: VIA Technologies, Inc. [1106]
          Physische ID: 100
          Bus-Informationen: pci@0000:00:00.0
          Version: 00
          Breite: 32 bits
          Takt: 66MHz
          Konfiguration: driver=agpgart-amd64 latency=8
          Ressourcen: irq:0 memory:e8000000-efffffff
        *-pci
             Beschreibung: PCI bridge
             Produkt: VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South] [1106:B188]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: 1
             Bus-Informationen: pci@0000:00:01.0
             Version: 00
             Breite: 32 bits
             Takt: 66MHz
             Fähigkeiten: pci pm normal_decode bus_master cap_list
             Ressourcen: memory:f4000000-f5ffffff memory:f0000000-f3ffffff
           *-display UNGEFORDERT
                Beschreibung: VGA compatible controller
                Produkt: K8M800/K8N800/K8N800A [S3 UniChrome Pro] [1106:3108]
                Hersteller: VIA Technologies, Inc. [1106]
                Physische ID: 0
                Bus-Informationen: pci@0000:01:00.0
                Version: 01
                Breite: 32 bits
                Takt: 66MHz
                Fähigkeiten: pm agp agp-3.0 vga_controller bus_master cap_list
                Konfiguration: latency=32 mingnt=2
                Ressourcen: memory:f0000000-f3ffffff memory:f4000000-f4ffffff memory:f5000000-f500ffff
        *-ide:0
             Beschreibung: IDE interface
             Produkt: VIA VT6420 SATA RAID Controller [1106:3149]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: f
             Bus-Informationen: pci@0000:00:0f.0
             Version: 80
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: ide pm bus_master cap_list
             Konfiguration: driver=sata_via latency=32
             Ressourcen: irq:20 ioport:de00(Größe=8) ioport:e400(Größe=4) ioport:e500(Größe=8) ioport:dc00(Größe=4) ioport:dd00(Größe=16) ioport:d000(Größe=256)
        *-ide:1
             Beschreibung: IDE interface
             Produkt: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:571]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: f.1
             Bus-Informationen: pci@0000:00:0f.1
             Version: 06
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: ide pm bus_master cap_list
             Konfiguration: driver=pata_via latency=32
             Ressourcen: irq:20 ioport:1f0(Größe=8) ioport:3f6 ioport:170(Größe=8) ioport:376 ioport:df00(Größe=16)
        *-usb:0
             Beschreibung: USB controller
             Produkt: VT82xx/62xx UHCI USB 1.1 Controller [1106:3038]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: 10
             Bus-Informationen: pci@0000:00:10.0
             Version: 81
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=32
             Ressourcen: irq:21 ioport:e000(Größe=32)
           *-usbhost
                Produkt: UHCI Host Controller [1D6B:1]
                Hersteller: Linux 4.4.0-22-generic uhci_hcd [1D6B]
                Physische ID: 1
                Bus-Informationen: usb@2
                Logischer Name: usb2
                Version: 4.04
                Fähigkeiten: usb-1.10
                Konfiguration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             Beschreibung: USB controller
             Produkt: VT82xx/62xx UHCI USB 1.1 Controller [1106:3038]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: 10.1
             Bus-Informationen: pci@0000:00:10.1
             Version: 81
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=32
             Ressourcen: irq:21 ioport:e100(Größe=32)
           *-usbhost
                Produkt: UHCI Host Controller [1D6B:1]
                Hersteller: Linux 4.4.0-22-generic uhci_hcd [1D6B]
                Physische ID: 1
                Bus-Informationen: usb@3
                Logischer Name: usb3
                Version: 4.04
                Fähigkeiten: usb-1.10
                Konfiguration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             Beschreibung: USB controller
             Produkt: VT82xx/62xx UHCI USB 1.1 Controller [1106:3038]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: 10.2
             Bus-Informationen: pci@0000:00:10.2
             Version: 81
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=32
             Ressourcen: irq:21 ioport:e200(Größe=32)
           *-usbhost
                Produkt: UHCI Host Controller [1D6B:1]
                Hersteller: Linux 4.4.0-22-generic uhci_hcd [1D6B]
                Physische ID: 1
                Bus-Informationen: usb@4
                Logischer Name: usb4
                Version: 4.04
                Fähigkeiten: usb-1.10
                Konfiguration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             Beschreibung: USB controller
             Produkt: VT82xx/62xx UHCI USB 1.1 Controller [1106:3038]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: 10.3
             Bus-Informationen: pci@0000:00:10.3
             Version: 81
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm uhci bus_master cap_list
             Konfiguration: driver=uhci_hcd latency=32
             Ressourcen: irq:21 ioport:e300(Größe=32)
           *-usbhost
                Produkt: UHCI Host Controller [1D6B:1]
                Hersteller: Linux 4.4.0-22-generic uhci_hcd [1D6B]
                Physische ID: 1
                Bus-Informationen: usb@5
                Logischer Name: usb5
                Version: 4.04
                Fähigkeiten: usb-1.10
                Konfiguration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             Beschreibung: USB controller
             Produkt: USB 2.0 [1106:3104]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: 10.4
             Bus-Informationen: pci@0000:00:10.4
             Version: 86
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm ehci bus_master cap_list
             Konfiguration: driver=ehci-pci latency=32
             Ressourcen: irq:21 memory:f6000000-f60000ff
           *-usbhost
                Produkt: EHCI Host Controller [1D6B:2]
                Hersteller: Linux 4.4.0-22-generic ehci_hcd [1D6B]
                Physische ID: 1
                Bus-Informationen: usb@1
                Logischer Name: usb1
                Version: 4.04
                Fähigkeiten: usb-2.00
                Konfiguration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   Beschreibung: USB-Hub
                   Produkt: USB 2.0 Hub [1A40:101]
                   Hersteller: Terminus Technology Inc. [1A40]
                   Physische ID: 1
                   Bus-Informationen: usb@1:1
                   Version: 1.11
                   Fähigkeiten: usb-2.00
                   Konfiguration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      Beschreibung: Tastatur
                      Produkt: Wired Keyboard 600 [45E:7F8]
                      Hersteller: Microsoft [45E]
                      Physische ID: 1
                      Bus-Informationen: usb@1:1.1
                      Version: 3.00
                      Fähigkeiten: usb-2.00
                      Konfiguration: driver=usbhid maxpower=100mA speed=1Mbit/s
                 *-usb:1
                      Beschreibung: Maus
                      Produkt: USB-PS/2 Optical Mouse [46D:C051]
                      Hersteller: Logitech [46D]
                      Physische ID: 3
                      Bus-Informationen: usb@1:1.3
                      Version: 30.00
                      Fähigkeiten: usb-2.00
                      Konfiguration: driver=usbhid maxpower=98mA speed=1Mbit/s
        *-isa
             Beschreibung: ISA bridge
             Produkt: VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: 11
             Bus-Informationen: pci@0000:00:11.0
             Version: 00
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: isa pm bus_master cap_list
             Konfiguration: latency=0
        *-multimedia
             Beschreibung: Multimedia audio controller
             Produkt: VT8233/A/8235/8237 AC97 Audio Controller [1106:3059]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: 11.5
             Bus-Informationen: pci@0000:00:11.5
             Version: 60
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm cap_list
             Konfiguration: driver=snd_via82xx latency=0
             Ressourcen: irq:22 ioport:d400(Größe=256)
        *-network
             Beschreibung: Ethernet interface
             Produkt: VT6102/VT6103 [Rhine-II] [1106:3065]
             Hersteller: VIA Technologies, Inc. [1106]
             Physische ID: 12
             Bus-Informationen: pci@0000:00:12.0
             Logischer Name: enp0s18
             Version: 78
             Seriennummer: [REMOVED]
             Größe: 100Mbit/s
             Kapazität: 100Mbit/s
             Breite: 32 bits
             Takt: 33MHz
             Fähigkeiten: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             Konfiguration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             Ressourcen: irq:23 ioport:d800(Größe=256) memory:f6001000-f60010ff
     *-pci:1
          Beschreibung: Host bridge
          Produkt: K8M800 Host Bridge [1106:1204]
          Hersteller: VIA Technologies, Inc. [1106]
          Physische ID: 101
          Bus-Informationen: pci@0000:00:00.1
          Version: 00
          Breite: 32 bits
          Takt: 33MHz
     *-pci:2
          Beschreibung: Host bridge
          Produkt: K8M800 Host Bridge [1106:2204]
          Hersteller: VIA Technologies, Inc. [1106]
          Physische ID: 102
          Bus-Informationen: pci@0000:00:00.2
          Version: 00
          Breite: 32 bits
          Takt: 33MHz
     *-pci:3
          Beschreibung: Host bridge
          Produkt: K8M800 Host Bridge [1106:3204]
          Hersteller: VIA Technologies, Inc. [1106]
          Physische ID: 103
          Bus-Informationen: pci@0000:00:00.3
          Version: 00
          Breite: 32 bits
          Takt: 33MHz
     *-pci:4
          Beschreibung: Host bridge
          Produkt: K8M800 Host Bridge [1106:4204]
          Hersteller: VIA Technologies, Inc. [1106]
          Physische ID: 104
          Bus-Informationen: pci@0000:00:00.4
          Version: 00
          Breite: 32 bits
          Takt: 33MHz
     *-pci:5
          Beschreibung: Host bridge
          Produkt: K8M800 Host Bridge [1106:7204]
          Hersteller: VIA Technologies, Inc. [1106]
          Physische ID: 105
          Bus-Informationen: pci@0000:00:00.7
          Version: 00
          Breite: 32 bits
          Takt: 33MHz
     *-pci:6
          Beschreibung: Host bridge
          Produkt: K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
          Hersteller: Advanced Micro Devices, Inc. [AMD] [1022]
          Physische ID: 106
          Bus-Informationen: pci@0000:00:18.0
          Version: 00
          Breite: 32 bits
          Takt: 33MHz
     *-pci:7
          Beschreibung: Host bridge
          Produkt: K8 [Athlon64/Opteron] Address Map [1022:1101]
          Hersteller: Advanced Micro Devices, Inc. [AMD] [1022]
          Physische ID: 107
          Bus-Informationen: pci@0000:00:18.1
          Version: 00
          Breite: 32 bits
          Takt: 33MHz
     *-pci:8
          Beschreibung: Host bridge
          Produkt: K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
          Hersteller: Advanced Micro Devices, Inc. [AMD] [1022]
          Physische ID: 108
          Bus-Informationen: pci@0000:00:18.2
          Version: 00
          Breite: 32 bits
          Takt: 33MHz
     *-pci:9
          Beschreibung: Host bridge
          Produkt: K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
          Hersteller: Advanced Micro Devices, Inc. [AMD] [1022]
          Physische ID: 109
          Bus-Informationen: pci@0000:00:18.3
          Version: 00
          Breite: 32 bits
          Takt: 33MHz
          Konfiguration: driver=k8temp
          Ressourcen: irq:0
     *-scsi:0
          Physische ID: 2
          Logischer Name: scsi1
          Fähigkeiten: emulated
        *-disk
             Beschreibung: ATA Disk
             Produkt: ExcelStor Techno
             Physische ID: 0.0.0
             Bus-Informationen: scsi@1:0.0.0
             Logischer Name: /dev/sda
             Version: AB3A
             Seriennummer: [REMOVED]
             Größe: 76GiB (82GB)
             Fähigkeiten: partitioned partitioned:dos
             Konfiguration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=f10ec230
           *-volume:0
                Beschreibung: EXT4-Laufwerk
                Hersteller: Linux
                Physische ID: 1
                Bus-Informationen: scsi@1:0.0.0,1
                Logischer Name: /dev/sda1
                Logischer Name: /
                Version: 1.0
                Seriennummer: [REMOVED]
                Größe: 76GiB
                Kapazität: 76GiB
                Fähigkeiten: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                Konfiguration: created=2016-04-17 09:38:10 filesystem=ext4 lastmountpoint=/ modified=2016-05-17 18:49:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-05-17 18:49:23 state=mounted
           *-volume:1
                Beschreibung: Extended partition
                Physische ID: 2
                Bus-Informationen: scsi@1:0.0.0,2
                Logischer Name: /dev/sda2
                Größe: 445MiB
                Kapazität: 445MiB
                Fähigkeiten: primary extended partitioned partitioned:extended
              *-logicalvolume
                   Beschreibung: Linux swap / Solaris partition
                   Physische ID: 5
                   Logischer Name: /dev/sda5
                   Kapazität: 445MiB
                   Fähigkeiten: nofs
     *-scsi:1
          Physische ID: 3
          Logischer Name: scsi2
          Fähigkeiten: emulated
        *-cdrom
             Beschreibung: DVD-RAM writer
             Produkt: DVDRAM GSA-H44N
             Hersteller: HL-DT-ST
             Physische ID: 0.0.0
             Bus-Informationen: scsi@2:0.0.0
             Logischer Name: /dev/cdrom
             Logischer Name: /dev/cdrw
             Logischer Name: /dev/dvd
             Logischer Name: /dev/dvdrw
             Logischer Name: /dev/sr0
             Version: RB01
             Fähigkeiten: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             Konfiguration: ansiversion=5 status=nodisc


```

The install is pretty fresh. I installed 15.10 and upgraded to 16.04 via the GUI update program. As far as I know, there were no errors.

---

### Post by DuckHook on 2016-05-18
> **Werscannt said:**
> ...It works fine when connected directly to the monitor. The setup with the switch is sadly as in my opening post.I was afraid this would happen. Like I said, this kludge doesn't work all the time.

> The install is pretty fresh. I installed 15.10 and upgraded to 16.04 via the GUI update program. As far as I know, there were no errors.I am sure the issue is not with your install (though the missing /sys/class/drm/ directory thing is still really bothering me), but with your KVM switch.

[LIST=1]
[*]First and foremost: you may wish to buy a better KVM switch. There are switches that will keep the actual EDID info in the switch itself. This way, when the computer boots and queries for EDID, it sees the KVM switch as an actual monitor and everything is good.
[*]
[*]We can also try disabling kernel mode settings (KMS) with the *nomodeset* switch, although this makes your display run more inefficiently. To do so, make your kernel boot line now look as follows:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=VGA-1:1680x1050e"
```Remember to:```
sudo update-grub
```Then reboot.
[/LIST]

---

### Post by Werscannt on 2016-05-18
> **DuckHook said:**
> although this makes your display run more inefficiently.

What does that mean. Will my electrical bill be higher? Can it damage the monitor?

---

### Post by DuckHook on 2016-05-18
> **Werscannt said:**
> What does that mean. Will my electrical bill be higher? Can it damage the monitor?No, nothing like that. It just won't switch from <Ctrl>+<Alt>+<F7> to <Ctrl>+<Alt>+<F1> without resetting the screen. There are also reports of obscure artifacts produced by some apps. *nomodeset* is a workaround that we use around here all the time for old video cards that don't work with new kernels, but should not be resorted to unless needed, as it disables a good feature in newer kernels. It's nice to have the kernel actually setting your video mode because this carries into all work that you do whether in or out of the GUI, or even if you switch between GUIs on unused consoles. This uses resources "efficiently". Defining your graphics used to be the role of Xorg. We are just going back to the bad old days, is all.

It would be a shame to disable this feature in your case because it obviously works as intended. It's your KVM switch that's the culprit. But if this switch is really useful to you, and you don't want to buy a better one, then it is a compromise worth making.

---

### Post by DuckHook on 2016-05-18
A quick Google search turned up this oldish link, but perhaps still useful to you.

[https://www.iogear.com/blog/2011/04/04/dynasync-technology-extends-kvm-handshake-monitors-resolutions-part-ii](https://www.iogear.com/blog/2011/04/04/dynasync-technology-extends-kvm-handshake-monitors-resolutions-part-ii)

There are all sorts available in the market. Just do your research beforehand and make sure they clone EDID into non-volatile memory.

---

### Post by Werscannt on 2016-05-19
Unfortunately with the nomodeset it stays the same. It works via direct hooking but not via the switch.

At least, since the nomodeset, I can boot the PC connected to the screen. When I've logged in I can switch the cables and use the setup as intendet. As long as I don't shutdown the PC it's "something". Not yet the comfort I sought.

Buying a better switch is not really an option, seeing the prices for the good ones.

I hope that we still can try some other stuff to get this to work.
And thank you for the help so far.

---

### Post by DuckHook on 2016-05-19
> **Werscannt said:**
> ...I hope that we still can try some other stuff to get this to work...Yes we can. However, the next steps *do* risk damaging your monitor. You should decide beforehand whether it is worth the risk.

I am going out for dinner shortly. I will post the next instructions when I get home. It is very important that you follow those instructions precisely for the sake of your monitor.

In the meantime, please think about the risk.

---

### Post by DuckHook on 2016-05-20
First, an overview.

We will try to force an EDID onto your video subsystem. This will make your video card put out a signal that has no concern for what your monitor can actually handle. Since your KVM switch prevents your system from accurately querying the monitor, this is the only way to establish a proper signal. The danger is that if the video card pushes a signal beyond the capabilities of the monitor, it can cause a scrambled picture or even burn out your monitor. Therefore, you must get the following absolutely accurate and follow instructions precisely.

[LIST=1]
[*]Connect your monitor directly to your computer (without the KVM switch).
[*]Open a terminal and do:```
cvt 1680 1050
```
[*]This will output two lines that will look something like:```
# 1680x1050 59.98 Hz (CVT 8.29M9) hsync: 134.18 kHz; pclk: 712.75 MHz
Modeline "1680x1050_60.00"  712.75  1680 1760 1792 1812  1050 1063 1068 1137 -hsync +vsync
```***DO NOT USE THESE VALUES!*** This is an example only. You must use the actual values returned from your CVT command. It is the second of these two lines after the "Modeline" that we must record. Do not make a mistake here. Best to copy and paste instead of writing it down and risk transposing a number.
[*]Create an xorg.conf file with:```
sudo nano /etc/X11/xorg.conf
```
[*]Type into this file the following:```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
	Option "DPMS"
	Modeline "The modeline you recorded from step 2 above" Example:
	Modeline "1680x1050_60.00"  712.75  1680 1760 1792 1812  1050 1063 1068 1137 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
                Depth           24
                Modes           "1680x1050_60.00"
        EndSubSection
EndSection
```...where you replace my sample Modeline with the actual Modeline from your CVT report. Again, best to copy and paste instead of retyping.
[*]Write your edits to the *xorg.conf* file with <Ctrl>+<o>, then exit *nano* with <Ctrl>+<x>
[*]Reboot.
[/LIST]

If everything looks okay, then shut computer down, reconnect monitor through KVM switch and boot up. Tell us how it goes.

---

### Post by Werscannt on 2016-05-20
Still no change.
Just to be sure:
I did this:
```
cvt 1680 1050
```

I recieved this:
```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

Then I did this:
```
sudo nano /etc/X11/xorg.conf
```

And created this:
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
    Option "DPMS"
    Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
        SubSection "Display"
                Depth           24
                Modes           "1680x1050_60.00"
        EndSubSection
EndSection

```

---

### Post by DuckHook on 2016-05-20
xorg.conf file looks fine and I am running out of ideas.

In my opinion, the problem with your setup is that you have tempted fate one too many times.

[LIST=1]
[*]You have a very old machine,
[*]with a very old AGP graphics card (I haven't seen one of those in years),
[*]that, in addition to its age and obsolete technology, is also obscure (it is an S3)
[/LIST]
...and yet this whole unlikely assembly runs well with a vanilla Lubuntu install. Frankly, this is already a huge testament to the versatility of Lubuntu. However, the addition of the cheap KVM switch is one mountain too many for Lubuntu to climb.

If a better KVM switch is not viable, then I suppose you will just have to physically swap cables.

Unless another poster has something to offer, I'm afraid I have no further ideas.

---

### Post by Werscannt on 2016-05-21
I wasn't aware of the rarity of my hardware.

I think I will undo the changes than.

What is your opinion about [this KVM-Switch]("http://www.amazon.de/UNICLASS-AH-04-Transparent-USB-Emulation-Monitor-Daten-Spiegelung/dp/B0051MNWRK/ref=sr_1_8?ie=UTF8&qid=1463816100&sr=8-8&keywords=kvm+EDID")?

---

### Post by DuckHook on 2016-05-21
> **Werscannt said:**
> ...I think I will undo the changes than......a good idea. If the changes don't really work anyway, then you want the original clean and simple environment.> What is your opinion about [this KVM-Switch]("http://www.amazon.de/UNICLASS-AH-04-Transparent-USB-Emulation-Monitor-Daten-Spiegelung/dp/B0051MNWRK/ref=sr_1_8?ie=UTF8&qid=1463816100&sr=8-8&keywords=kvm+EDID")?Unfortunately, I don't speak German, but so long as your purchase allows for returns, why not check it out? Another option is to just install an EDID emulator on your Linux computer. I found [this]("http://www.ebay.ca/itm/Extron-EDID-101V-Emulator-Extron-Emulato-With-EDID-Minder-for-VGA-/152004023018?hash=item23642552ea:g:5x4AAOSwKIpWEe9m") one on ebay for $US14.99+shipping. I have no knowledge of these units. I just Googled for them, so you must do your own research and make your own decision, but based on their description, it would appear to fit your needs.

---

