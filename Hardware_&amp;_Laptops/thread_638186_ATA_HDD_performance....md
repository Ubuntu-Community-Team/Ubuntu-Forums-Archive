---
title: "ATA HDD performance..."
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by tjodSK on 2007-12-11
Hi !

i have replaced hdd in my laptop, and i think it performs better in win than in Ubuntu, which is weird...

i ran
```
sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   784 MB in  2.00 seconds = 392.06 MB/sec
 Timing buffered disk reads:  116 MB in  3.03 seconds =  38.28 MB/sec


```

and
```
sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       ST9100828A
        Serial Number:      5LZ4PYW7
        Firmware Revision:  3.ALD
Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 2
        Supported: 6 5 4
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  195371568
        LBA48  user addressable sectors:  195371568
        device size with M = 1024*1024:       95396 MBytes
        device size with M = 1000*1000:      100030 MBytes (100 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x8080)
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
```


are these values "just okay" for 100gig Seagate 5400rpm ide disk?

i'm comlete new to ubuntu and this forum:)

---

### Post by tgalati4 on 2007-12-11
Those are excellent numbers.  You are getting 38.3 MB/sec which is quite fast for a 5400 rpm disk.  To get more speed you will have to go to 7200 rpm.  I don't think I've seen a 10K laptop drive.  That will get you around 40-45 MB/sec.  You are running the fastest data transfer mode (udma5) that your drive supports.

Windows will perform better if its Win 98 SE on a 128 MB RAM machine.  Since you didn't give us any specs on your machine, we can't comment on performance.

---

### Post by tjodSK on 2007-12-11
So, i have a 1.5Ghz celeron, 780megs of ram, and 100gb ata Seagate... I'm running dualboot with winXP prof.

can be this factor slowing down?
i originally installed kubuntu, but recently i found out i like much more gnome, so i just installed gnome-desktop via apt, and now i'm using gnome primary... i know it's a bit OT but you might know...

---

### Post by tgalati4 on 2007-12-11
Try running a Live CD of Mint 4 which is based on Gutsy and XFCE window environment.  See if that's faster for you.  KDE is a heavier window environment.  Because you installed Gnome over it, you may have KDE parts still running which will make it seem heavy.

I assume you have built-in graphics (perhaps Intel) and that will also be a factor in perceived speed.

Post the output of:

> lspci -vv

Also, immediately after boot, post your processes that are running:

>ps -ef

---

### Post by tjodSK on 2007-12-12
i have crappy SiS661 integrated card, using sis xorg driver....

i will post those logs soon,

thank you very much.

---

### Post by tgalati4 on 2007-12-12
I have a desktop with a SIS630 graphics chip.  It is also seems slower than in Windows, so that could be the reason.  The Windows driver is custom-written and works reasonably well.  The open-source driver is reverse-engineered (I believe) and so it's laggy.

You can run a benchmark, such as super_pi which is available in both Windows and Linux to get a number-crunching comparison.  They should be the same or slightly faster in Linux.

The graphics performance really affects the "feel" of speed.  Not much you can do about it as you can't change the graphics chip in a laptop.

---

### Post by tjodSK on 2007-12-12
i got this:
```

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 19:57 ?        00:00:01 /sbin/init
root         2     0  0 19:57 ?        00:00:00 [kthreadd]
root         3     2  0 19:57 ?        00:00:00 [migration/0]
root         4     2  0 19:57 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 19:57 ?        00:00:00 [watchdog/0]
root         6     2  0 19:57 ?        00:00:00 [events/0]
root         7     2  0 19:57 ?        00:00:00 [khelper]
root        26     2  0 19:57 ?        00:00:00 [kblockd/0]
root        27     2  0 19:57 ?        00:00:00 [kacpid]
root        28     2  0 19:57 ?        00:00:00 [kacpi_notify]
root       103     2  0 19:57 ?        00:00:00 [kseriod]
root       122     2  0 19:57 ?        00:00:00 [pdflush]
root       123     2  0 19:57 ?        00:00:00 [pdflush]
root       124     2  0 19:57 ?        00:00:00 [kswapd0]
root       175     2  0 19:57 ?        00:00:00 [aio/0]
root      2025     2  0 19:57 ?        00:00:00 [ata/0]
root      2026     2  0 19:57 ?        00:00:00 [ata_aux]
root      2028     2  0 19:57 ?        00:00:00 [scsi_eh_0]
root      2029     2  0 19:57 ?        00:00:00 [scsi_eh_1]
root      2053     2  0 19:57 ?        00:00:00 [ksuspend_usbd]
root      2054     2  0 19:57 ?        00:00:00 [khubd]
root      2421     2  0 19:57 ?        00:00:00 [kjournald]
root      3789     1  0 19:57 ?        00:00:00 /sbin/udevd --daemon
root      4830     2  0 19:57 ?        00:00:00 [pccardd]
root      4877     2  0 19:57 ?        00:00:00 [kpsmoused]
dhcp      5391     1  0 19:57 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.lea
root      5589     1  0 19:57 ?        00:00:00 /sbin/mount.ntfs-3g /dev/sda1 /media/hda1 -o rw,locale=en_US.UTF-8
root      5604     1  0 19:57 ?        00:00:01 /sbin/mount.ntfs-3g /dev/sda2 /media/hda2 -o rw,locale=en_US.UTF-8
daemon    5726     1  0 19:57 ?        00:00:00 /sbin/portmap
statd     5805     1  0 19:57 ?        00:00:00 /sbin/rpc.statd
root      5956     1  0 19:57 tty4     00:00:00 /sbin/getty 38400 tty4
root      5957     1  0 19:57 tty5     00:00:00 /sbin/getty 38400 tty5
root      5960     1  0 19:57 tty2     00:00:00 /sbin/getty 38400 tty2
root      5961     1  0 19:57 tty3     00:00:00 /sbin/getty 38400 tty3
root      5962     1  0 19:57 tty1     00:00:00 /sbin/getty 38400 tty1
root      5963     1  0 19:57 tty6     00:00:00 /sbin/getty 38400 tty6
root      6210     1  0 19:57 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      6264     2  0 19:57 ?        00:00:00 [kondemand/0]
syslog    6333     1  0 19:57 ?        00:00:00 /sbin/syslogd -u syslog
root      6397     1  0 19:57 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      6399     1  0 19:57 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
104       6432     1  0 19:57 ?        00:00:00 /usr/bin/dbus-daemon --system
root      6448     1  0 19:57 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      6470     1  0 19:57 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher
root      6487     1  0 19:57 ?        00:00:00 /usr/bin/system-tools-backends
root      6488  6487  0 19:57 ?        00:00:00 dbus-daemon --session --print-address --nofork
107       6507     1  0 19:57 ?        00:00:00 /usr/sbin/hald
root      6508  6507  0 19:57 ?        00:00:00 hald-runner
107       6575  6508  0 19:57 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event1
107       6576  6508  0 19:57 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event10
107       6577  6508  0 19:57 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event4
107       6578  6508  0 19:57 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event5
107       6579  6508  0 19:57 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event7
107       6582  6508  0 19:57 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       6611  6508  0 19:57 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event8
107       6612  6508  0 19:57 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event9
root      6649     1  0 19:57 ?        00:00:00 /usr/sbin/gdm
107       6689  6508  0 19:57 ?        00:00:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      6915     1  0 19:58 ?        00:00:00 /usr/sbin/cupsd
root      6976     1  0 19:58 ?        00:00:00 ptal-mlcd mlc:usb:psc_1200_series -devidmatch MDL:psc 1200 series; -devidmatch SN:MY35NC12CR5H
root      6979     1  0 19:58 ?        00:00:00 ptal-printd mlc:usb:psc_1200_series -morepipes 9 -like /etc/ptal/ptal-printd-like
root      7023     1  0 19:58 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     7067  7023  0 19:58 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysq
root      7068  7023  0 19:58 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      7258     1  0 19:58 ?        00:00:00 /usr/bin/dirmngr --daemon --sh
root      7456     2  0 19:58 ?        00:00:00 [lockd]
root      7457     2  0 19:58 ?        00:00:00 [rpciod/0]
root      7461     2  0 19:58 ?        00:00:00 [nfsd4]
root      7462     2  0 19:58 ?        00:00:00 [nfsd]
root      7463     2  0 19:58 ?        00:00:00 [nfsd]
root      7464     2  0 19:58 ?        00:00:00 [nfsd]
root      7465     2  0 19:58 ?        00:00:00 [nfsd]
root      7466     2  0 19:58 ?        00:00:00 [nfsd]
root      7467     2  0 19:58 ?        00:00:00 [nfsd]
root      7468     2  0 19:58 ?        00:00:00 [nfsd]
root      7469     2  0 19:58 ?        00:00:00 [nfsd]
root      7485     1  0 19:58 ?        00:00:00 /usr/sbin/rpc.mountd
root      7535     1  0 19:58 ?        00:00:00 /usr/sbin/nmbd -D
root      7549     1  0 19:58 ?        00:00:00 /usr/sbin/smbd -D
root      7606  7549  0 19:58 ?        00:00:00 /usr/sbin/smbd -D
root      7607     1  0 19:58 ?        00:00:00 /usr/sbin/winbindd
root      7691     1  0 19:58 ?        00:00:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
root      7696     1  0 19:58 ?        00:00:00 /usr/sbin/console-kit-daemon
root      7718  7607  0 19:58 ?        00:00:00 /usr/sbin/winbindd
avahi     7778     1  0 19:58 ?        00:00:00 avahi-daemon: running [PC-Jacalam.local]
avahi     7779  7778  0 19:58 ?        00:00:00 avahi-daemon: chroot helper
root      7793     1  0 19:58 ?        00:00:00 /usr/sbin/dhcdbd --system
root      7821     1  0 19:58 ?        00:00:00 /usr/sbin/hcid -x -s
root      7840     2  0 19:58 ?        00:00:00 [krfcommd]
root      7841  7821  0 19:58 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-input
root      7861  7821  0 19:58 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-audio
ntp       7862     1  0 19:58 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 113:123 -g
daemon    7915     1  0 19:58 ?        00:00:00 /usr/sbin/atd
root      7937     1  0 19:58 ?        00:00:00 /usr/sbin/cron
root      8029     1  0 19:58 ?        00:00:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0
root      8043     1  0 19:58 ?        00:00:00 /usr/bin/vmnet-natd -d /var/run/vmnet-natd-8.pid -m /var/run/vmnet-natd-8.mac -c /etc/vmware/v
root      8051     1  0 19:58 ?        00:00:00 /usr/sbin/vmware-serverd -s -d
root      8101     1  0 19:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  8173  8101  0 19:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  8174  8101  0 19:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  8175  8101  0 19:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  8176  8101  0 19:58 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  8177  8101  0 19:58 ?        00:00:00 /usr/sbin/apache2 -k start
root      8215     1  0 19:58 ?        00:00:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet8.pid /dev/vmnet8 vmnet8
root      8226     1  0 19:58 ?        00:00:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet1.pid /dev/vmnet1 vmnet1
root      8236     1  0 19:58 ?        00:00:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet1/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet1/dhcpd/dhcp
root      8237     1  0 19:58 ?        00:00:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet8/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet8/dhcpd/dhcp
root      8267     1  0 19:58 ?        00:00:00 /usr/bin/timidity -Os -iAD
martinko  8341     1  0 19:58 ?        00:00:00 /usr/bin/gpg-agent --daemon --sh
root      8502  7607  0 19:59 ?        00:00:00 /usr/sbin/winbindd
root      8503  7607  0 19:59 ?        00:00:00 /usr/sbin/winbindd
martinko  8713     1  2 20:06 ?        00:01:18 python /home/martinko/.kde/share/apps/amarok/scripts/AmarokPidgin/AmarokPidgin.py
root      9729  6649  0 20:58 ?        00:00:00 /usr/sbin/gdm
root      9734  9729  4 20:58 tty9     00:00:04 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt9
martinko  9762  9729  0 20:58 ?        00:00:00 /usr/bin/gnome-session
martinko  9816  9762  0 20:58 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
martinko  9819     1  0 20:58 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
martinko  9820     1  0 20:58 ?        00:00:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
martinko  9822     1  0 20:58 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 6
martinko  9825     1  0 20:58 ?        00:00:00 /usr/bin/gnome-keyring-daemon
martinko  9827     1  0 20:58 ?        00:00:00 /usr/lib/gnome-control-center/gnome-settings-daemon
martinko  9833  9762  0 20:58 ?        00:00:00 /usr/bin/metacity --sm-client-id=default0
martinko  9835  9762  2 20:58 ?        00:00:01 gnome-panel --sm-client-id default1
martinko  9836  9762  1 20:58 ?        00:00:00 nautilus --no-default-window --sm-client-id default2
martinko  9840     1  0 20:58 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
martinko  9841     1  0 20:58 ?        00:00:00 gnome-volume-manager --sm-client-id default4
martinko  9843     1  0 20:58 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
martinko  9854  9762  0 20:58 ?        00:00:00 vino-session --sm-client-id default5
martinko  9855  9762  0 20:58 ?        00:00:00 bluetooth-applet
martinko  9857  9762  0 20:58 ?        00:00:00 update-notifier
martinko  9858  9762  0 20:58 ?        00:00:00 /usr/lib/evolution/2.12/evolution-alarm-notify
martinko  9864  9762  0 20:58 ?        00:00:00 python /usr/share/system-config-printer/applet.py
martinko  9868  9762  0 20:58 ?        00:00:00 nm-applet --sm-disable
martinko  9872     1  0 20:58 ?        00:00:00 gnome-power-manager
martinko  9879     1  0 20:58 ?        00:00:00 gnome-screensaver
martinko  9894     1  0 20:58 ?        00:00:00 /usr/lib/evolution/evolution-data-server-1.12 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataSe
martinko  9902     1  0 20:58 ?        00:00:00 /usr/lib/evolution/2.12/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_E
martinko  9923     1  0 20:58 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory -
martinko  9943     1  0 20:58 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapping-daemon
martinko  9952     1  0 20:59 ?        00:00:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Fact
martinko  9960     1  0 20:59 ?        00:00:00 /usr/lib/gnome-applets/gweather-applet-2 --oaf-activate-iid=OAFIID:GNOME_GWeatherApplet_Factor
martinko  9962     1  0 20:59 ?        00:00:00 python /usr/lib/gnome-applets/computertemp --oaf-activate-iid=OAFIID:GNOME_ComputertempApplet_
martinko  9964     1  0 20:59 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf
martinko  9966     1  0 20:59 ?        00:00:00 /usr/lib/gnome-applets/gnome-keyboard-applet --oaf-activate-iid=OAFIID:GNOME_KeyboardApplet_Fa
martinko  9975     1  1 20:59 ?        00:00:00 konsole
martinko  9978     1  0 20:59 ?        00:00:00 kdeinit Running...
martinko  9981     1  0 20:59 ?        00:00:00 dcopserver [kdeinit] --n
martinko  9984  9978  0 20:59 ?        00:00:00 klauncher [kdeinit]
martinko  9986     1  0 20:59 ?        00:00:00 kded [kdeinit]
martinko  9989  9975  0 20:59 pts/0    00:00:00 /bin/bash
martinko 10013  9989  0 20:59 pts/0    00:00:00 ps -ef


```


```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 64
        Region 0: Memory at e0000000 (32-bit, non-prefetchable) [size=32M]
        Capabilities: [c0] AGP version 3.5
                Status: RQ=32 Iso- ArqSz=2 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: e2100000-e21fffff
        Prefetchable memory behind bridge: e8000000-efffffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 0
        Region 4: I/O ports at 8100 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Acer Incorporated [ALI] Unknown device 0082
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128
        Interrupt: pin ? routed to IRQ 18
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        Region 4: I/O ports at 1000 [size=16]

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: Acer Incorporated [ALI] Unknown device 0082
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 17
        Region 0: I/O ports at 1400 [size=256]
        Region 1: I/O ports at 1080 [size=128]
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Acer Incorporated [ALI] Unknown device 0082
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 173 (13000ns min, 2750ns max)
        Interrupt: pin C routed to IRQ 17
        Region 0: I/O ports at 1c00 [size=256]
        Region 1: I/O ports at 1800 [size=128]
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0082
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at e2000000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0082
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin B routed to IRQ 20
        Region 0: Memory at e2001000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0082
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max), Cache Line Size: 32 bytes
        Interrupt: pin D routed to IRQ 21
        Region 0: Memory at e2002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
        Subsystem: Acer Incorporated [ALI] Unknown device 0082
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 173 (13000ns min, 2750ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 2000 [size=256]
        Region 1: Memory at e2003000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 48000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0082
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at 48020000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 44000000-47fff000
        I/O window 0: 00002400-000024ff
        I/O window 1: 00002800-000028ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0082
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 7
        BIST result: 00
        Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Region 1: Memory at e2100000 (32-bit, non-prefetchable) [size=128K]
        Region 2: I/O ports at 9000 [size=128]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] AGP version 3.0
                Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>



```


Thanks for your time!

---

### Post by tjodSK on 2007-12-12
Hi... it's me again...

its weird, but things like Opera, Konsole (i use this in gnome) and other apps works just "smoother" inn KDE than in Gnome, it's really strange thing...

i know konsole is an KDE app, but in gnome it takes at least secs to load, and in KDE it's like in a second,
opera i think loads twice as fast as in gnome, its weird...

it looks like kde is "interferring" with gnome even if i'm logged only in gnome...

thank you again.

---

### Post by IeU on 2007-12-14
> **tgalati4 said:**
> Those are excellent numbers.  You are getting 38.3 MB/sec which is quite fast for a 5400 rpm disk.  To get more speed you will have to go to 7200 rpm.  I don't think I've seen a 10K laptop drive.  That will get you around 40-45 MB/sec.  You are running the fastest data transfer mode (udma5) that your drive supports.

Windows will perform better if its Win 98 SE on a 128 MB RAM machine.  Since you didn't give us any specs on your machine, we can't comment on performance.

just for some feedback . . .

**This being a +4 years old seagate 160gb 7.2k rpm . linux is installed here**
```
[root@minwinpc home]# hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       ST3160023AS                             
        Serial Number:      3JS43A5S            
        Firmware Revision:  3.18    
Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 2 
        Supported: 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  312581808
        device size with M = 1024*1024:      152627 MBytes
        device size with M = 1000*1000:      160041 MBytes (160 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard
        R/W multiple sector transfer: Max = 16  Current = 1
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    SATA-I signaling speed (1.5Gb/s)
Security: 
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct

``````

[root@minwinpc home]# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1362 MB in  2.00 seconds = 681.20 MB/sec
 Timing buffered disk reads:  160 MB in  3.03 seconds =  52.88 MB/sec
[root@minwinpc home]# 
```




**This here being a not even 1 year old XRaptor 10k rpm, windows is here (ntfs)**
```
[root@minwinpc home]# hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
        Model Number:       WDC WD1500AHFD-00RAR1                   
        Serial Number:      WD-WMAP41541601
        Firmware Revision:  20.07P20
Standards:
        Used: ATA/ATAPI-7 published, ANSI INCITS 397-2005 
        Supported: 7 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  293046768
        device size with M = 1024*1024:      143089 MBytes
        device size with M = 1000*1000:      150039 MBytes (150 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 1
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
                Power-Up In Standby feature set
           *    SET_FEATURES required to spinup after power up
                SET_MAX security extension
           *    Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    SATA-I signaling speed (1.5Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
                DMA Setup Auto-Activate optimization
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT LBA Segment Access (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
                unknown 206[12]
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct

```
```
/dev/sdb:
 Timing cached reads:   1316 MB in  2.00 seconds = 658.08 MB/sec
 Timing buffered disk reads:  244 MB in  3.01 seconds =  81.55 MB/sec
[root@minwinpc home]# 
```


**This being a not even 1 year old WD500Gb drive. nothing here, not even a partition :)**
```
[root@minwinpc home]# hdparm -I /dev/sdc

/dev/sdc:

ATA device, with non-removable media
        Model Number:       WDC WD5000AAKS-00TMA0                   
        Serial Number:      WD-WCAPW0420271
        Firmware Revision:  12.01C01
Standards:
        Supported: 7 6 5 4 
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  976773168
        device size with M = 1024*1024:      476940 MBytes
        device size with M = 1000*1000:      500107 MBytes (500 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 1
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
                Power-Up In Standby feature set
           *    SET_FEATURES required to spinup after power up
                SET_MAX security extension
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    64-bit World wide name
           *    Segmented DOWNLOAD_MICROCODE
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
                DMA Setup Auto-Activate optimization
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT LBA Segment Access (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
                unknown 206[12]
                unknown 206[13]
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
        128min for SECURITY ERASE UNIT. 
Checksum: correct
```
```
[root@minwinpc home]# hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   1236 MB in  2.00 seconds = 617.83 MB/sec
 Timing buffered disk reads:  244 MB in  3.01 seconds =  81.09 MB/sec
[root@minwinpc home]# 

```

the new WD500 almost outperforming the new WD-Raptor150 ?

is this right ? do i have to enable any option on my Raptor to perform better ?

---

### Post by tgalati4 on 2008-03-18
Make sure ncq is turned off for your Raptor.  You can check your dmesg for the following:

Bad:

ata2.00: ATA-7, max UDMA/133, 321672960 sectors: LBA48 NCQ (depth 31/32)

Good:

ata2.00: ATA-7, max UDMA/133, 321672960 sectors: LBA48 NCQ (depth 0/32)

Also, there are several flavors of Raptors with 8 MB and 16 MB caches and different firmware.  You would have to do some research on your particular one to see if there are any tweaks available.

What's the warranty difference between the 2 drives?

---

