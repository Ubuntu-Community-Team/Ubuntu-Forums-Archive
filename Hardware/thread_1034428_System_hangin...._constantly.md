---
title: "System hangin.... constantly"
date: 2009-01-08
forum: Hardware
---

### Post by Melvin Udall on 2009-01-08
Hey everyone,
i joined simply so i could post this question. 

I've been using Ubuntu since Feisty.

Anyway, my system has, I THINK since installing Ibex, started to hang, and i can see on the system monitor that I/O is at 100%, so then everything just stalls, FF or Opera, Pidgin, Rhythmbox... everything, and then depending on the length of the hand (which can last as long as 2 minutes) the system then catches up with itself, so Rhythmbox will skip past the 2 mins its lost, pidgin will print all the text that has been received during the hang time, and FF or Opera will load the page or scroll down to where i was supposed to be goin. But during this time the comp is unusable.

at first i thought it may have been the HDD, so i bought a new one, cus the old one was 3 years old and only 80 gigs and a little shagged, so i thought it was a welcome problem, but the problem is still here.

I have an Acer Aspire 9500, Intel Pentium M 1.7, 2g ram. 

I also have a NUMBER of Dmesg's, so ill print one of them. It seems like there is something wrong with the HDD, but im confused.

ANY HELP is greatly appreciated

[   16.647090] mmc1: SDHCI controller on PCI [0000:05:04.4] using PIO
[   17.109928] cs: IO port probe 0x100-0x3af: clean.
[   17.111611] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.112360] cs: IO port probe 0x820-0x8ff: clean.
[   17.112961] cs: IO port probe 0xc00-0xcf7: clean.
[   17.113730] cs: IO port probe 0xa00-0xaff: clean.
[   18.002160] lp0: using parport0 (interrupt-driven).
[   18.129875] Adding 2441872k swap on /dev/sda2.  Priority:-1 extents:1 across:2441872k
[   18.679088] EXT3 FS on sda1, internal journal
[   19.634855] kjournald starting.  Commit interval 5 seconds
[   19.635318] EXT3 FS on sda3, internal journal
[   19.635324] EXT3-fs: mounted filesystem with ordered data mode.
[   19.950886] type=1505 audit(1231421394.098:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4023
[   20.175818] type=1505 audit(1231421394.322:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4028
[   20.176179] type=1505 audit(1231421394.326:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4028
[   20.351727] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.831790] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.918475] apm: BIOS not found.
[   22.273171] ppdev: user-space parallel port driver
[   23.310426] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   23.310435] vboxdrv: Successfully done.
[   23.310437] vboxdrv: Found 1 processor cores.
[   23.312094] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   23.312104] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   25.030538] Bluetooth: Core ver 2.13
[   25.033423] NET: Registered protocol family 31
[   25.033433] Bluetooth: HCI device and connection manager initialized
[   25.033439] Bluetooth: HCI socket layer initialized
[   25.095640] Bluetooth: L2CAP ver 2.11
[   25.095652] Bluetooth: L2CAP socket layer initialized
[   25.138197] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.138205] Bluetooth: BNEP filters: protocol multicast
[   25.179230] Bridge firewalling registered
[   25.180264] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   25.219291] Bluetooth: SCO (Voice Link) ver 0.6
[   25.219300] Bluetooth: SCO socket layer initialized
[   25.236908] Bluetooth: RFCOMM socket layer initialized
[   25.237189] Bluetooth: RFCOMM TTY layer initialized
[   25.237198] Bluetooth: RFCOMM ver 1.10
[   29.206565] [drm] Initialized drm 1.1.0 20060810
[   29.227651] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.227663] pci 0000:00:02.0: setting latency timer to 64
[   29.230467] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   29.336512] r8169: eth0: link down
[   29.480046] NET: Registered protocol family 17
[   58.272888] ieee80211_crypt: registered algorithm 'CCMP'
[   58.992605] padlock: VIA PadLock not detected.
[   72.077313] NET: Registered protocol family 10
[   72.079311] lo: Disabled Privacy Extensions
[   72.080999] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   82.812017] eth1: no IPv6 routers present
[ 1666.776217] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 1666.776253] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 1666.776258]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1666.776263]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 1666.776275] ata1.01: status: { DRDY }
[ 1666.776299] ata1: soft resetting link
[ 1667.256185] ata1.00: configured for UDMA/100
[ 1667.256203] ata1.01: configured for UDMA/33
[ 1667.256226] ata1: EH complete
[ 1667.257919] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 1667.259303] sd 0:0:0:0: [sda] Write Protect is off
[ 1667.259320] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1667.297102] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1667.301101] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 1667.334318] sd 0:0:0:0: [sda] Write Protect is off
[ 1667.334335] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1667.335592] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2915.780129] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2915.780166] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 2915.780170]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 2915.780175]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 2915.780187] ata1.01: status: { DRDY }
[ 2915.780211] ata1: soft resetting link
[ 2916.252700] ata1.00: configured for UDMA/100
[ 2916.252719] ata1.01: configured for UDMA/33
[ 2916.252742] ata1: EH complete
[ 2916.260205] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 2916.264432] sd 0:0:0:0: [sda] Write Protect is off
[ 2916.264450] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2916.270353] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2916.323477] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 2916.323809] sd 0:0:0:0: [sda] Write Protect is off
[ 2916.323819] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2916.328849] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3764.776121] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3764.776156] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 3764.776161]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3764.776166]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 3764.776177] ata1.01: status: { DRDY }
[ 3764.776201] ata1: soft resetting link
[ 3765.251583] ata1.00: configured for UDMA/100
[ 3765.251600] ata1.01: configured for UDMA/33
[ 3765.251624] ata1: EH complete
[ 3765.254109] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 3765.254858] sd 0:0:0:0: [sda] Write Protect is off
[ 3765.254867] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3765.258087] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3765.260793] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 3765.262944] sd 0:0:0:0: [sda] Write Protect is off
[ 3765.262961] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3765.288599] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4829.452147] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 4829.452180] ata1.00: cmd 35/00:d0:d0:db:7a/00:00:14:00:00/e0 tag 0 dma 106496 out
[ 4829.452185]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 4829.452196] ata1.00: status: { DRDY }
[ 4829.452220] ata1: soft resetting link
[ 4829.701699] ata1.00: configured for UDMA/100
[ 4829.701718] ata1.01: configured for UDMA/33
[ 4829.701743] ata1: EH complete
[ 4829.707516] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 4829.709892] sd 0:0:0:0: [sda] Write Protect is off
[ 4829.709909] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4829.717462] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4829.722100] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 4829.730247] sd 0:0:0:0: [sda] Write Protect is off
[ 4829.730265] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4829.736298] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5407.780129] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5407.780166] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 5407.780171]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 5407.780176]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 5407.780187] ata1.01: status: { DRDY }
[ 5407.780212] ata1: soft resetting link
[ 5408.252457] ata1.00: configured for UDMA/100
[ 5408.252476] ata1.01: configured for UDMA/33
[ 5408.252500] ata1: EH complete
[ 5408.258217] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 5408.275705] sd 0:0:0:0: [sda] Write Protect is off
[ 5408.275723] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5408.279850] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5408.327405] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 5408.327951] sd 0:0:0:0: [sda] Write Protect is off
[ 5408.327969] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5408.329434] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by namdung on 2009-01-08
I've seen/heard/experienced too many issues with Intrepid that I strongly recommend the much stable Hardy Heron 8.04 LTS with 3 yrs support. Intrepid may have more features but also has more bugs. 

The next release of Hardy 8.04.2 is anytime now.
[https://launchpad.net/ubuntu/+milestones](https://launchpad.net/ubuntu/+milestones)

---

### Post by linux_tech on 2009-01-08
You should start by scanning the HD using Bonager or else boot to live cd and run fsck.

You can also run fsck at next reboot by typing :
```
sudo touch /forcefsck
```

 Bonager info here:
[http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

---

### Post by markbuntu on 2009-01-08
The first thing you should do is look in the log files for error messages. You might not see any but then again, you might and if you do they will help you figure out what is going on.

---

