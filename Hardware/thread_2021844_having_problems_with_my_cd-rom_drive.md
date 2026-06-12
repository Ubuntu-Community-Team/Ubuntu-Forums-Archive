---
title: "having problems with my cd-rom drive"
date: 2012-07-09
forum: Hardware
---

### Post by IlikeMoose on 2012-07-09
i keep getting the following error code when trying to eject my cd-rom  drive, the only way i can get it to eject is by powering off.

Error ejecting: eject exited with exit code 1: eject: unable to eject, last error: Inappropriate ioctl for device

mike@hackbox:~$ eject -rv
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/sr0'
eject: `/dev/sr0' is not mounted
eject: `/dev/sr0' is not a mount point
eject: `/dev/sr0' is not a multipartition device
eject: trying to eject `/dev/sr0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: unable to eject, last error: Input/output error
mike@hackbox:~$ eject cdrom
eject: unable to eject, last error: Inappropriate ioctl for device

i know the drive works because i ripped 2 audio cd's last night, at  first i thought the problem was rhythmbox but i uninstalled it and  installed audacious and everything was working. this is the same cd-rom  drive i used for the ubuntu install and i didn't have a single problem.  please help me!!!!:sad:

---

### Post by jmfal on 2012-07-09
Welcome to Ubuntu, 

 Sometimes in a fresh install the eject app is not installed, try this

```
 sudo apt-get install libcdaudio1    
```

That should do it, but if it doesn't try

```
 sudo apt-get install eject   
```

you won't need to remove libcdaudio.

---

### Post by IlikeMoose on 2012-07-09
tried both, i had the newest version when i tried to install each one, any other suggestions? when i reboot it works for a while but then it seems something locks it up, sometimes when i try to eject it the disc will spin up really fast and won't spin down until i shut the machine off.

---

### Post by jmfal on 2012-07-09
When the cd-rom is running there should be an icon for it on the desktop, right click on it and click eject.

If there is no icon, click on desktop and click eject

---

### Post by IlikeMoose on 2012-07-09
Tried that, all i get it this:

Error ejecting: eject exited with exit code 1: eject: unable to eject, last error: Inappropriate ioctl for device

And then i have to reboot to get the disc out

---

### Post by jmfal on 2012-07-09
OK  run this in a terminal

```
  lspci -v    
```

and copy/paste the output between the brackets of the code tag #
need to see if cdrom is recognized

---

### Post by IlikeMoose on 2012-07-09
here goes!:
```

mike@hackbox:~$ sudo lspci -v
[sudo] password for mike: 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e0400000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 10c0 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at e0480000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at e04c0000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=20, subordinate=20, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 60200000-603fffff
    Prefetchable memory behind bridge: 0000000060400000-00000000605fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Hewlett-Packard Company Device 3012
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=3f, subordinate=3f, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: e0500000-e07fffff
    Prefetchable memory behind bridge: 0000000060000000-00000000601fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Hewlett-Packard Company Device 3012
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 1060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at e04c4000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: [50] Subsystem: Hewlett-Packard Company Device 3012

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 10a0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 10d8 [size=8]
    I/O ports at 10f0 [size=4]
    I/O ports at 10e0 [size=8]
    I/O ports at 10f4 [size=4]
    I/O ports at 10b0 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

3f:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 01)
    Subsystem: Hewlett-Packard Company Device 3012
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at e0500000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Vital Product Data
    Capabilities: [58] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Kernel driver in use: tg3
    Kernel modules: tg3


```

---

### Post by jmfal on 2012-07-09
Alright I don't see it there. Are you on a laptop??

Try this

```
   sudo lshw -C disk    
```

---

### Post by IlikeMoose on 2012-07-09
i'm on an ancient hp compaq dc7600 ultra slim desktop
dc7600u/p4-521/34471/

here's the outpot from that last command you gave me

```
mike@hackbox:~$ sudo lshw -C disk
[sudo] password for mike: 
PCI (sysfs)  

  *-cdrom                 
       description: SCSI CD-ROM
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       capabilities: audio
       configuration: status=nodisc
  *-disk
       description: ATA Disk
       product: ST3402112AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.BH
       serial: 9LR0XAAJ
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0005ffb5

```

---

### Post by jmfal on 2012-07-09
Your going to have to do some research on this, Ill be back in A.M.

Try googling "ubuntu 12.04 compaq dc7600 cdrom eject problems"

and see what comes up.

Or you can try the "search this forum" tag above, and enter  a similar phrase.

---

### Post by IlikeMoose on 2012-07-09
note: this also seems to be an intermittent problem. i restarted about 45 minutes ago and the drive seems to be ok now.  I've ripped another CD and it seems to be accepting and ejecting discs normally now. I'm just wondering if there's some kind of permanent fix for this or if i should report it as a bug.

---

### Post by jmfal on 2012-07-09
Maybe restarting set the installation of eject in place.

---

### Post by George Heine on 2013-01-02
Is anyone still looking at this thread?
I started experiencing the same problem as IlikeMoose(unable to eject disk) with my HP Compaq nc2400.  This is a laptop with builtin cd drive; there is also an external DVD drive plugged into a USB port.  Running Ubuntu 12.04 since September, and have used command-line eject dozens of times since then.  But today, i get errors:
```
gheine@ganesh:~$ eject /dev/sr0
eject: unable to eject, last error: Inappropriate ioctl for device
```/dev/sr0 is the internal CD-drive.  Just tried the external drive : 
```
gheine@ganesh:~$ eject /dev/sr1
```and the tray opened with normally.

Here is the output of 

```
gheine@ganesh:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK6008GA
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: BU02
       serial: 9743W6NUW
       size: 55GiB (60GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000cee4
  *-cdrom
       description: DVD reader
       product: UJDA775 DVD/CDRW
       vendor: MATSHITA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/sr0
       version: 1.21
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       product: External USB 3.0
       vendor: TOSHIBA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 0001
       serial: Y1TGF5QHS
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=6 signature=155f9ff9
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GE24LU20
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/sr1
       version: OL00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc

```Thanks for any help!

---

### Post by Wray on 2013-01-02
> **jmfal said:**
> Welcome to Ubuntu, 

 Sometimes in a fresh install the eject app is not installed, try this

```
 sudo apt-get install libcdaudio1    
```That should do it, but if it doesn't try

```
 sudo apt-get install eject   
```you won't need to remove libcdaudio.

sudo apt-get install eject fixed my problem also...thanks

---

### Post by George Heine on 2013-03-09
This appears to be[ bug 875543]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/875543").

---

