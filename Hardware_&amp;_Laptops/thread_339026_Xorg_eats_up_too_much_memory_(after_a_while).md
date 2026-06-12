---
title: "Xorg eats up too much memory (after a while)"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by eantoranz on 2007-01-15
I have noticed that Xorg eats up a huge amount of memory after a while.... well... not exactly a while. It's been running for about three weeks.. and now top says it's taking 1176Mb of Virtual Memory, 276Mb or Resident Memory and about 3Mbs of shared memory.

Is there a memory leak?

I will be restarting X later in the day, so I get to release that amount of memory.... but if you need any information or want me to run a command before I kill it, this is the moment to do it.

This is some information:
xorg.conf
```

Section "Files"
        # paths to defoma fonts
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/100dpi:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
    FontPath    "/usr/local/share/fonts"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "latam"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        #VideoRam       4096
EndSection

Section "Monitor"
        Identifier      "hp 5500"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Device"
        Monitor         "hp 5500"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option  "Composite" "Enabled"
EndSection

```

ps ax
```

  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init splash
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S      0:00 [migration/1]
    6 ?        SN     0:00 [ksoftirqd/1]
    7 ?        S      0:00 [watchdog/1]
    8 ?        S<     0:02 [events/0]
    9 ?        S<     0:00 [events/1]
   10 ?        S<     0:00 [khelper]
   11 ?        S<     0:00 [kthread]
   14 ?        S<     0:01 [kblockd/0]
   15 ?        S<     0:00 [kblockd/1]
   16 ?        S<     0:00 [kacpid]
   17 ?        S<     0:00 [kacpi_notify]
   89 ?        S<     0:00 [kseriod]
  130 ?        S      0:25 [kswapd0]
  131 ?        S<     0:00 [aio/0]
  132 ?        S<     0:00 [aio/1]
  758 ?        S      0:00 [kirqd]
 1805 ?        S<     0:00 [khubd]
 1980 ?        S<     0:02 [reiserfs/0]
 1981 ?        S<     0:00 [reiserfs/1]
 2062 ?        Ss     0:00 //sbin/logd
 2159 ?        S<s    0:00 /sbin/udevd --daemon
 3566 ?        S<     0:00 [kpsmoused]
 3692 ?        S<     0:00 [shpchpd]
 4165 ?        S<s    0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
 4256 ?        S<     0:07 [kjournald]
 4733 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4734 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4737 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4738 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4739 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4740 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5239 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 5454 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 5456 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 5475 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 5490 ?        Ss     0:02 /usr/sbin/hald
 5491 ?        S      0:00 hald-runner
 5497 ?        S      0:00 /usr/lib/hal/hald-addon-acpi
 5500 ?        S      0:03 /usr/lib/hal/hald-addon-keyboard
 5514 ?        S      0:01 /usr/lib/hal/hald-addon-storage
 5548 ?        Ssl    0:40 /usr/sbin/named -u bind
 5608 ?        Ss     0:15 /usr/sbin/cupsd
 5625 ?        Ss     0:00 /usr/sbin/hpiod
 5628 ?        S      0:00 python /usr/sbin/hpssd
 5674 ?        Ss     0:01 /usr/sbin/apt-index-watcher watch --syslog
 5729 ?        Ss     0:01 /usr/bin/freshclam -p /var/run/clamav/freshclam.pid -d --quiet
 5743 ?        S      0:00 /usr/sbin/inetutils-inetd
 5780 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 5844 ?        Sl     1:05 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 5845 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 5946 ?        Ss     4:43 /usr/sbin/nmbd -D
 5948 ?        Ss     0:00 /usr/sbin/smbd -D
 5966 ?        Ss     0:00 /usr/sbin/sshd
 5980 ?        S      0:00 /usr/sbin/smbd -D
 6021 ?        Ss     0:00 /usr/bin/kdm
 6031 tty7     Rs+  139:50 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-Vn0pL3
 6032 ?        S      0:00 -:0
 6069 ?        Ss     0:00 /usr/sbin/hcid
 6073 ?        Ss     0:00 /usr/sbin/sdpd
 6118 ?        Ss     0:00 /usr/bin/hidd --search --master --server
 6125 ?        S<     0:00 [krfcommd]
 6205 ?        Ss     0:00 /usr/sbin/squid -D -sYC
 6207 ?        S      0:00 (squid) -D -sYC
 6228 ?        Ss     0:00 (sh) /home/antoranz/squid_ldap.sh
 6229 ?        Ss     0:00 (sh) /home/antoranz/squid_ldap.sh
 6230 ?        Ss     0:00 (sh) /home/antoranz/squid_ldap.sh
 6231 ?        Ss     0:00 (sh) /home/antoranz/squid_ldap.sh
 6232 ?        Ss     0:00 (sh) /home/antoranz/squid_ldap.sh
 6233 ?        Ss     0:00 /usr/sbin/cron
 6252 ?        Ss     0:00 (unlinkd)
 6257 ?        Ss     0:00 /usr/sbin/apache2 -k start -DSSL
 6315 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6316 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6317 ?        S      0:01 /usr/sbin/apache2 -k start -DSSL
 6318 ?        S      0:01 /usr/sbin/apache2 -k start -DSSL
 6319 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6359 ?        Ss     0:00 /bin/sh /usr/bin/startkde
 6413 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
 6414 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
 6417 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
 6418 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 9 --print-address 7 --session
 6452 ?        S      0:00 start_kdeinit --new-startup +kcminit_startup
 6453 ?        Ss     0:14 kdeinit Running...
 6456 ?        S      0:50 dcopserver [kdeinit] --nosid
 6459 ?        S      0:07 klauncher [kdeinit] --new-startup
 6461 ?        S      9:09 kded [kdeinit] --new-startup
 6467 ?        S      0:00 kwrapper ksmserver
 6469 ?        S      0:01 ksmserver [kdeinit]
 6470 ?        S      2:12 kwin [kdeinit] -session 10f9dca194000116541898400000111340000_1166219154_780641
 6472 ?        S      3:58 kdesktop [kdeinit]
 6474 ?        S      7:22 kicker [kdeinit]
 6496 ?        S      0:02 kio_uiserver [kdeinit]
 6530 ?        S      0:01 /usr/bin/artsd -F 10 -S 4096 -a alsa -d -n -s 1 -m artsmessage -c drkonqi -l 3 -f
 6539 ?        S      0:09 kaccess [kdeinit]
 6541 ?        S      0:06 kxkb [kdeinit]
 6544 ?        S      0:07 kmix [kdeinit] -session 10f9dca194000114226452900000117630027_1166219152_361633
 6551 ?        Sl     0:47 ktorrent -session 10f9dca194000115981509800000169250030_1166219151_537192
 6553 ?        S     14:32 akregator -session 10f9dca194000116378640900000010500136_1166219151_537350
 6554 ?        S      0:58 gkrellm --sm-client-id 10f9dca194000116014172400000104200014
 6560 ?        R      0:04 knotify [kdeinit]
 6567 ?        SLl   65:58 amarok                    -session 10f9dca194000116411723300000010500152_1166219152_233032
 6578 ?        S      0:00 /usr/bin/passkey-agent --default /usr/lib/kdebluetooth/kbluepin
 6590 ?        S      0:16 xscreensaver -nosplash
 6592 ?        S      0:11 klipper [kdeinit]
 6595 ?        Ss     0:00 vdccm
 6596 ?        S      2:03 adept_notifier
 6603 ?        S      0:01 kbluetoothd --dontforceshow
 6607 ?        S      0:12 korgac --miniicon korganizer
 6618 ?        S      0:13 kwalletmanager --kwalletd
 6647 ?        S      0:00 ruby /usr/share/apps/amarok/scripts/score_default/score_default.rb
 6648 ?        S      0:00 ruby /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb
18382 ?        S      0:00 /usr/bin/kdesud
27263 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
23122 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
14694 ?        Ss     0:00 /sbin/mount.smbfs //192.168.0.87/edmundo /mnt/tmp/ -o rw uid 1000 username fhep\ecarmona
14696 ?        S      0:00 [smbiod]
32042 ?        S      0:06 [pdflush]
32043 ?        S      0:15 [pdflush]
32231 ?        Ss     0:00 /sbin/mount.smbfs //fhep_srvapp01.fhep.org/asys /mnt/tmp/ -o rw username fhep\ecarmona
27954 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-antoranz/klauncherYKL2wb.slave-socket /tmp/ksocket-antoranz/kio_thumbnailMQlxsa.slave-socket
 2896 ?        S      0:00 dcopserver [kdeinit] --nosid
19640 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
19641 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 2846 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 4132 ?        Ss     0:00 /usr/bin/freshclam -p /var/run/clamav/freshclam.pid -d --quiet
29235 ?        SNs    0:00 /sbin/syslogd
30637 ?        RLl    6:17 /usr/lib/firefox/firefox-bin
30642 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 12
30820 ?        S      0:01 konsole [kdeinit]
30821 pts/1    Ss+    0:00 /bin/bash
30956 ?        Ss     0:00 /usr/lib/firefox/firefox-bin
31092 ?        S      0:09 konqueror [kdeinit] http://digg.com/linux_unix/4_reasons_to_dump_Linux
31931 ?        R      0:20 konsole [kdeinit]
31932 pts/2    Ss     0:00 /bin/bash
31957 ?        S      0:00 kio_http [kdeinit] http /tmp/ksocket-antoranz/klauncherYKL2wb.slave-socket /tmp/ksocket-antoranz/akregatorsztbJa.slave-socket
32023 ?        S      0:00 kio_http [kdeinit] http /tmp/ksocket-antoranz/klauncherYKL2wb.slave-socket /tmp/ksocket-antoranz/amarokgD1P6b.slave-socket
32028 pts/2    R+     0:00 ps ax
32029 pts/2    R+     0:00 cat

```

lshw
```

aitdes-03
    description: Low Profile Desktop Computer
    product: HP dc5000 SFF(DX854AV)
    vendor: Hewlett-Packard
    serial: MXJ4430DCN
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=low-profile uuid=D07ACE85-0D2B-D911-BBDA-85B4BAF30011
  *-core
       description: Motherboard
       product: 090Ch
       vendor: Hewlett-Packard
       physical id: 0
       serial: MXJ4430DCN
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786B0 v1.00 (02/12/2004)
          size: 128KB
          capacity: 448KB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: XU1 PROCESSOR
          size: 3GHz
          capacity: 3200MHz
          width: 32 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 20KB
             capacity: 20KB
             capabilities: burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 1MB
             capacity: 4MB
             capabilities: burst internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory:0
          description: System Memory
          physical id: 27
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: NT128D64SH4B1G-5T
             vendor: JEDEC ID:7F 7F 7F 0B 00 00 00 00
             physical id: 0
             serial: 00000000
             slot: DIMM1
             size: 128MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PSD256400
             vendor: JEDEC ID:7F 7F 7F 7F 7F 02 00 00
             physical id: 1
             serial: 00000000
             slot: DIMM2
             size: 256MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: NT128D64SH4B1G-5T
             vendor: JEDEC ID:7F 7F 7F 0B 00 00 00 00
             physical id: 2
             serial: 00000000
             slot: DIMM3
             size: 128MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: PSD256400
             vendor: JEDEC ID:7F 7F 7F 7F 7F 02 00 00
             physical id: 3
             serial: 00000000
             slot: DIMM4
             size: 256MB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 28
          slot: System board or motherboard
          capacity: 512KB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-cpu:1
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@1
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:f0000000-f7ffffff iomemory:fc400000-fc47ffff ioport:14d0-14d7 irq:185
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1440-145f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1460-147f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1480-149f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:fc480000-fc4803ff irq:177
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5782 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@05:02.0
                logical name: eth0
                version: 03
                serial: 00:11:85:b4:ba:f3
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5782-v3.13 ip=192.168.0.103 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:fc500000-fc50ffff irq:209
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:14c0-14cf iomemory:40000000-400003ff irq:169
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD800BB-22HEA1
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 14.03G14
                   serial: WD-WCAJ51177853
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 20GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 53GB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: IDE CD-ROM
                   product: SAMSUNG CD-ROM SC-148A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: B404
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:1000-10ff ioport:1400-143f iomemory:fc480400-fc4805ff iomemory:fc480600-fc4806ff irq:201

```

lspci
```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)

```

---

