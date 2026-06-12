---
title: "Stuck at 92%"
date: 2008-08-15
forum: General Help
---

### Post by HpZ on 2008-08-15
I'm installing Ubuntu from the live CD and it has stopped at 92%. I can still open things and everything works, just it isn't moving up from 92%. It says that it's detecting harware. How long should I wait?

---

### Post by ibuclaw on 2008-08-15
Isn't usually that long. How many times have you tried installing?

Does
```
sudo lshw
```in the console finish running?

Regards
Iain

---

### Post by HpZ on 2008-08-15
i've tried installing alot of times today, more yesterday.

it's still on 92% after I ran the code. here is the output > ubuntu@ubuntu:~$ sudo lshw
ubuntu
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop uuid=1297A232-FFFF-FFFF-FFFF-FFFFFFFFFFFF
  *-core
       description: Motherboard
       product: AK32
       vendor: Shuttle Inc
       physical id: 0
       slot: USB
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/07/2003)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 2GHz
          capacity: 2GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 1011MB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MB
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
     *-pci
          description: Host bridge
          product: VT8366/A/7 [Apollo KT266/A/333]
          vendor: VIA Technologies, Inc.
          physical id: e8000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: VT8366/A/7 [Apollo KT266/A/333 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 4000 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: c1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:ec000000-ecffffff iomemory:e0000000-e7ffffff irq:5
        *-network:0 DISABLED
             description: Wireless interface
             product: Ralink RT2500 802.11 Cardbus Reference Card
             vendor: RaLink
             physical id: c
             bus info: pci@00:0c.0
             logical name: ra0
             version: 01
             serial: 00:11:50:14:c0:49
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt2500 multicast=yes wireless=RT2500 Wireless
             resources: iomemory:ee000000-ee001fff irq:193
        *-network:1
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: e
             bus info: pci@00:0e.0
             logical name: eth0
             version: 10
             serial: 00:06:4f:56:c1:12
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half ip=192.168.1.4 link=yes multicast=yes port=MII speed=10MB/s
             resources: ioport:d000-d0ff iomemory:ee002000-ee0020ff irq:185
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-23-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: 2.4G Receiver
                   vendor: Areson Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=60mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-23-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:dc00-dc1f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-23-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:ee003000-ee0030ff irq:177
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-23-386 ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:e000-e00f irq:169
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD1200JB-00GVA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 08.02D08
                   serial: WD-WCAL93879252
                   size: 111GB
                   capacity: 111GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 108GB
                      capabilities: primary bootable
                 *-volume:1 UNCLAIMED
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      capacity: 2965MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: LITE-ON DVDRW LH-20A1P
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: KL02
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:e400-e4ff irq:201


---

### Post by Superkoop on 2008-08-15
Attach your intaller log, and we can see what is going wrong.
The log is located in /var/log/installer/syslog

---

### Post by HpZ on 2008-08-15
Ubiquity 1.0.12
Fri, 15 Aug 2008 16:56:58 INFO     switched to page stepLanguage
ubiquity: Starting up '['/usr/lib/ubiquity/localechooser/localechooser']' for ubiquity.components.language.Language
ubiquity: Watching for question patterns ^languagechooser/language-name
Fri, 15 Aug 2008 16:57:26 INFO     Step_before = stepLanguage
Fri, 15 Aug 2008 16:57:26 INFO     switched to page stepLocation
Fri, 15 Aug 2008 16:57:26 INFO     Step_after = stepLocation
ubiquity: Starting up '['/usr/share/ubiquity/tzsetup']' for ubiquity.components.timezone.Timezone
ubiquity: Watching for question patterns ^time/zone$
Fri, 15 Aug 2008 16:57:37 INFO     Step_before = stepLocation
Fri, 15 Aug 2008 16:57:37 INFO     switched to page stepKeyboardConf
Fri, 15 Aug 2008 16:57:37 INFO     Step_after = stepKeyboardConf
ubiquity: kbd-chooser prepare
ubiquity: Starting up '['/bin/sh', '-c', '. /usr/share/debconf/confmodule; exec /usr/lib/ubiquity/kbd-chooser/kbd-chooser']' for ubiquity.components.kbd_chooser.KbdChooser
ubiquity: Watching for question patterns ^kbd-chooser/method$, ^console-keymaps.*/keymap$, ERROR
ubiquity: apply_keyboard: uk
ubiquity: apply_keyboard: layout gb
ubiquity: Display map: {u'Swedish': u'se-latin1', u'Icelandic': u'is-latin1', u'Estonian': u'et', u'Romanian': u'ro', u'Italian': u'it', u'Latin American': u'la-latin1', u'Dutch': u'nl', u'Brazilian (EUA layout)': u'br-latin1', u'Belgian': u'be2-latin1', u'Danish': u'dk-latin1', u'Bulgarian': u'bg', u'Turkish (F layout)': u'trfu', u'Hungarian': u'hu', u'Macedonian': u'mk', u'Lithuanian': u'lt', u'French': u'fr-latin9', u'Norwegian': u'no-latin1', u'Slovakian': u'sk-qwerty', u'Russian': u'ru', u'Dvorak': u'dvorak', u'Slovene': u'slovene', u'Finnish': u'fi-latin1', u'British English': u'uk', u'Spanish': u'es', u'Greek': u'gr', u'Canadian French': u'cf', u'Latvian': u'lv-latin4', u'American English': u'us', u'Croatian': u'croat', u'Portuguese': u'pt-latin1', u'Czech': u'cz-lat2', u'Ukrainian': u'ua', u'Japanese': u'jp106', u'Belarusian': u'by', u'Turkish (Q layout)': u'trqu', u'German': u'de-latin1-nodeadkeys', u'Hebrew': u'hebrew', u'Polish': u'pl', u'Brazilian (ABNT2 layout)': u'br-abnt2', u'Swiss French': u'fr_CH-latin1', u'Swiss German': u'sg-latin1', u'Serbian (Cyrillic)': u'sr-cy'}
ubiquity: Untranslated choices: [u'by', u'bg', u'croat', u'cz-lat2', u'sg-latin1', u'de-latin1-nodeadkeys', u'dk-latin1', u'us', u'uk', u'dvorak', u'et', u'es', u'la-latin1', u'fi-latin1', u'fr-latin9', u'be2-latin1', u'cf', u'fr_CH-latin1', u'gr', u'hebrew', u'hu', u'is-latin1', u'it', u'lt', u'lv-latin4', u'jp106', u'mk', u'no-latin1', u'nl', u'pl', u'pt-latin1', u'br-abnt2', u'br-latin1', u'ro', u'ru', u'sk-qwerty', u'slovene', u'sr-cy', u'se-latin1', u'trfu', u'trqu', u'ua']
ubiquity: Choices: [u'Belarusian', u'Bulgarian', u'Croatian', u'Czech', u'Swiss German', u'German', u'Danish', u'American English', u'British English', u'Dvorak', u'Estonian', u'Spanish', u'Latin American', u'Finnish', u'French', u'Belgian', u'Canadian French', u'Swiss French', u'Greek', u'Hebrew', u'Hungarian', u'Icelandic', u'Italian', u'Lithuanian', u'Latvian', u'Japanese', u'Macedonian', u'Norwegian', u'Dutch', u'Polish', u'Portuguese', u'Brazilian (ABNT2 layout)', u'Brazilian (EUA layout)', u'Romanian', u'Russian', u'Slovakian', u'Slovene', u'Serbian (Cyrillic)', u'Swedish', u'Turkish (F layout)', u'Turkish (Q layout)', u'Ukrainian']
ubiquity: console-keymaps-at/keymap db: uk
Fri, 15 Aug 2008 16:57:41 INFO     Step_before = stepKeyboardConf
Fri, 15 Aug 2008 16:57:41 INFO     switched to page stepUserInfo
Fri, 15 Aug 2008 16:57:41 INFO     Step_after = stepUserInfo
ubiquity: Starting up '['/usr/lib/ubiquity/user-setup/user-setup-ask', '/target']' for ubiquity.components.usersetup.UserSetup
ubiquity: Watching for question patterns ^passwd/user-fullname$, ^passwd/username$, ^passwd/user-password$, ^passwd/user-password-again$, ERROR
ON STATE: 1
ON STATE: 2
ON STATE: 3
ON STATE: 4
ON STATE: 5
ON STATE: 6
ON STATE: 7
ON STATE: 8
Fri, 15 Aug 2008 16:57:51 INFO     Step_before = stepUserInfo
Fri, 15 Aug 2008 16:57:51 INFO     switched to page stepPartDisk
Fri, 15 Aug 2008 16:57:51 INFO     Step_after = stepPartDisk
ubiquity: Starting up '/bin/partman' for ubiquity.components.partman.Partman
ubiquity: Watching for question patterns ^partman-auto/select_disk$, ^partman-auto/.*automatically_partition$, ^partman-partitioning/new_size$, ^partman/choose_partition$, ^partman/confirm.*, type:boolean, ERROR, PROGRESS
unsupported
kernelmodules_basicfilesystems
kernelmodules_ext3
kernelmodules_jfs
kernelmodules_reiserfs
kernelmodules_xfs
umount_target
parted
dump
update_partitions
filesystems_detected
auto_mountpoints
autouse_swap
backup
Fri, 15 Aug 2008 16:57:58 INFO     switched to page stepPartAuto
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
Fri, 15 Aug 2008 16:58:01 INFO     switched to page stepReady
ubiquity: Starting up '['/usr/share/ubiquity/summary']' for ubiquity.components.summary.Summary
ubiquity: Watching for question patterns ^ubiquity/summary$
swapon: /dev/hda5: Device or resource busy
swapon: /dev/hda5: Device or resource busy
swapon: /dev/hda5: Device or resource busy
swapon: /dev/hda5: Device or resource busy
umount /target/
swapoff /dev/hda5
chroot: cannot run command `apt-get': No such file or directory
Fri, 15 Aug 2008 16:59:50 INFO     progress_loop()
ubiquity: Starting up '['/usr/share/ubiquity/install.py']' for ubiquity.components.install.Install
ubiquity: Watching for question patterns ^.*/apt-install-failed$, CAPB, ERROR, PROGRESS
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory
ubiquity: Starting up '['sh', '-c', '/usr/lib/ubiquity/localechooser/post-base-installer && /usr/lib/ubiquity/localechooser/prebaseconfig']' for ubiquity.components.language_apply.LanguageApply
Reading package lists...
Building dependency tree...
Skipping locales, it is already installed and upgrade is not set.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists...
Building dependency tree...
E: Couldn't find package localization-config
Reading package lists...
Building dependency tree...
Skipping console-tools, it is already installed and upgrade is not set.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubiquity: Starting up '['/usr/share/ubiquity/apt-setup']' for ubiquity.components.apt_setup.AptSetup
/usr/lib/ubiquity/apt-setup/generators/01setup: line 7: /target/etc/apt/sources.list: No such file or directory
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release [34.8kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages [619kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages [4571B]
Fetched 659kB in 3s (213kB/s)
Reading package lists...
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources [255kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources [1478B]
Fetched 257kB in 1s (173kB/s)
Reading package lists...
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release [50.9kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages [284kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages [6702B]
Fetched 342kB in 1s (211kB/s)
Reading package lists...
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources [76.1kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources [983B]
Fetched 77.1kB in 0s (113kB/s)
Reading package lists...
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [154kB]
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [8706B]
Fetched 213kB in 1s (172kB/s)
Reading package lists...
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Fetched 1B in 0s (2B/s)
Reading package lists...
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [30.9kB]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [983B]
Fetched 31.9kB in 0s (52.8kB/s)
Reading package lists...
Fri, 15 Aug 2008 17:04:17 INFO     keeping language packs for: en
ubiquity: Starting up '['/usr/lib/ubiquity/tzsetup/prebaseconfig']' for ubiquity.components.timezone_apply.TimezoneApply
ubiquity: Starting up '['/usr/share/ubiquity/clock-setup']' for ubiquity.components.clock_setup.ClockSetup
ubiquity: Starting up '['/usr/lib/ubiquity/kbd-chooser/prebaseconfig']' for ubiquity.components.kbd_chooser_apply.KbdChooserApply
ubiquity: Starting up '['/usr/lib/ubiquity/user-setup/user-setup-apply', '/target']' for ubiquity.components.usersetup_apply.UserSetupApply
ubiquity: Starting up '['/bin/hw-detect']' for ubiquity.components.hw_detect.HwDetect
find: WARNING: Hard link count is wrong for /lib/modules/2.6.15-23-386/kernel: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

---

### Post by HpZ on 2008-08-15
still at 92% :(

---

### Post by HpZ on 2008-08-15
c'mon...anyone?

---

### Post by HpZ on 2008-08-15
shameless bump

---

### Post by jackTL2 on 2008-08-15
There might be something wrong with the ubuntu disc. Try downloading and re-burning the disc and also use the MD5 or ASC hash to check if the file you downloaded is the exact same copy on the server you downloaded it from. There are free tools on win to check these hashes.

---

