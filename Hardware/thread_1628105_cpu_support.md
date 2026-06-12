---
title: "cpu support?"
date: 2010-11-22
forum: Hardware
---

### Post by armintirand on 2010-11-22
hi 
I've e qompaq laptop in presario 2100 model. my laptop has cor2 cpu but ubuntu hasn't known core2 and this is lshw command result:
description: Computer```

    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 432MiB
     *-cpu
          product: Mobile Intel(R) Pentium(R) 4 - M CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 2200MHz
          capacity: 2200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: RS200/RS200M AGP Bridge [IGP 340M]
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64
          resources: irq:0 memory:d4000000-d7ffffff memory:d000a000-d000afff
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 340M]
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:9000(size=4096) memory:d0300000-d03fffff memory:d8000000-dfffffff
           *-display
                description: VGA compatible controller
                product: Radeon IGP 330M/340M/350M
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:10 memory:d8000000-dfffffff ioport:9000(size=256) memory:d0300000-d030ffff memory:d0320000-d033ffff
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:10 memory:d0000000-d0000fff
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2
             resources: irq:5 ioport:1000(size=256) memory:d0001000-d0001fff
        *-isa
             description: ISA bridge
             product: M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-communication UNCLAIMED
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=64
             resources: memory:d0002000-d0002fff ioport:1400(size=256)
        *-network:0
             description: Wireless interface
             product: Prism 2.5 Wavelan chipset
             vendor: Intersil Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wifi0
             version: 01
             serial: 00:02:8a:aa:97:43
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list logical wireless ethernet physical
             configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=64 multicast=yes wireless=IEEE 802.11b
             resources: irq:10 memory:d000b000-d000bfff
        *-pcmcia
             description: CardBus bridge
             product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
             resources: irq:11 memory:d0003000-d0003fff ioport:1800(size=256) ioport:1c00(size=256) memory:2c000000-2fffffff memory:30000000-33ffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:11 memory:d0008000-d00087ff memory:d0004000-d0007fff
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_ali latency=32 maxlatency=4 mingnt=2
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2000(size=16)
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus latency=0
             resources: irq:0
        *-network:1
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 00
             serial: 00:0b:cd:ea:ef:46
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical
             configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.1.2 latency=90 maxlatency=52 mingnt=11 multicast=yes
             resources: irq:10 ioport:2400(size=256) memory:d0009000-d0009fff memory:34000000-3400ffff
```
how can introduce cpu to ubuntu?

---

### Post by Fafler on 2010-11-22
> product: Mobile Intel(R) Pentium(R) 4 - M CPU 2.20GHz

[http://ark.intel.com/Product.aspx?id=27359](http://ark.intel.com/Product.aspx?id=27359)

I'll let you figure the rest out.

---

### Post by armintirand on 2010-11-23
my laptop is working in ubuntu slower than xp please help me?
do i need to compile a custom kernel or other work?

---

### Post by Fafler on 2010-11-23
What do you base that claim on? Your CPU is a Pentium 4-M. It only has one core, not matter which OS you use.

If it's just that your laptop /feels/ slower with Ubuntu, then try one of the lighter alternatives like Lubuntu and Xubuntu. They use less memory and runs faster on older systems like yours.

---

### Post by armintirand on 2010-11-24
thank you for help me.
I download iso image of arche linux that it doesn't have desktop and working with a command line mode wery fast but i am a web and Qt programmer and i need desktop mode and i want to download all of library and software for installing gnome desktop and configure all them and a custom kernel for working faster and using less memory.
can you help me in this way.perhaps we create new custom linux for our owen .

---

### Post by Fafler on 2010-11-24
You really should try this: [http://people.ubuntu.com/~gilir/lubuntu-10.10.iso](http://people.ubuntu.com/~gilir/lubuntu-10.10.iso) It´s an Ubuntu variant that uses LXDE as window manager instead of Gnome. Quite neat and useful.
Or if you really want Gnome, try Debian. It install less software as default and might be a bit faster.

You could also look into upgrading your laptop. More memory could be added and you could find a faster harddrive. Those things can be found quite cheap second hand.

---

### Post by armintirand on 2010-11-25
thanks but i should test creating custom linux .can you help me?

---

### Post by Fafler on 2010-11-26
A custom kernel? Well, back in the day when computers ran at a couple of hundred mhz and had 32 mb of memory it could improve performance to configure and build a custom kernel, but your case you won't benefit from it. It's way to much of a hassle to justify.

Try something LXDE based or get more memory :-)

---

### Post by conradin on 2010-11-26
Fluxbox has served me well for a light weight interface. You may also want to verify your system's hardware performance before simply adding more ram.
As an example, a failing harddrive may generate numerous IO errors or context switches which will take up more cpu time. a great application for testing hardware is vmstat. [http://events.linuxfoundation.org/slides/2010/linuxcon2010_hoch.pdf](http://events.linuxfoundation.org/slides/2010/linuxcon2010_hoch.pdf) is a decent tutorial on system performance.

---

### Post by mastablasta on 2010-11-26
problem could also be the bad ATI driver. ATI dropped support for osme older cards so we need to use opensource drivers which are a hit or miss. depending on what card/chip you have.
 
try turning off the special effects.
 
you **HAVE** enough memory to run Ubuntu. = 432MiB
 
edit i run it (Ubuntu 10.04 LTS) on 224MB. but have a different card. i am runnig it with all effects off, clearlooks theme and no background photo. runs much faster then winXP.

---

### Post by armintirand on 2010-11-26
thank's for answers .my process that i saw its by writing 
ps -e
command in terminal:
>  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 migration/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 cpuset
    8 ?        00:00:00 khelper
    9 ?        00:00:00 netns
   10 ?        00:00:00 async/mgr
   11 ?        00:00:00 pm
   12 ?        00:00:00 sync_supers
   13 ?        00:00:00 bdi-default
   14 ?        00:00:00 kintegrityd/0
   15 ?        00:00:00 kblockd/0
   16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpi_notify
   18 ?        00:00:00 kacpi_hotplug
   19 ?        00:00:00 ata_aux
   20 ?        00:00:00 ata_sff/0
   21 ?        00:00:00 khubd
   22 ?        00:00:00 kseriod
   23 ?        00:00:00 kmmcd
   25 ?        00:00:00 khungtaskd
   26 ?        00:00:00 kswapd0
   27 ?        00:00:00 ksmd
   28 ?        00:00:00 aio/0
   29 ?        00:00:00 ecryptfs-kthrea
   30 ?        00:00:00 crypto/0
   38 ?        00:00:00 kstriped
   39 ?        00:00:00 kmpathd/0
   40 ?        00:00:00 kmpath_handlerd
   41 ?        00:00:00 ksnapd
   42 ?        00:00:00 kondemand/0
   43 ?        00:00:00 kconservative/0
  200 ?        00:00:00 scsi_eh_0
  203 ?        00:00:00 scsi_eh_1
  265 ?        00:00:00 jbd2/sda8-8
  266 ?        00:00:00 ext4-dio-unwrit
  299 ?        00:00:00 flush-8:0
  329 ?        00:00:00 upstart-udev-br
  332 ?        00:00:00 udevd
  445 ?        00:00:00 udevd
  446 ?        00:00:00 udevd
  495 ?        00:00:00 kpsmoused
  501 ?        00:00:00 pccardd
  701 ?        00:00:00 jbd2/sda5-8
  704 ?        00:00:00 ext4-dio-unwrit
  743 ?        00:00:00 jbd2/sda6-8
  745 ?        00:00:00 ext4-dio-unwrit
  838 ?        00:00:00 smbd
  846 ?        00:00:00 rsyslogd
  863 ?        00:00:00 dbus-daemon
  879 ?        00:00:00 NetworkManager
  880 ?        00:00:00 avahi-daemon
  884 ?        00:00:00 avahi-daemon
  891 ?        00:00:00 modem-manager
  912 ?        00:00:00 smbd
  917 ?        00:00:00 wpa_supplicant
  952 tty4     00:00:00 getty
  957 tty5     00:00:00 getty
  964 ?        00:00:00 gdomap
  968 tty2     00:00:00 getty
  970 tty3     00:00:00 getty
  973 tty6     00:00:00 getty
  975 ?        00:00:00 acpid
  981 ?        00:00:00 cron
  982 ?        00:00:00 atd
 1011 ?        00:00:00 winbindd
 1020 ?        00:00:00 winbindd
 1081 ?        00:00:00 apache2
 1128 ?        00:00:00 apache2
 1129 ?        00:00:00 apache2
 1130 ?        00:00:00 apache2
 1131 ?        00:00:00 apache2
 1132 ?        00:00:00 apache2
 1147 ?        00:00:00 gdm-binary
 1161 ?        00:00:00 cupsd
 1164 ?        00:00:00 console-kit-dae
 1232 ?        00:00:00 gdm-simple-slav
 1237 tty7     00:01:24 Xorg
 1281 tty1     00:00:00 getty
 1289 ?        00:00:00 radeon/0
 1290 ?        00:00:00 ttm_swap
 1297 ?        00:00:01 kslowd000
 1298 ?        00:00:01 kslowd001
 1317 ?        00:00:00 dbus-launch
 1335 ?        00:00:00 gdm-session-wor
 1339 ?        00:00:00 upowerd
 1360 ?        00:00:00 polkitd
 1450 ?        00:00:00 gnome-keyring-d
 1469 ?        00:00:00 gnome-session
 1508 ?        00:00:00 ssh-agent
 1511 ?        00:00:00 dbus-launch
 1512 ?        00:00:00 dbus-daemon
 1517 ?        00:00:01 gconfd-2
 1522 ?        00:00:00 gnome-power-man
 1526 ?        00:00:03 gnome-settings-
 1531 ?        00:00:00 gvfsd
 1536 ?        00:00:00 gvfs-fuse-daemo
 1540 ?        00:00:04 metacity
 1543 ?        00:00:16 pulseaudio
 1545 ?        00:00:00 rtkit-daemon
 1550 ?        00:00:02 python
 1551 ?        00:00:00 polkit-gnome-au
 1552 ?        00:00:03 gnome-panel
 1554 ?        00:00:12 nautilus
 1556 ?        00:00:01 nm-applet
 1557 ?        00:00:00 gconf-helper
 1569 ?        00:00:01 syndaemon
 1571 ?        00:00:00 gvfs-gdu-volume
 1573 ?        00:00:00 udisks-daemon
 1574 ?        00:00:00 udisks-daemon
 1576 ?        00:00:00 gvfsd-trash
 1578 ?        00:00:00 gvfs-afc-volume
 1581 ?        00:00:00 gvfs-gphoto2-vo
 1583 ?        00:00:00 bonobo-activati
 1592 ?        00:00:08 wnck-applet
 1593 ?        00:00:00 trashapplet
 1596 ?        00:00:03 multiload-apple
 1607 ?        00:00:00 indicator-apple
 1608 ?        00:00:01 clock-applet
 1609 ?        00:00:00 notification-ar
 1620 ?        00:00:00 gvfsd-metadata
 1622 ?        00:00:00 indicator-me-se
 1627 ?        00:00:00 indicator-sessi
 1631 ?        00:00:00 gnome-screensav
 1634 ?        00:00:00 gvfsd-burn
 1645 ?        00:00:00 gdu-notificatio
 1649 ?        00:00:00 winbindd
 1660 ?        00:00:00 firefox
 1664 ?        00:00:00 run-mozilla.sh
 1668 ?        00:03:02 firefox-bin
 1698 ?        00:00:00 applet.py
 1711 ?        00:00:10 ubuntuone-syncd
 1719 ?        00:00:00 update-notifier
 1725 ?        00:00:00 system-service-
 1742 ?        00:00:00 dhclient
 1749 ?        00:00:01 notify-osd
 1804 ?        00:00:00 nmbd
 1876 ?        00:00:03 gnome-terminal
 1879 ?        00:00:00 gnome-pty-helpe
 1880 pts/0    00:00:01 bash
 1974 pts/0    00:00:00 man
 1983 pts/0    00:00:00 pager
 2189 pts/1    00:00:00 bash
 2207 pts/1    00:00:00 ps

and i want to disable its but i don't know its work.for example i need desable apachi and gdm for default and enable them if i need.
which command can disable default of them's,and enable?

---

### Post by armintirand on 2010-11-30
do you know how disable a services in start up?for example gdm and apachi and so on.my startup services is very much and i don't need more them.please help me.
thank's .

---

### Post by Ralph L on 2011-09-20
For speeding up Presario 2195us, see [http://ubuntuforums.org/showthread.php?t=1805633&highlight=presario+2100](http://ubuntuforums.org/showthread.php?t=1805633&highlight=presario+2100)

---

### Post by sisco311 on 2011-09-20
Necrobumping.

Thread Closed.

---

