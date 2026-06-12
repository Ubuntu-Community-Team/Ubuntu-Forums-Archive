---
title: "[SOLVED] LaCie Network Space 1TB compatible?"
date: 2008-10-05
forum: Hardware
---

### Post by stormtrooprdave on 2008-10-05
Does anyone know if this is fully compatible with Ubuntu?

[http://www.lacie.com/uk/products/product.htm?pid=11090]("http://www.lacie.com/uk/products/product.htm?pid=11090")

---

### Post by matthiayer on 2008-11-06
> **stormtrooprdave said:**
> Does anyone know if this is fully compatible with Ubuntu?

[http://www.lacie.com/uk/products/product.htm?pid=11090]("http://www.lacie.com/uk/products/product.htm?pid=11090")
can somebody answer this question already?

i'm doubting about a network drive too, and this one is very cheep here!!

or should i buy a wd my book world?

thanks

---

### Post by stormtrooprdave on 2008-11-08
If you follow the link and download the manual it mentions linux in the minimum system requirements section on page 6.  It says you need linux 2.4 and a web browser, but that is the only mention of linux in the whole manual.

---

### Post by stormtrooprdave on 2008-11-20
I bought this and it is fully compatible with Ubuntu.  I have it to automount on startup and works no problem

---

### Post by Daan on 2008-11-21
> **stormtrooprdave said:**
> I bought this and it is fully compatible with Ubuntu.  I have it to automount on startup and works no problem

And it should. From the manual at [http://www.lacie.com/download/manual/networkspace_en.pdf:](http://www.lacie.com/download/manual/networkspace_en.pdf:)

"The LaCie Network Space is compatible with Mac®, Windows® and Linux machines"

You can even hook up an ext3 formatted drive to its usb port.

I'm getting one tomorrow. :-)

---

### Post by Daan on 2008-11-21
[At its website]("http://www.lacie.com/uk/support/drivers/driver.htm?id=10117") Lacie says that the Linux version of its Ethernet Agent application is still under development, and it cannot be downloaded. But most configuration is done via a web browser, so no real problem here.

From the manual I get that there are only two accounts on the file server of the device, "Administrator" and "user", and that rights cannot be managed in a very advanced way. There is "MyShare", which can only be accessed by the admin and there is the public share that can be accessed by everyone on the LAN through SMB and by the user via FTP.

---

### Post by Daan on 2008-11-22
I got mine now and it works fine with my Debian Lenny. I did not need the Lacie Ethernet Agent, a web browser is sufficient to configure the Network Space. From its log file I see that the device is operated by a Linux OS.

The log file:
```
Jan  1 00:00:23 (none) syslog.info syslogd started: BusyBox v1.1.0 (2006.11.03-14:53+0000)
Jan  1 00:00:24 (none) user.notice kernel: klogd started: BusyBox v1.1.0 (2006.11.03-14:53+0000)
Jan  1 00:00:24 (none) user.notice kernel: Linux version 2.6.12.6-arm1 (jrichefeu@grp-horus) (gcc version 3.4.4 (release) (CodeSourcery ARM 2005q3-2)) #2 Thu Aug 14 16:36:28 CEST 2008
Jan  1 00:00:24 (none) user.warn kernel: CPU: ARM926EJ-Sid(wb) [41069260] revision 0 (ARMv5TEJ)
Jan  1 00:00:24 (none) user.warn kernel: CPU0: D VIVT write-back cache
Jan  1 00:00:24 (none) user.warn kernel: CPU0: I cache: 16384 bytes, associativity 1, 32 byte lines, 512 sets
Jan  1 00:00:24 (none) user.warn kernel: CPU0: D cache: 16384 bytes, associativity 1, 32 byte lines, 512 sets
Jan  1 00:00:24 (none) user.warn kernel: Machine: Feroceon
Jan  1 00:00:24 (none) user.warn kernel: Using UBoot passing parameters structure
Jan  1 00:00:24 (none) user.warn kernel: Memory policy: ECC disabled, Data cache writeback
Jan  1 00:00:24 (none) user.debug kernel: On node 0 totalpages: 4096
Jan  1 00:00:24 (none) user.debug kernel:   DMA zone: 4096 pages, LIFO batch:1
Jan  1 00:00:24 (none) user.debug kernel:   Normal zone: 0 pages, LIFO batch:1
Jan  1 00:00:24 (none) user.debug kernel:   HighMem zone: 0 pages, LIFO batch:1
Jan  1 00:00:24 (none) user.warn kernel: Built 1 zonelists
Jan  1 00:00:24 (none) user.notice kernel: Kernel command line: console=ttyS0,115200 root=/dev/sda7 ro boardType=mv88F6082 productType=Aston reset=0
Jan  1 00:00:24 (none) user.warn kernel: mvBoardGpioIntMaskGet:Board intsGppMask 0
Jan  1 00:00:24 (none) user.warn kernel: PID hash table entries: 128 (order: 7, 2048 bytes)
Jan  1 00:00:24 (none) user.warn kernel: Console: colour dummy device 80x30
Jan  1 00:00:24 (none) user.warn kernel: Dentry cache hash table entries: 4096 (order: 2, 16384 bytes)
Jan  1 00:00:24 (none) user.warn kernel: Inode-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jan  1 00:00:24 (none) user.info kernel: Memory: 8MB 8MB 0MB 0MB = 16MB total
Jan  1 00:00:24 (none) user.notice kernel: Memory: 13408KB available (2278K code, 385K data, 84K init)
Jan  1 00:00:24 (none) user.debug kernel: Calibrating delay loop... 219.54 BogoMIPS (lpj=1097728)
Jan  1 00:00:24 (none) user.warn kernel: Mount-cache hash table entries: 512
Jan  1 00:00:24 (none) user.info kernel: CPU: Testing write buffer coherency: ok
Jan  1 00:00:24 (none) user.info kernel: NET: Registered protocol family 16
Jan  1 00:00:24 (none) user.warn kernel: mvBoardMppGet mppGroupNum 0 mppGroup 4096
Jan  1 00:00:24 (none) user.warn kernel: mvBoardMppGet mppGroupNum 1 mppGroup 17
Jan  1 00:00:24 (none) user.warn kernel: Sys Clk = 166666667, Tclk = 133333333
Jan  1 00:00:24 (none) user.warn kernel: 
Jan  1 00:00:24 (none) user.warn kernel: CPU Interface
Jan  1 00:00:24 (none) user.warn kernel: -------------
Jan  1 00:00:24 (none) user.warn kernel: SDRAM_CS0 ....base 00000000, size   8MB 
Jan  1 00:00:24 (none) user.warn kernel: SDRAM_CS1 ....base 00800000, size   8MB 
Jan  1 00:00:24 (none) user.warn kernel: PEX0_MEM ....base e0000000, size 128MB 
Jan  1 00:00:24 (none) user.warn kernel: PEX0_IO ....base f2000000, size   1MB 
Jan  1 00:00:24 (none) user.warn kernel: INTER_REGS ....base f1000000, size   1MB 
Jan  1 00:00:24 (none) user.warn kernel: NFLASH_CS ....base f9000000, size   2MB 
Jan  1 00:00:24 (none) user.warn kernel: MFLASH_CS ....base f8000000, size 256KB 
Jan  1 00:00:24 (none) user.warn kernel: SPI_CS ....base fa000000, size   8MB 
Jan  1 00:00:24 (none) user.warn kernel: BOOT_ROM_CS ....base fc000000, size   1MB 
Jan  1 00:00:24 (none) user.warn kernel: DEV_BOOTCS ....base fc000000, size   1MB 
Jan  1 00:00:24 (none) user.warn kernel: CRYPT_ENG ....base f0000000, size  64KB 
Jan  1 00:00:24 (none) user.warn kernel: 
Jan  1 00:00:24 (none) user.warn kernel:   Marvell Development Board (LSP Version 2.2.2_NAS_GDP)-- RD-88F6082-NAS-PH  Soc: MV88F6082 Rev 1
Jan  1 00:00:24 (none) user.warn kernel: 
Jan  1 00:00:24 (none) user.warn kernel:  Detected Tclk 133333333 and SysClk 166666667 
Jan  1 00:00:24 (none) user.warn kernel: Marvell USB EHCI Host controller #0: c031eb00
Jan  1 00:00:24 (none) user.info kernel: PCI: bus0: Fast back to back transfers enabled
Jan  1 00:00:24 (none) user.notice kernel: SCSI subsystem initialized
Jan  1 00:00:24 (none) user.info kernel: usbcore: registered new driver usbfs
Jan  1 00:00:24 (none) user.info kernel: usbcore: registered new driver hub
Jan  1 00:00:24 (none) user.warn kernel: Fast Floating Point Emulator V0.9 (c) Peter Teichmann.
Jan  1 00:00:24 (none) user.info kernel: inotify device minor=63
Jan  1 00:00:24 (none) user.warn kernel: Registering unionfs 1.1.5
Jan  1 00:00:24 (none) user.info kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing disabled
Jan  1 00:00:24 (none) user.warn kernel: ttyS0 at MMIO 0x0 (irq = 3) is a 16550A
Jan  1 00:00:24 (none) user.info kernel: io scheduler noop registered
Jan  1 00:00:24 (none) user.warn kernel: Marvell Ethernet Driver 'mv_ethernet':
Jan  1 00:00:24 (none) user.warn kernel:   o Uncached descriptors in DRAM
Jan  1 00:00:24 (none) user.warn kernel:   o DRAM SW cache-coherency
Jan  1 00:00:24 (none) user.warn kernel:   o TCP segmentation offload enabled
Jan  1 00:00:24 (none) user.warn kernel:   o Checksum offload enabled
Jan  1 00:00:24 (none) user.warn kernel:   o Rx desc: 64
Jan  1 00:00:24 (none) user.warn kernel:   o Tx desc: 128
Jan  1 00:00:24 (none) user.warn kernel:   o Loading network interface 'egiga0' 'egiga1' 
Jan  1 00:00:24 (none) user.info kernel: ipddp.c:v0.01 8/28/97 Bradford W. Johnson <johns393@maroon.tc.umn.edu>
Jan  1 00:00:24 (none) user.warn kernel: ipddp0: Appletalk-IP Encap. mode by Bradford W. Johnson <johns393@maroon.tc.umn.edu>
Jan  1 00:00:24 (none) user.warn kernel: Intergrated Sata device found
Jan  1 00:00:24 (none) user.info kernel: scsi0 : Marvell SCSI to SATA adapter
Jan  1 00:00:24 (none) user.notice kernel:   Vendor: SAMSUNG   Model: HD103UJ           Rev: 1AA0
Jan  1 00:00:24 (none) user.notice kernel:   Type:   Direct-Access                      ANSI SCSI revision: 03
Jan  1 00:00:24 (none) user.notice kernel: SCSI device sda: 1953525168 512-byte hdwr sectors (1000205 MB)
Jan  1 00:00:24 (none) user.notice kernel: SCSI device sda: drive cache: write back
Jan  1 00:00:24 (none) user.notice kernel: SCSI device sda: 1953525168 512-byte hdwr sectors (1000205 MB)
Jan  1 00:00:24 (none) user.notice kernel: SCSI device sda: drive cache: write back
Jan  1 00:00:24 (none) user.info kernel:  sda: sda1 < sda5 sda6 sda7 sda8 sda9 sda10 > sda2
Jan  1 00:00:24 (none) user.notice kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
Jan  1 00:00:24 (none) user.notice kernel: Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
Jan  1 00:00:24 (none) user.info kernel: ehci_platform ehci_platform.70059: EHCI Host Controller
Jan  1 00:00:24 (none) user.info kernel: ehci_platform ehci_platform.70059: new USB bus registered, assigned bus number 1
Jan  1 00:00:24 (none) user.info kernel: ehci_platform ehci_platform.70059: irq 17, io mem 0x00000000
Jan  1 00:00:24 (none) user.info kernel: ehci_platform ehci_platform.70059: park 0
Jan  1 00:00:24 (none) user.info kernel: ehci_platform ehci_platform.70059: USB 0.0 initialized, EHCI 1.00, driver 10 Dec 2004
Jan  1 00:00:24 (none) user.info kernel: hub 1-0:1.0: USB hub found
Jan  1 00:00:24 (none) user.info kernel: hub 1-0:1.0: 1 port detected
Jan  1 00:00:24 (none) user.debug kernel: ntroller (OHCI) Driver (PCI)
Jan  1 00:00:24 (none) user.info kernel: USB Universal Host Controller Interface driver v2.2
Jan  1 00:00:24 (none) user.info kernel: Initializing USB Mass Storage driver...
Jan  1 00:00:24 (none) user.info kernel: usbcore: registered new driver usb-storage
Jan  1 00:00:24 (none) user.info kernel: USB Mass Storage support registered.
Jan  1 00:00:24 (none) user.info kernel: usbcore: registered new driver usbhid
Jan  1 00:00:24 (none) user.info kernel: drivers/usb/input/hid-core.c: v2.01:USB HID core driver
Jan  1 00:00:24 (none) user.info kernel: mice: PS/2 mouse device common for all mice
Jan  1 00:00:24 (none) user.warn kernel: DATA IN REG=28E1
Jan  1 00:00:24 (none) user.info kernel: aston_power 1.0 initialised
Jan  1 00:00:24 (none) user.info kernel: i2c /dev entries driver
Jan  1 00:00:24 (none) user.info kernel: rs5c372 0-0032: Oscillator halt detected, reseting clock to 01/01/2000
Jan  1 00:00:24 (none) user.info kernel: NET: Registered protocol family 2
Jan  1 00:00:24 (none) user.info kernel: IP: routing cache hash table of 512 buckets, 4Kbytes
Jan  1 00:00:24 (none) user.warn kernel: TCP established hash table entries: 1024 (order: 1, 8192 bytes)
Jan  1 00:00:24 (none) user.warn kernel: TCP bind hash table entries: 1024 (order: 0, 4096 bytes)
Jan  1 00:00:24 (none) user.info kernel: TCP: Hash tables configured (established 1024 bind 1024)
Jan  1 00:00:24 (none) user.info kernel: NET: Registered protocol family 1
Jan  1 00:00:24 (none) user.info kernel: NET: Registered protocol family 17
Jan  1 00:00:24 (none) user.info kernel: NET: Registered protocol family 5
Jan  1 00:00:24 (none) user.info kernel: Loading I2C based RTC driver device interface.
Jan  1 00:00:24 (none) user.info kernel: Found TWSI adapter with id: 0
Jan  1 00:00:24 (none) user.info kernel: Found I2C RTC rs5c372 @ 0x32
Jan  1 00:00:24 (none) user.info kernel: kjournald starting.  Commit interval 5 seconds
Jan  1 00:00:24 (none) user.info kernel: EXT3-fs: mounted filesystem with ordered data mode.
Jan  1 00:00:24 (none) user.warn kernel: VFS: Mounted root (ext3 filesystem) readonly.
Jan  1 00:00:24 (none) user.info kernel: Freeing init memory: 84K
Jan  1 00:00:24 (none) user.info kernel: kjournald starting.  Commit interval 5 seconds
Jan  1 00:00:24 (none) user.info kernel: EXT3-fs: mounted filesystem with ordered data mode.
Jan  1 00:00:24 (none) user.info kernel: kjournald starting.  Commit interval 5 seconds
Jan  1 00:00:24 (none) user.info kernel: EXT3 FS on sda9, internal journal
Jan  1 00:00:24 (none) user.info kernel: EXT3-fs: mounted filesystem with ordered data mode.
Jan  1 00:00:24 (none) user.info kernel: kjournald starting.  Commit interval 5 seconds
Jan  1 00:00:24 (none) user.info kernel: EXT3-fs: mounted filesystem with ordered data mode.
Jan  1 00:00:24 (none) user.info kernel: SGI XFS with large block numbers, no debug enabled
Jan  1 00:00:24 (none) user.info kernel: usb 1-1: new high speed USB device using ehci_platform and address 2
Jan  1 00:00:24 (none) user.info kernel: scsi1 : SCSI emulation for USB Mass Storage devices
Jan  1 00:00:24 (none) user.debug kernel: usb-storage: device found at 2
Jan  1 00:00:24 (none) user.debug kernel: usb-storage: waiting for device to settle before scanning
Jan  1 00:00:24 (none) user.info kernel: input: USB HID v1.11 Device [OEM Mass Storage Plus] on usb-ehci_platform.70059-1
Jan  1 00:00:24 (none) user.err kernel: VFS: Can't find ext3 filesystem on dev sda2.
Jan  1 00:00:24 (none) user.err kernel: FAT: bogus number of FAT structure
Jan  1 00:00:24 (none) user.info kernel: VFS: Can't find a valid FAT filesystem on dev sda2.
Jan  1 00:00:24 (none) user.err kernel: FAT: bogus number of FAT structure
Jan  1 00:00:24 (none) user.info kernel: VFS: Can't find a valid FAT filesystem on dev sda2.
Jan  1 00:00:24 (none) user.warn kernel: HFS+-fs: unable to find HFS+ superblock
Jan  1 00:00:24 (none) user.notice kernel: XFS mounting filesystem sda2
Jan  1 00:00:24 (none) user.debug kernel: Ending clean XFS mount for filesystem: sda2
Jan  1 00:00:24 (none) user.notice kernel:   Vendor: Ext Hard  Model:  Disk             Rev:     
Jan  1 00:00:24 (none) user.notice kernel:   Type:   Direct-Access                      ANSI SCSI revision: 04
Jan  1 00:00:24 (none) user.notice kernel: SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
Jan  1 00:00:24 (none) user.err kernel: sdb: assuming drive cache: write through
Jan  1 00:00:24 (none) user.notice kernel: SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
Jan  1 00:00:24 (none) user.err kernel: sdb: assuming drive cache: write through
Jan  1 00:00:24 (none) user.info kernel:  sdb: sdb1
Jan  1 00:00:24 (none) user.notice kernel: Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
Jan  1 00:00:24 (none) user.notice kernel: Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 0
Jan  1 00:00:24 (none) user.debug kernel: usb-storage: device scan complete
Jan  1 00:00:24 (none) user.info kernel: kjournald starting.  Commit interval 5 seconds
Jan  1 00:00:24 (none) user.info kernel: EXT3-fs: mounted filesystem with ordered data mode.
Jan  1 00:00:24 (none) user.info kernel: kjournald starting.  Commit interval 5 seconds
Jan  1 00:00:24 (none) user.info kernel: EXT3 FS on sda9, internal journal
Jan  1 00:00:24 (none) user.info kernel: EXT3-fs: mounted filesystem with ordered data mode.
Jan  1 00:00:25 (none) user.info kernel: SGI XFS with large block numbers, no debug enabled
Jan  1 00:00:25 (none) user.warn kernel: fuse init (API version 7.8)
Jan  1 00:00:25 (none) user.warn kernel: fuse distribution version: 2.7.3
Jan  1 00:00:26 (none) user.info kernel: Adding 128448k swap on /dev/sda5.  Priority:-1 extents:1
Jan  1 00:00:27 (none) user.notice kernel: XFS mounting filesystem sda2
Jan  1 00:00:27 (none) user.debug kernel: Ending clean XFS mount for filesystem: sda2
Jan  1 00:00:30 (none) local0.info udhcpc[598]: udhcpc (v0.9.9-pre) started
Jan  1 00:00:30 (none) user.notice kernel: egiga0: link down
Jan  1 00:00:32 (none) user.notice kernel: egiga0: link up, full duplex, speed 100 Mbps
Jan  1 00:00:34 (none) local0.info udhcpc[598]: Lease of 192.168.1.9 obtained, lease time 172800
Jan  1 00:00:42 (none) daemon.info ifplugd(egiga0)[770]: ifplugd 0.28 initializing.
Jan  1 00:00:42 (none) daemon.info ifplugd(egiga0)[770]: Using interface egiga0/00:D0:4B:86:23:B0 with driver <egiga> (version: )
Jan  1 00:00:42 (none) daemon.info ifplugd(egiga0)[770]: Using detection mode: SIOCETHTOOL
Jan  1 00:00:42 (none) daemon.info ifplugd(egiga0)[770]: Initialization complete, link beat detected.
Jan  1 00:00:42 (none) daemon.info ifplugd(egiga0)[770]: Executing '/etc/ifplugd/ifplugd.action egiga0 up'.
Jan  1 00:00:42 (none) daemon.warn ifplugd(egiga0)[770]: client: route: SIOC[ADD|DEL]RT: No such process
Jan  1 00:00:43 (none) daemon.info ifplugd(egiga0)[770]: Program executed successfully.
Jan  1 00:00:44 (none) user.info ipconfd[817]: daemon started 
Jan  1 00:00:46 (none) authpriv.debug httpd: pam_unix(httpd:account): account admin has password changed in future
Jan  1 00:00:46 (none) authpriv.info httpd: pam_unix(httpd:session): session opened for user admin by (uid=0)
Jan  1 00:00:46 (none) authpriv.info httpd: pam_unix(httpd:session): session closed for user admin
Jan  1 00:00:49 (none) authpriv.debug httpd: pam_unix(httpd:account): account admin has password changed in future
Jan  1 00:00:49 (none) authpriv.info httpd: pam_unix(httpd:session): session opened for user admin by (uid=0)
Jan  1 00:00:49 (none) authpriv.info httpd: pam_unix(httpd:session): session closed for user admin
Oct 16 07:35:33 (none) user.info usbmount[1088]: executing command: mount -tvfat -osync,noexec,nodev,noatime /dev/sdb1 /home/usbdisksdb1
Oct 16 07:35:34 (none) user.info usbmount[1088]: executing command: run-parts /etc/usbmount/mount.d
Oct 16 07:35:41 (none) authpriv.info httpd: pam_unix(httpd:session): session opened for user admin by (uid=0)
Oct 16 07:35:41 (none) authpriv.info httpd: pam_unix(httpd:session): session closed for user admin
Oct 16 07:35:43 (none) user.info kernel: Halt requested from user space
Oct 16 07:35:43 (none) user.info kernel: Found TWSI adapter with id: 1
Oct 16 07:35:43 (none) user.err kernel: Failed to set power OFF
Oct 16 07:35:43 (none) daemon.info init: Starting pid 1347, console /dev/ttyS0: '/shutdown'
Oct 16 07:35:51 (none) user.notice kernel: egiga0: link down
Oct 16 07:35:51 (none) daemon.info ifplugd(egiga0)[770]: Link beat lost.
Oct 16 07:35:52 (none) daemon.info atalkd[1527]: restart (2.0.3)
Oct 16 07:35:52 (none) daemon.info ifplugd(egiga0)[770]: Executing '/etc/ifplugd/ifplugd.action egiga0 down'.
Oct 16 07:35:53 (none) user.info kernel: usb 1-1: USB disconnect, address 2
Oct 16 07:35:56 (none) daemon.warn ifplugd(egiga0)[770]: client: route: SIOC[ADD|DEL]RT: No such process
Oct 16 07:35:57 (none) local0.info udhcpc[741]: Performing a DHCP renew
Oct 16 07:35:57 (none) user.info usbmount[1566]: executing command: umount -l /home/usbdisksdb1
Oct 16 07:35:58 (none) daemon.info ifplugd(egiga0)[770]: Program executed successfully.
Oct 16 07:36:00 (none) lpr.info papd[1718]: restart (2.0.3)
Oct 16 07:36:00 (none) user.info usbmount[1695]: processing delshare list
Oct 16 07:36:04 (none) daemon.info afpd[1780]: Registering CNID module [last]
Oct 16 07:36:04 (none) daemon.info afpd[1780]: Registering CNID module [cdb]
Oct 16 07:36:04 (none) daemon.info afpd[1780]: Registering CNID module [dbd]
Oct 16 07:36:04 (none) daemon.debug afpd[1780]: Loading ConfigFile
Oct 16 07:36:04 (none) daemon.err afpd[1780]: main: atp_open: Cannot assign requested address
Oct 16 07:36:04 (none) daemon.info afpd[1780]: ASIP started on 192.168.1.9:548(5) (2.0.3)
Oct 16 07:36:04 (none) daemon.debug afpd[1780]: uam: loading (/etc/netatalk/uams/uams_clrtxt.so)
```

---

### Post by PartisanEntity on 2008-11-26
Glad I found this thread, I am planning to buy the Lacie Network Space 1TB and was wondering if it run nicely with Ubuntu.

Any tips on getting started from your experiences?

Also, how do the speeds far when accessing it through wifi?

---

### Post by PartisanEntity on 2008-11-27
How did you guys connect from Ubuntu to your lacie drives?

For some reason, if I choose FTP (with logon) the folders appear empty even though I have files in them.

---

### Post by stormtrooprdave on 2008-11-27
> **PartisanEntity said:**
> Glad I found this thread, I am planning to buy the Lacie Network Space 1TB and was wondering if it run nicely with Ubuntu.

Any tips on getting started from your experiences?

Also, how do the speeds far when accessing it through wifi?

With a bit of trial and error and piecing things together from threads here I got it working to my satisfaction.

Create a folder in /media then add this line to fstab:

//192.168.1.64/openshare/ media/NetworkSpace cifs 0 0

Change the address to whatever it is, and whatever you called the folder in /media.  It now automounts on to my desktop after my wireless connection has logged on.  I originally had my music and videos on another partition of the same hdd so going through a network was initially slower slightly but now it seems the same as it used to be.

---

### Post by PartisanEntity on 2008-11-27
> **stormtrooprdave said:**
> With a bit of trial and error and piecing things together from threads here I got it working to my satisfaction.

Create a folder in /media then add this line to fstab:

//192.168.1.64/openshare/ media/NetworkSpace cifs 0 0

Change the address to whatever it is, and whatever you called the folder in /media.  It now automounts on to my desktop after my wireless connection has logged on.  I originally had my music and videos on another partition of the same hdd so going through a network was initially slower slightly but now it seems the same as it used to be.

Actually, since posting here I got it to work, I downloaded the Linux version of the LaCie Agent, made sure smbfs was also installed, and then simply went to Places > Connect to Server and it worked.

---

### Post by Daan on 2008-11-30
> **PartisanEntity said:**
> Actually, since posting here I got it to work, I downloaded the Linux version of the LaCie Agent, made sure smbfs was also installed, and then simply went to Places > Connect to Server and it worked.

So Lacie got its Network Assistant for Linux finished in the few days since I last checked. It can be used to set the IP address of the Networkspace, or choose for Automatic through DHCP, which is the default. Since my router has DHCP, I do not need the Network Assistant.

Installing the Assistant on my Debian Lenny went easy by just doing "sh LaCie\ Network\ Assistant\ 1.1.package" in a terminal. Then "LaCie_Network_Assistant" and a little clickable icon appeared in the notification area of the Gnome.

It would be cool if some Linux geeks found a way to make the firmware better, so that we can have more user accounts with different permissions and direct hook up as a usb mass storage device to a PC.

---

### Post by TheMadGeneral on 2010-01-18
I have just installed this on Ubuntu 9.10 - the Karmic Koala.

I Inserted the disk that came with the drive and navigated to the Linux folder on the CD.  Double clicked on the lna-linux-1.1.rar Folder and copied the LaCie Network Assistant 1.1 by dragging it to my desktop.  I then double clicked on the Readme.txt file in the /media/CD_Utilities    /Linux/lna-linux-1.1.rar Folder and read the following.

========================
Please read these instructions about LaCie Network Assistant 1.1 for linux.

The software was tested on ubuntu 8.04, mandriva, and Suze, 32bits version.

--Installation--

To install LaCie Network Assistant, just double click on the .package file. ***[COLOR="DarkRed"]I HAD TO DO THIS NEXT STEP[/COLOR]*** You might need to check the file has execution permissions. If not, right click on the file, choose "properties", in the "permissions" settings check "allow executing file as program". 

Upon opening the .package, if the autopackage tools are not installed in your system, the installer will automatically offer you to install it.

--Configuration--

1/ If you have a 64bits system, you will need the Avahi libraries for 32bits.

2/ Mandriva and suze automatically close ports for Avahi. The application can be launched but it does not list devices on your network. In this case you should open the right port for avahi (UDP 5353). We do not advise you to deactivate your firewall.

3/ If you cannot mount volumes, make sure you have "smbfs" installed.

[www.lacie.com](www.lacie.com)

==============================

Then I clicked on Applications|Accessories|LaCie Network Assistant on the menu bar at the top left of your desktop.

I feel really proud of myself as I am a novice and am still finding my way around Ubuntu.  My goal is to have all my hardware and software applications (or their alternatives) replicated on the Ubuntu platform.  Last night it was my Epson Perfection 4490 Photo scanner, tonight the NAS, and tomorrow night, ah yes Spanish lessons. lol.

Thanks to all who add their information to the Ubuntu forums.  You don't realize how helpful it is.:popcorn:

---

### Post by wormhole_ on 2010-10-03
Sorry my english is very bad.

- I add in fstab this two line :
  //192.168.1.11/OpenShare/ media/LaCie_1T cifs 0 0
  //192.168.1.11/MyShare/ media/LaCie_1T cifs 0 0

- I add the directory /media/LaCie_1T
But it dosen' t  work

Can you explain me were is my mistake ?

Thanks

---

### Post by TheMadGeneral on 2010-12-27
Go to [http://www.lacie.com/uk/support/drivers/driver.htm?id=10138](http://www.lacie.com/uk/support/drivers/driver.htm?id=10138) to get the latest UBUNTU LaCie Network Assistant

Still works with Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010 and supported until April 2013.

---

### Post by thefabfour on 2011-01-02
Hello,

I just finished the installation of the LaCie Network assistant. All look fine, but, when I going to click on the blue Lacie logo on the tool bar, to have access to my two Drive "Open Share " and "My Share", I cannot see them as in Win7 or Mac OSX. To have access to thr both Folders, I have to go to the Ubuntu Control tool bar/Shortcut/Network and the I see twice 2 Network links "NetworkSpace2" and "NETWORKSPACE2". 

Any idea to have a better and simple access to my folders ?

Thanks

config : Ubuntu 10.04 Lucid Lynx

---

### Post by PartisanEntity on 2011-01-02
Hi, I gave up on the LaCie NetworkSpace a year ago. The firmware and control panel are/were painfully primitive and limiting.

I took the HDD out of the enclosure and turned it into a USB hdd. I attached it to my spare Ubuntu laptop, and am now using it as a networked drive and have set up my own DLNA server, as well as TimeMachine backup device, I can also connect to my shared content using AFP from the Macs.

---

### Post by dai_bach on 2011-01-19
I know that the thread is closed but I thought I'd throw in my tuppence's worth as some folk have been doing the same as me but seeming to have some trouble...

I wanted to mount the OpenShare partition so I installed smbfs (it's use is apparently depreciated so someone might want to correct me here), then added the following line to /etc/fstab
```
//192.168.local.ip/OpenShare/	/mount/point	cifs	users,auto,credentials=/path/to/credentials/file,noexec,noperm	0	0
```

and created a credentials file in the location given by /path/to/credentials/file containing the lines
```
user = USERNAME
password = PASSWORD
```

with read only permissions (400) by the owner (me) as well as ownership of the file
```
chmod 400 /path/to/credentials/file
chown USERNAME.USERNAME /path/to/credentials/file
```

and voilà, the partion automounted on the next restart!

Basically, I did the same as is detailed in [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) except for the part about ownership of the credentials file.  I tried root.root ownership but this meant that the partition could only be mounted by root and henceforth had root ownership (i.e. all file operations had to be preceeded by "sudo").

Hope this helps someone!

---

### Post by dai_bach on 2011-01-19
I know that the thread is closed but I thought I'd throw in my tuppence's worth as some folk have been doing the same as me but seeming to have some trouble...

I wanted to mount the OpenShare partition so I installed smbfs (it's use is apparently depreciated so someone might want to correct me here), then added the following line to /etc/fstab
```
//192.168.local.ip/OpenShare/	/mount/point	cifs	users,auto,credentials=/path/to/credentials/file,noexec,noperm	0	0
```

and created a credentials file in the location given by /path/to/credentials/file containing the lines
```
user = USERNAME
password = PASSWORD
```

with read only permissions (400) by the owner (me) as well as ownership of the file
```
chmod 400 /path/to/credentials/file
chown USERNAME.USERNAME /path/to/credentials/file
```

and voilà, the partion automounted on the next restart!

Basically, I did the same as is detailed in [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) except for the part about ownership of the credentials file.  I tried root.root ownership but this meant that the partition could only be mounted by root and henceforth had root ownership (i.e. all file operations had to be preceeded by "sudo").

Hope this helps someone!

---

### Post by dai_bach on 2011-01-19
I know that the thread is closed but I thought I'd throw in my tuppence's worth as some folk have been doing the same as me but seeming to have some trouble...

I wanted to mount the OpenShare partition so I installed smbfs (it's use is apparently depreciated so someone might want to correct me here), then added the following line to /etc/fstab
```
//192.168.local.ip/OpenShare/	/mount/point	cifs	users,auto,credentials=/path/to/credentials/file,noexec,noperm	0	0
```

and created a credentials file in the location given by /path/to/credentials/file containing the lines
```
user = USERNAME
password = PASSWORD
```

with read only permissions (400) by the owner (me) as well as ownership of the file
```
chmod 400 /path/to/credentials/file
chown USERNAME.USERNAME /path/to/credentials/file
```

and voilà, the partion automounted on the next restart!

Basically, I did the same as is detailed in [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) except for the part about ownership of the credentials file.  I tried root.root ownership but this meant that the partition could only be mounted by root and henceforth had root ownership (i.e. all file operations had to be preceeded by "sudo").

Hope this helps someone!

---

### Post by dai_bach on 2011-01-19
I know that the thread is closed but I thought I'd throw in my tuppence's worth as some folk have been doing the same as me but seeming to have some trouble...

I wanted to mount the OpenShare partition so I installed smbfs (it's use is apparently depreciated so someone might want to correct me here), then added the following line to /etc/fstab
```
//192.168.local.ip/OpenShare/	/mount/point	cifs	users,auto,credentials=/path/to/credentials/file,noexec,noperm	0	0
```

and created a credentials file in the location given by /path/to/credentials/file containing the lines
```
user = USERNAME
password = PASSWORD
```

with read only permissions (400) by the owner (me) as well as ownership of the file
```
chmod 400 /path/to/credentials/file
chown USERNAME.USERNAME /path/to/credentials/file
```

and voilà, the partion automounted on the next restart!

Basically, I did the same as is detailed in [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) except for the part about ownership of the credentials file.  I tried root.root ownership but this meant that the partition could only be mounted by root and henceforth had root ownership (i.e. all file operations had to be preceeded by "sudo").

Hope this helps someone!

---

### Post by dai_bach on 2011-01-19
I know that the thread is closed but I thought I'd throw in my tuppence's worth 
as some folk have been doing the same as me but seeming to have some trouble...

I wanted to mount the OpenShare partition so I installed smbfs (it's use is appa
rently depreciated so someone might want to correct me here), then added the fol
lowing line to /etc/fstab
```
//192.168.local.ip/OpenShare/	/mount/point	cifs	users,auto,crede
ntials=/path/to/credentials/file,noexec,noperm	0	0
```

and created a credentials file in the location given by /path/to/credentials/fil
e containing the lines
```
user = USERNAME
password = PASSWORD
```

with read only permissions (400) by the owner (me) as well as ownership of the f
ile
```
chmod 400 /path/to/credentials/file
chown USERNAME.USERNAME /path/to/credentials/file
```

and voilà, the partion automounted on the next restart!

Basically, I did the same as is detailed in [url]http://ubuntuforums.org/showthr
ead.php?t=283131[/url] except for the part about ownership of the credentials fi
le.  I tried root.root ownership but this meant that the partition could only be
 mounted by root and henceforth had root ownership (i.e. all file operations had
 to be preceeded by "sudo").

Hope this helps someone!

---

### Post by dai_bach on 2011-01-20
I know that the thread is closed but I thought I'd throw in my tuppence's worth as some folk have been doing the same as me but seeming to have some trouble...

I wanted to mount the OpenShare partition so I installed smbfs (it's use is apparently depreciated so someone might want to correct me here), then added the following line to /etc/fstab
```
//192.168.local.ip/OpenShare/	/mount/point	cifs	users,auto,credentials=/path/to/credentials/file,noexec,noperm	0	0
```

and created a credentials file in the location given by /path/to/credentials/file containing the lines
```
user = USERNAME
password = PASSWORD
```

with read only permissions (400) by the owner (me) as well as ownership of the file
```
chmod 400 /path/to/credentials/file
chown USERNAME.USERNAME /path/to/credentials/file
```

and voilà, the partion automounted on the next restart!

Basically, I did the same as is detailed in [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) except for the part about ownership of the credentials file.  I tried root.root ownership but this meant that the partition could only be mounted by root and henceforth had root ownership (i.e. all file operations had to be preceeded by "sudo").

Hope this helps someone!

---

### Post by carrabta on 2011-01-30
Hi all !
I've just bought a LaCie Network Space 2 NAS, 2To and am using ubuntu "up-to-date" version. 
Just to confirm that it is fully compatible with my system. LaCie have developped their Network Assistant for linux and managed to have it operational on 64bits system like mine.
=> So this product is a good choice for linux users !

Tanguy

---

### Post by mosamasa on 2011-02-23
> **carrabta said:**
> Hi all !
I've just bought a LaCie Network Space 2 NAS, 2To and am using ubuntu "up-to-date" version. 
Just to confirm that it is fully compatible with my system. LaCie have developped their Network Assistant for linux and managed to have it operational on 64bits system like mine.
=> So this product is a good choice for linux users !

Tanguy

How to install LaCie Network Assistant on AMD64? It seems that I would need Avahi libraries for 32bits. How to get it?

---

### Post by piade87 on 2012-07-20
> **mosamasa said:**
> How to install LaCie Network Assistant on AMD64? It seems that I would need Avahi libraries for 32bits. How to get it?

Hi! Have you solved this problem? I use Ubuntu 12.04 64 bit and I can't install the Network Assistant

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

