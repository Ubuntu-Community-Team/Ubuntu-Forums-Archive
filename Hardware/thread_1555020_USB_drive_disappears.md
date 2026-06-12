---
title: "USB drive disappears"
date: 2010-08-17
forum: Hardware
---

### Post by Bakmeel on 2010-08-17
Hello,

I am running Ubuntu Server 10.04 64bit with 2.6.34-020634-generic kernel. Attached to the system is a USB drive (A Samsung S1 Mini 120GB). The USB drive is permanently attached to cache my running torrents. It also holds the system log files.

Fstab looks like this:
```
# <file system>                           <mount point>   <type>  <options>                 <dump>  <pass>
proc                                      /proc           proc    nodev,noexec,nosuid       0       0
UUID=4b342ec3-7a2d-4555-b6fb-1d928893be55 /               ext2    noatime,errors=remount-ro 0       1
tmpfs                                     /tmp            tmpfs   noexec,defaults,noatime   0       0
tmpfs                                     /var/tmp        tmpfs   noexec,defaults,noatime   0       0

# Disks on the Samsung S1 USB Drive
# <file system>                           <mount point>   <type>  <options>                 <dump>  <pass>
UUID=a356b81c-eab7-436c-940f-557df73d5561 /var/log        ext4    noexec,defaults           0       0
UUID=88c2f485-71c9-4b7d-b595-87777b7d60ea /mnt/active     ext4    defaults                  0       0
```When I am not running any torrents, the system works fine.
When the torrents are running for several hours, up to a day or so, the USB drive disappears and doesn't come back online. All torrents are killed obviously and the log files are inaccessible except for the part that is cached in the memory. The system itself keeps running however (fortunately).

When I try to re-mount the drive, I get:
```
me@system:~$ sudo mount -all
[sudo] password for me: 
mount: special device UUID=a356b81c-eab7-436c-940f-557df73d5561 does not exist
mount: special device UUID=88c2f485-71c9-4b7d-b595-87777b7d60ea does not exist
```blkid only returns the system drive mounted in /
```
me@system:~$ blkid
/dev/sda1: LABEL="SYSTEM" UUID="4b342ec3-7a2d-4555-b6fb-1d928893be55" TYPE="ext2" 
```Fortunately the dmesg log is cached in the memory, so I could at least grab some logfile... It clearly indicates something went wrong but I can't decipher what... sdb1 and sdb2 should be the partitions on the USB drive.

```
[   27.289535] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[   27.415827] EXT4-fs (sdb2): mounted filesystem with ordered data mode
[   29.242501] ppdev: user-space parallel port driver
[13743.070049] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[13758.190063] usb 1-2: device descriptor read/64, error -110
[13773.420035] usb 1-2: device descriptor read/64, error -110
[13773.650039] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[13788.770037] usb 1-2: device descriptor read/64, error -110
[13804.000035] usb 1-2: device descriptor read/64, error -110
[13804.230065] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[13814.650034] usb 1-2: device not accepting address 2, error -110
[13814.770055] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[13825.190066] usb 1-2: device not accepting address 2, error -110
[13825.190164] usb 1-2: USB disconnect, address 2
[13825.190201] sd 4:0:0:0: Device offlined - not ready after error recovery
[13825.190229] sd 4:0:0:0: [sdb] Unhandled error code
[13825.190236] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[13825.190248] sd 4:0:0:0: [sdb] CDB: Write(10): 2a 00 00 67 b2 00 00 00 1e 00
[13825.190277] end_request: I/O error, dev sdb, sector 54366208
[13825.190307] Buffer I/O error on device sdb2, logical block 6533376
[13825.190331] lost page write due to I/O error on sdb2
[13825.190349] Buffer I/O error on device sdb2, logical block 6533377
[13825.190371] lost page write due to I/O error on sdb2
[13825.190383] Buffer I/O error on device sdb2, logical block 6533378
[13825.190406] lost page write due to I/O error on sdb2
[13825.190418] Buffer I/O error on device sdb2, logical block 6533379
[13825.190441] lost page write due to I/O error on sdb2
[13825.190453] Buffer I/O error on device sdb2, logical block 6533380
[13825.190477] lost page write due to I/O error on sdb2
[13825.190490] Buffer I/O error on device sdb2, logical block 6533381
[13825.190513] lost page write due to I/O error on sdb2
[13825.190525] Buffer I/O error on device sdb2, logical block 6533382
[13825.190548] lost page write due to I/O error on sdb2
[13825.190561] Buffer I/O error on device sdb2, logical block 6533383
[13825.190583] lost page write due to I/O error on sdb2
[13825.190596] Buffer I/O error on device sdb2, logical block 6533384
[13825.190619] lost page write due to I/O error on sdb2
[13825.190631] Buffer I/O error on device sdb2, logical block 6533385
[13825.190654] lost page write due to I/O error on sdb2
[13825.191642] sd 4:0:0:0: [sdb] Unhandled error code
[13825.191655] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[13825.191666] sd 4:0:0:0: [sdb] CDB: Write(10): 2a 00 00 67 b2 1e 00 00 1e 00
[13825.191695] end_request: I/O error, dev sdb, sector 54366448
[13825.192957] JBD2: Detected IO errors while flushing file data on sdb1-8
[13825.193470] Aborting journal on device sdb1-8.
[13825.194356] EXT4-fs error (device sdb1) in ext4_reserve_inode_write: Journal has aborted
[13825.199380] JBD2: Detected IO errors while flushing file data on sdb2-8
[13825.199443] Aborting journal on device sdb2-8.
[13825.199478] JBD2: I/O error detected when updating journal superblock for sdb1-8.
[13825.199641] JBD2: I/O error detected when updating journal superblock for sdb2-8.
[13825.199664] EXT4-fs (sdb2): delayed block allocation failed for inode 524328 at logical offset 0 with max blocks 1 with error -30
[13825.199676] 
[13825.199678] This should not happen!!  Data will be lost
[13825.199703] EXT4-fs error (device sdb2) in ext4_da_writepages: Journal has aborted
[13825.199888] journal commit I/O error
[13825.201215] EXT4-fs error (device sdb2): ext4_journal_start_sb: Detected aborted journal
[13825.201284] EXT4-fs (sdb2): Remounting filesystem read-only
[13825.202562] EXT4-fs (sdb2): ext4_da_writepages: jbd2_start: 1021 pages, ino 524328; err -30
[13825.202622] EXT4-fs error (device sdb1) in ext4_dirty_inode: Journal has aborted
[13825.202629] EXT4-fs (sdb1): previous I/O error to superblock detected
[13825.202705] 
[13825.202740] EXT4-fs error (device sdb1): ext4_journal_start_sb: Detected aborted journal
[13825.202797] EXT4-fs (sdb1): Remounting filesystem read-only
[13825.212586] JBD2: Detected IO errors while flushing file data on sdb1-8
[13825.450040] usb 1-2: new high speed USB device using ehci_hcd and address 3
[13840.570066] usb 1-2: device descriptor read/64, error -110
[13855.800062] usb 1-2: device descriptor read/64, error -110
[13855.810268] EXT4-fs error (device sdb1): ext4_find_entry: reading directory #2 offset 0
[13855.810433] EXT4-fs error (device sdb1): ext4_find_entry: reading directory #2 offset 0
[13856.030034] usb 1-2: new high speed USB device using ehci_hcd and address 4
[13856.040214] EXT4-fs error (device sdb1): ext4_find_entry: reading directory #2 offset 0
[13871.150063] usb 1-2: device descriptor read/64, error -110
[13886.380037] usb 1-2: device descriptor read/64, error -110
[13886.610051] usb 1-2: new high speed USB device using ehci_hcd and address 5
[13897.030030] usb 1-2: device not accepting address 5, error -110
[13897.150065] usb 1-2: new high speed USB device using ehci_hcd and address 6
[13907.570030] usb 1-2: device not accepting address 6, error -110
[13907.570090] hub 1-0:1.0: unable to enumerate USB device on port 2
[13907.950037] usb 3-2: new full speed USB device using uhci_hcd and address 2
[13923.070047] usb 3-2: device descriptor read/64, error -110
[13938.300034] usb 3-2: device descriptor read/64, error -110
[13938.530031] usb 3-2: new full speed USB device using uhci_hcd and address 3
[13953.650035] usb 3-2: device descriptor read/64, error -110
[13968.890033] usb 3-2: device descriptor read/64, error -110
[13969.120035] usb 3-2: new full speed USB device using uhci_hcd and address 4
[13979.540035] usb 3-2: device not accepting address 4, error -110
[13979.660036] usb 3-2: new full speed USB device using uhci_hcd and address 5
[13990.080030] usb 3-2: device not accepting address 5, error -110
[13990.080094] hub 3-0:1.0: unable to enumerate USB device on port 2
[18231.563159] EXT4-fs error (device sdb1): ext4_find_entry: reading directory #2 offset 0

```The last message repeats many times until the end of the log.

Can someone please help me figuring out what is going on? Is it hardware?

Thanks
Bakmeel

---

### Post by Fafler on 2010-08-17
The USB to IDE bridge seems to reset itself. It might be a power issue. Is it a 2.5" drive being fed from the USB port? Does it have one or two USB connectors in the PC end of the cable? If it only have one connector, you probably need to get a cable with two. Is there any specific reason you dont interenalize the drive?

---

### Post by Bakmeel on 2010-08-17
It is a 1.8" drive that should be able to run on a single port (according to spec)... This is the mftr link: [http://www.samsung.com/global/business/hdd/productmodel.do?group=72&type=93&subtype=95&model_cd=431&ppmi=1219](http://www.samsung.com/global/business/hdd/productmodel.do?group=72&type=93&subtype=95&model_cd=431&ppmi=1219)

The disk is actually half-internal.. The whole thing is tucked away inside the server enclosure. I made my own little cable to attach it directly to a free USB header on the motherboard.

The motherboard is a Supermicro X7SPA-HF: [http://www.supermicro.com/products/motherboard/ATOM/ICH9/X7SPA.cfm?typ=H&IPMI=Y](http://www.supermicro.com/products/motherboard/ATOM/ICH9/X7SPA.cfm?typ=H&IPMI=Y)

The reasoning behind putting it like this is as follows:
- The motherboard has 6 SATA channels.. 1 for the system drive, 1 for the DVD, and 4 to be used in a hot-swappable RAID-5 configuration. These drives are yet to be installed (so they are not in fstab).
- The system drive is a Kingston 64GB SSD. In an attempt to reduce read/write cycles, temp files are on a ramdisk. There is no swap, and the filesystem on the SSD is ext2 (because ext2 has no journalling)
- In order to save up some space on the system, and to further reduce read/write cycles on the SSD, I decided to install a small USB drive that would be able to run from USB power, while large enough to hold a few torrents. In the mean while I figured it might be nice to put the log files there too, for the above reasons.

---

### Post by Bakmeel on 2010-08-17
It appears that when I unplug the drive and plug it back in, and then do sudo mount -all, the drive comes back online.
It is now in sde however instead of sdb, while it is in exactly the same port as it used to be... could be a detail??

But I bet it will go again in a few hours or so, and I don't like to open up the server every day ;)

---

### Post by Fafler on 2010-08-17
That seems reasonable :-)

Is it possible for you to test the drive with another controller?

And is the Matrox G200ew any good?

---

### Post by Bakmeel on 2010-08-17
> **Fafler said:**
> That seems reasonable :-)

Is it possible for you to test the drive with another controller?

Yes. That would imply however to stop the server for a while a do a few torrents on my own laptop. But it's certainly doable. I'll give it a try tonight. My laptop is running Ubuntu 10.04 too...

> **Fafler said:**
> 
And is the Matrox G200ew any good?
I wouldn't know actually... the server is headless... It's not causing any trouble though :D.

I did try to run gparted once on the system, and that was giving me some issues on the graphics... But for command line it's OK...

---

### Post by Bakmeel on 2010-08-17
I have found an old thread in the Ubuntu forum archives that seems to relate to this: [http://ubuntuforums.org/showthread.php?t=663279](http://ubuntuforums.org/showthread.php?t=663279)

In this thread, the disconnecting of the USB drive is reported as a bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235)

The bug reappears through several releases even until end of last year where it was tagged as regression-potential.

Reading through the bug report, and comparing to my dmesg log above, there appears to be some similarity... Could someone confirm this is the same bug?

Thanks

---

### Post by mlentink on 2010-08-17
Interesting.

I use my Samsung S1 mini to store my music on so I can easliy take it with me. But after a couple of hours of play it does exactly the same as yours, and I need to plug it out and back in to get it working again. 
Think I might try it with a double lead USB cable, but that may take a while...

---

### Post by Bakmeel on 2010-08-17
Some more info... funny things happened...

Before I unplugged and re-plugged the drive, I tried to remount it. Here's what I did:

sudo mount -all <-- didn't work.. see first post.

```
fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sdb1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no
```

Mounted??? But it didn't even exist?? and it is certainly not mounted!

```
me@system:/$ sudo umount /dev/sdb1
umount: /var/log: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

Busy even.... I tried to force umount. Same response

lsof did show a few processes using /var/log and the torrents folder...
Logically, because the log files are used all the time...

Strange....

---

### Post by Bakmeel on 2010-08-19
I have tested the USB drive on another system by running a torrent overnight.
The drive remained accessible and the torrent finished.

The other system was my Laptop (Asus M51Va) with Ubuntu 10.04 64bit

---

### Post by Severun on 2010-08-20
I have the same problem w/ a Maxtor External 1TB external US drive.

Also this problem started happening just after I upgraded from Hardy to Lucid.  I've been putting it off for awhile, but the system and the USB drive have run fine until the upgrade.  Now it will mount, etc, but after awhile I get 

USB disconnect, address 27
Aug 20 08:07:46 monstro kernel: [74559.800090] sd 15:0:0:0: Device offlined - not ready after error recovery
Aug 20 08:07:46 monstro kernel: [74559.800102] sd 15:0:0:0: [sdb] Unhandled error code
Aug 20 08:07:46 monstro kernel: [74559.800105] sd 15:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Aug 20 08:07:46 monstro kernel: [74559.800110] sd 15:0:0:0: [sdb] CDB: Read(10): 28 00 01 81 22 8f 00 00 f0 00
Aug 20 08:07:46 monstro kernel: [74559.800216] sd 15:0:0:0: [sdb] Unhandled error code
Aug 20 08:07:46 monstro kernel: [74559.800220] sd 15:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK

And it's done.  If I unplug and plug the drive back in it will work fine for awhile, then it goes away again w/ the above error.

I would have suspected hardware, but it worked fine on Hardy.

---

### Post by sblanzio on 2010-10-19
I got the same issue with a verbatim store'n'go 250Gb usb external drive.

The problems comes expecially when running rtorrent and saving files on the drive on ubuntu 9.10.
This even happens on a lenny debian workstation.

Someone suggests to keep the drive online using a crontab process to touch a file inside the drive to avoid sleep time, but it doesn't work for me.

The drives just disconnects, even using intermediate USB hubs.

If any of you solved the problem please let me know.
thank you very much

---

### Post by cbraxton on 2010-11-11
I'm seeing this problem as well, it may have to do with the USB chipset(s) involved.

In the last month or so I've deployed 4 Ubuntu 10.04 servers in small businesses. The servers are identical hardware-wise and 2.5" USB hard drives are used for backups. The USB drives used are different in each case.

Just one of these servers is displaying instability with the USB drives, which are Hitachi. (The drives do not mount automatically, they are mounted/dismounted via the backup script.) What occurs is that when you first attempt to mount the drive the device node will sometimes disappear, and dmesg displays various I/O errors similar to those that others have noted. After about a minute the device node will reappear, though it may not be the same. (For example, /dev/sdc may change to /dev/sdd). After this occurs it is possible to mount and use the drive.

Fortunately, once mounted the drive so far stays online long enough to complete the backup and it is possible to work around this fault in the backup script. Very annoying though, and this did NOT occur with these drives on the very old Mandrake Linux server that we replaced, so I do not believe it's an issue of the drives going to sleep.  Google searches reveal this has been an ongoing problem for at least a few years now.

---

### Post by TopicMapper333 on 2010-12-22
I have this problem on two servers running 10.10, each of which has 5 usb disk drives connected via usb.  These disks have backups on them which are renewed every night via rsync.  

About once a week, I don't receive a backup report from one of the servers, because one of the backups has stalled.  It always turns out that one of the USB disks -- the one being backed-up-to -- has its disk-access light solidly lit (or, in the case of some of them, the disk-access light has gone out, which means the same thing).  When I do an ls of the directory the disk is mounted on, there's no output and ls just hangs.  When I look at var/log/syslog, I see evidence that the system is trying, unsuccessfully, to reset the disk in question every few seconds:

Dec 22 10:01:02 tacho kernel: [268394.077906] usb 1-3: reset high speed USB device using ehci_hcd and address 3
Dec 22 10:01:02 tacho kernel: [268394.237237] sd 11:0:0:0: [sdf] Unhandled error code
Dec 22 10:01:02 tacho kernel: [268394.237240] sd 11:0:0:0: [sdf] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Dec 22 10:01:02 tacho kernel: [268394.237245] sd 11:0:0:0: [sdf] CDB: Read(10): 28 00 2e b5 36 bf 00 00 08 00
Dec 22 10:01:02 tacho kernel: [268394.237254] end_request: I/O error, dev sdf, sector 783627967
Dec 22 10:01:02 tacho kernel: [268394.237360] REISERFS error (device sdf1): zam-7001 reiserfs_find_entry: io error

All this is nasty enough, but it gets worse.  I have tried everything I can think of, but apparently there is no way to restore access to the disk, short of removing power from the disk.  In other words, I have to be physically present at the server in order to get the disk going again.  Even worse: if I attempt to reboot the machine, the machine can't bring itself down.  It hangs during the shutdown process, which means that I have to be physically present at the machine in order to regain ANY kind of access to the machine.  Even worse than that: I have to remove power from, or hard-reset, the machine without an orderly shutdown process; there's just nothing else to be done because the machine does not respond to anything else, once it has started its shutdown process and has hung itself up trying to unmount the disk that's in trouble.  And that spells trouble for the machine's software RAID (which has always recovered, eventually, after rebooting but this REALLY gives me the willies).  (The RAID has nothing to do with the USB disks, BTW.)

I'm not competent to fix this problem, but it seems to me that the problem has existed long enough now, and it's more than serious enough, to be worthy of the most serious attention.  I will be glad to cooperate in any way.

I tried to attach lshw output to this, but I'm too dense to figure out how I'm supposed to do that.  So, here is that output, cut-and-pasted here:

root@tacho:~# lshw -xml
<?xml version="1.0" standalone="yes" ?>
<!-- generated by lshw-B.02.14 -->
<!-- GCC 4.4.3 -->
<!-- Linux 2.6.32-26-generic #47-Ubuntu SMP Wed Nov 17 15:58:05 UTC 2010 x86_64 -->
<!-- GNU libc 2 (glibc 2.11.1) -->
<node id="tacho" claimed="true" class="system" handle="DMI:0001">
 <description>Desktop Computer</description>
 <product>To Be Filled By O.E.M.</product>
 <vendor>To Be Filled By O.E.M.</vendor>
 <version>To Be Filled By O.E.M.</version>
 <serial>To Be Filled By O.E.M.</serial>
 <width units="bits">64</width>
 <configuration>
  <setting id="boot" value="normal" />
  <setting id="chassis" value="desktop" />
  <setting id="uuid" value="00020003-0004-0005-0006-000700080009" />
 </configuration>
 <capabilities>
  <capability id="smbios-2.5" >SMBIOS version 2.5</capability>
  <capability id="dmi-2.5" >DMI version 2.5</capability>
  <capability id="vsyscall64" >64-bit processes</capability>
  <capability id="vsyscall32" >32-bit processes</capability>
 </capabilities>
  <node id="core" claimed="true" class="bus" handle="DMI:0002">
   <description>Motherboard</description>
   <product>X58 Extreme</product>
   <vendor>ASRock</vendor>
   <physid>0</physid>
    <node id="firmware" claimed="true" class="memory" handle="">
     <description>BIOS</description>
     <vendor>American Megatrends Inc.</vendor>
     <physid>0</physid>
     <version>P2.50 (08/16/2010)</version>
     <size units="bytes">65536</size>
     <capacity units="bytes">983040</capacity>
     <capabilities>
      <capability id="pci" >PCI bus</capability>
      <capability id="upgrade" >BIOS EEPROM can be upgraded</capability>
      <capability id="shadowing" >BIOS shadowing</capability>
      <capability id="cdboot" >Booting from CD-ROM/DVD</capability>
      <capability id="bootselect" >Selectable boot path</capability>
      <capability id="socketedrom" >BIOS ROM is socketed</capability>
      <capability id="edd" >Enhanced Disk Drive extensions</capability>
      <capability id="int13floppy1200" >5.25&quot; 1.2MB floppy</capability>
      <capability id="int13floppy720" >3.5&quot; 720KB floppy</capability>
      <capability id="int13floppy2880" >3.5&quot; 2.88MB floppy</capability>
      <capability id="int5printscreen" >Print Screen key</capability>
      <capability id="int9keyboard" >i8042 keyboard controller</capability>
      <capability id="int14serial" >INT14 serial line control</capability>
      <capability id="int17printer" >INT17 printer control</capability>
      <capability id="int10video" >INT10 CGA/Mono video</capability>
      <capability id="acpi" >ACPI</capability>
      <capability id="usb" >USB legacy emulation</capability>
      <capability id="ls120boot" >Booting from LS-120</capability>
      <capability id="zipboot" >Booting from ATAPI ZIP</capability>
      <capability id="biosbootspecification" >BIOS boot specification</capability>
      <capability id="netboot" >Function-key initiated network service boot</capability>
     </capabilities>
    </node>
    <node id="cpu" claimed="true" class="processor" handle="DMI:0004">
     <description>CPU</description>
     <product>Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz</product>
     <vendor>Intel Corp.</vendor>
     <physid>4</physid>
     <businfo>cpu@0</businfo>
     <version>Intel(R) Core(TM) i7 CPU         930  @ 2.80GHz</version>
     <serial>To Be Filled By O.E.M.</serial>
     <slot>CPUSocket</slot>
     <size units="Hz">1600000000</size>
     <capacity units="Hz">2800000000</capacity>
     <width units="bits">64</width>
     <clock units="Hz">133000000</clock>
     <capabilities>
      <capability id="fpu" >mathematical co-processor</capability>
      <capability id="fpu_exception" >FPU exceptions reporting</capability>
      <capability id="wp" />
      <capability id="vme" >virtual mode extensions</capability>
      <capability id="de" >debugging extensions</capability>
      <capability id="pse" >page size extensions</capability>
      <capability id="tsc" >time stamp counter</capability>
      <capability id="msr" >model-specific registers</capability>
      <capability id="pae" >4GB+ memory addressing (Physical Address Extension)</capability>
      <capability id="mce" >machine check exceptions</capability>
      <capability id="cx8" >compare and exchange 8-byte</capability>
      <capability id="apic" >on-chip advanced programmable interrupt controller (APIC)</capability>
      <capability id="sep" >fast system calls</capability>
      <capability id="mtrr" >memory type range registers</capability>
      <capability id="pge" >page global enable</capability>
      <capability id="mca" >machine check architecture</capability>
      <capability id="cmov" >conditional move instruction</capability>
      <capability id="pat" >page attribute table</capability>
      <capability id="pse36" >36-bit page size extensions</capability>
      <capability id="clflush" />
      <capability id="dts" >debug trace and EMON store MSRs</capability>
      <capability id="acpi" >thermal control (ACPI)</capability>
      <capability id="mmx" >multimedia extensions (MMX)</capability>
      <capability id="fxsr" >fast floating point save/restore</capability>
      <capability id="sse" >streaming SIMD extensions (SSE)</capability>
      <capability id="sse2" >streaming SIMD extensions (SSE2)</capability>
      <capability id="ss" >self-snoop</capability>
      <capability id="ht" >HyperThreading</capability>
      <capability id="tm" >thermal interrupt and status</capability>
      <capability id="pbe" >pending break event</capability>
      <capability id="syscall" >fast system calls</capability>
      <capability id="nx" >no-execute bit (NX)</capability>
      <capability id="rdtscp" />
      <capability id="x86-64" >64bits extensions (x86-64)</capability>
      <capability id="constant_tsc" />
      <capability id="arch_perfmon" />
      <capability id="pebs" />
      <capability id="bts" />
      <capability id="rep_good" />
      <capability id="xtopology" />
      <capability id="nonstop_tsc" />
      <capability id="aperfmperf" />
      <capability id="pni" />
      <capability id="dtes64" />
      <capability id="monitor" />
      <capability id="ds_cpl" />
      <capability id="vmx" />
      <capability id="est" />
      <capability id="tm2" />
      <capability id="ssse3" />
      <capability id="cx16" />
      <capability id="xtpr" />
      <capability id="pdcm" />
      <capability id="sse4_1" />
      <capability id="sse4_2" />
      <capability id="popcnt" />
      <capability id="lahf_lm" />
      <capability id="ida" />
      <capability id="tpr_shadow" />
      <capability id="vnmi" />
      <capability id="flexpriority" />
      <capability id="ept" />
      <capability id="vpid" />
      <capability id="cpufreq" >CPU Frequency scaling</capability>
     </capabilities>
      <node id="cache:0" claimed="true" class="memory" handle="DMI:0005">
       <description>L1 cache</description>
       <physid>5</physid>
       <slot>L1-Cache</slot>
       <size units="bytes">262144</size>
       <capacity units="bytes">262144</capacity>
       <capabilities>
        <capability id="internal" >Internal</capability>
        <capability id="write-through" >Write-trough</capability>
        <capability id="instruction" >Instruction cache</capability>
       </capabilities>
      </node>
      <node id="cache:1" claimed="true" class="memory" handle="DMI:0006">
       <description>L2 cache</description>
       <physid>6</physid>
       <slot>L2-Cache</slot>
       <size units="bytes">1048576</size>
       <capacity units="bytes">1048576</capacity>
       <capabilities>
        <capability id="internal" >Internal</capability>
        <capability id="write-through" >Write-trough</capability>
        <capability id="unified" >Unified cache</capability>
       </capabilities>
      </node>
      <node id="cache:2" claimed="true" class="memory" handle="DMI:0007">
       <description>L3 cache</description>
       <physid>7</physid>
       <slot>L3-Cache</slot>
       <size units="bytes">8388608</size>
       <capacity units="bytes">8388608</capacity>
       <capabilities>
        <capability id="internal" >Internal</capability>
        <capability id="write-back" >Write-back</capability>
        <capability id="unified" >Unified cache</capability>
       </capabilities>
      </node>
    </node>
    <node id="memory" claimed="true" class="memory" handle="DMI:000F">
     <description>System Memory</description>
     <physid>f</physid>
     <slot>System board or motherboard</slot>
     <size units="bytes">6442450944</size>
      <node id="bank:0" claimed="true" class="memory" handle="DMI:0011">
       <description>DIMM 1333 MHz (0.8 ns)</description>
       <product>CM3X2G1600C9</product>
       <vendor>Corsair</vendor>
       <physid>0</physid>
       <serial>00000000</serial>
       <slot>DIMM0</slot>
       <size units="bytes">2147483648</size>
       <width units="bits">64</width>
       <clock units="Hz">1333000000</clock>
      </node>
      <node id="bank:1" claimed="true" class="memory" handle="DMI:0013">
       <description>DIMM 1333 MHz (0.8 ns) [empty]</description>
       <vendor>Manufacturer01</vendor>
       <physid>1</physid>
       <serial>00000000</serial>
       <slot>DIMM1</slot>
       <width units="bits">64</width>
       <clock units="Hz">1333000000</clock>
      </node>
      <node id="bank:2" claimed="true" class="memory" handle="DMI:0015">
       <description>DIMM 1333 MHz (0.8 ns)</description>
       <vendor>Manufacturer02</vendor>
       <physid>2</physid>
       <serial>00000000</serial>
       <slot>DIMM2</slot>
       <size units="bytes">2147483648</size>
       <width units="bits">64</width>
       <clock units="Hz">1333000000</clock>
      </node>
      <node id="bank:3" claimed="true" class="memory" handle="DMI:0017">
       <description>DIMM 1333 MHz (0.8 ns) [empty]</description>
       <product>CM3X2G1600C9</product>
       <vendor>Corsair</vendor>
       <physid>3</physid>
       <serial>00000000</serial>
       <slot>DIMM3</slot>
       <width units="bits">64</width>
       <clock units="Hz">1333000000</clock>
      </node>
      <node id="bank:4" claimed="true" class="memory" handle="DMI:0019">
       <description>DIMM 1333 MHz (0.8 ns)</description>
       <vendor>Manufacturer04</vendor>
       <physid>4</physid>
       <serial>00000000</serial>
       <slot>DIMM4</slot>
       <size units="bytes">2147483648</size>
       <width units="bits">64</width>
       <clock units="Hz">1333000000</clock>
      </node>
      <node id="bank:5" claimed="true" class="memory" handle="DMI:001B">
       <description>DIMM 1333 MHz (0.8 ns) [empty]</description>
       <vendor>Manufacturer05</vendor>
       <physid>5</physid>
       <serial>00000000</serial>
       <slot>DIMM5</slot>
       <width units="bits">64</width>
       <clock units="Hz">1333000000</clock>
      </node>
    </node>
    <node id="pci" claimed="true" class="bridge" handle="PCIBUS:0000:00">
     <description>Host bridge</description>
     <product>5520/5500/X58 I/O Hub to ESI Port</product>
     <vendor>Intel Corporation</vendor>
     <physid>100</physid>
     <businfo>pci@0000:00:00.0</businfo>
     <version>13</version>
     <width units="bits">32</width>
     <clock units="Hz">33000000</clock>
      <node id="pci:0" claimed="true" class="bridge" handle="PCIBUS:0000:06">
       <description>PCI bridge</description>
       <product>5520/5500/X58 I/O Hub PCI Express Root Port 1</product>
       <vendor>Intel Corporation</vendor>
       <physid>1</physid>
       <businfo>pci@0000:00:01.0</businfo>
       <version>13</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="pcieport" />
       </configuration>
       <capabilities>
        <capability id="pci" />
        <capability id="msi" >Message Signalled Interrupts</capability>
        <capability id="pciexpress" >PCI Express</capability>
        <capability id="pm" >Power Management</capability>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;24" />
       </resources>
      </node>
      <node id="pci:1" claimed="true" class="bridge" handle="PCIBUS:0000:04">
       <description>PCI bridge</description>
       <product>5520/5500/X58 I/O Hub PCI Express Root Port 3</product>
       <vendor>Intel Corporation</vendor>
       <physid>3</physid>
       <businfo>pci@0000:00:03.0</businfo>
       <version>13</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="pcieport" />
       </configuration>
       <capabilities>
        <capability id="pci" />
        <capability id="msi" >Message Signalled Interrupts</capability>
        <capability id="pciexpress" >PCI Express</capability>
        <capability id="pm" >Power Management</capability>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;25" />
        <resource type="ioport&quot; value=&quot;e000(size=4096)" />
        <resource type="memory&quot; value=&quot;fbe00000-fbefffff" />
        <resource type="ioport&quot; value=&quot;d0000000(size=268435456)" />
       </resources>
        <node id="display" claimed="true" class="display" handle="PCI:0000:04:00.0">
         <description>VGA compatible controller</description>
         <product>RV710 [Radeon HD 4350]</product>
         <vendor>ATI Technologies Inc</vendor>
         <physid>0</physid>
         <businfo>pci@0000:04:00.0</businfo>
         <version>00</version>
         <width units="bits">64</width>
         <clock units="Hz">33000000</clock>
         <configuration>
          <setting id="driver" value="radeon" />
          <setting id="latency" value="0" />
         </configuration>
         <capabilities>
          <capability id="pm" >Power Management</capability>
          <capability id="pciexpress" >PCI Express</capability>
          <capability id="msi" >Message Signalled Interrupts</capability>
          <capability id="bus_master" >bus mastering</capability>
          <capability id="cap_list" >PCI capabilities listing</capability>
          <capability id="rom" >extension ROM</capability>
         </capabilities>
         <resources>
          <resource type="irq&quot; value=&quot;31" />
          <resource type="memory&quot; value=&quot;d0000000-dfffffff(prefetchable)" />
          <resource type="memory&quot; value=&quot;fbee0000-fbeeffff" />
          <resource type="ioport&quot; value=&quot;e000(size=256)" />
          <resource type="memory&quot; value=&quot;fbec0000-fbedffff(prefetchable)" />
         </resources>
        </node>
        <node id="multimedia" claimed="true" class="multimedia" handle="PCI:0000:04:00.1">
         <description>Audio device</description>
         <product>RV710/730</product>
         <vendor>ATI Technologies Inc</vendor>
         <physid>0.1</physid>
         <businfo>pci@0000:04:00.1</businfo>
         <version>00</version>
         <width units="bits">64</width>
         <clock units="Hz">33000000</clock>
         <configuration>
          <setting id="driver" value="HDA Intel" />
          <setting id="latency" value="0" />
         </configuration>
         <capabilities>
          <capability id="pm" >Power Management</capability>
          <capability id="pciexpress" >PCI Express</capability>
          <capability id="msi" >Message Signalled Interrupts</capability>
          <capability id="bus_master" >bus mastering</capability>
          <capability id="cap_list" >PCI capabilities listing</capability>
         </capabilities>
         <resources>
          <resource type="irq&quot; value=&quot;17" />
          <resource type="memory&quot; value=&quot;fbefc000-fbefffff" />
         </resources>
        </node>
      </node>
      <node id="pci:2" claimed="true" class="bridge" handle="PCIBUS:0000:05">
       <description>PCI bridge</description>
       <product>5520/5500/X58 I/O Hub PCI Express Root Port 7</product>
       <vendor>Intel Corporation</vendor>
       <physid>7</physid>
       <businfo>pci@0000:00:07.0</businfo>
       <version>13</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="pcieport" />
       </configuration>
       <capabilities>
        <capability id="pci" />
        <capability id="msi" >Message Signalled Interrupts</capability>
        <capability id="pciexpress" >PCI Express</capability>
        <capability id="pm" >Power Management</capability>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;26" />
       </resources>
      </node>
      <node id="generic:0" class="generic" handle="PCI:0000:00:14.0">
       <description>PIC</description>
       <product>5520/5500/X58 I/O Hub System Management Registers</product>
       <vendor>Intel Corporation</vendor>
       <physid>14</physid>
       <businfo>pci@0000:00:14.0</businfo>
       <version>13</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="pciexpress" >PCI Express</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
      </node>
      <node id="generic:1" class="generic" handle="PCI:0000:00:14.1">
       <description>PIC</description>
       <product>5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers</product>
       <vendor>Intel Corporation</vendor>
       <physid>14.1</physid>
       <businfo>pci@0000:00:14.1</businfo>
       <version>13</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="pciexpress" >PCI Express</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
      </node>
      <node id="generic:2" class="generic" handle="PCI:0000:00:14.2">
       <description>PIC</description>
       <product>5520/5500/X58 I/O Hub Control Status and RAS Registers</product>
       <vendor>Intel Corporation</vendor>
       <physid>14.2</physid>
       <businfo>pci@0000:00:14.2</businfo>
       <version>13</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="pciexpress" >PCI Express</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
      </node>
      <node id="generic:3" class="generic" handle="PCI:0000:00:14.3">
       <description>PIC</description>
       <product>5520/5500/X58 I/O Hub Throttle Registers</product>
       <vendor>Intel Corporation</vendor>
       <physid>14.3</physid>
       <businfo>pci@0000:00:14.3</businfo>
       <version>13</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="latency" value="0" />
       </configuration>
      </node>
      <node id="usb:0" claimed="true" class="bus" handle="PCI:0000:00:1a.0">
       <description>USB Controller</description>
       <product>82801JI (ICH10 Family) USB UHCI Controller #4</product>
       <vendor>Intel Corporation</vendor>
       <physid>1a</physid>
       <businfo>pci@0000:00:1a.0</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="uhci_hcd" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;16" />
        <resource type="ioport&quot; value=&quot;9400(size=32)" />
       </resources>
      </node>
      <node id="usb:1" claimed="true" class="bus" handle="PCI:0000:00:1a.1">
       <description>USB Controller</description>
       <product>82801JI (ICH10 Family) USB UHCI Controller #5</product>
       <vendor>Intel Corporation</vendor>
       <physid>1a.1</physid>
       <businfo>pci@0000:00:1a.1</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="uhci_hcd" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;21" />
        <resource type="ioport&quot; value=&quot;9480(size=32)" />
       </resources>
      </node>
      <node id="usb:2" claimed="true" class="bus" handle="PCI:0000:00:1a.2">
       <description>USB Controller</description>
       <product>82801JI (ICH10 Family) USB UHCI Controller #6</product>
       <vendor>Intel Corporation</vendor>
       <physid>1a.2</physid>
       <businfo>pci@0000:00:1a.2</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="uhci_hcd" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;19" />
        <resource type="ioport&quot; value=&quot;9800(size=32)" />
       </resources>
      </node>
      <node id="usb:3" claimed="true" class="bus" handle="PCI:0000:00:1a.7">
       <description>USB Controller</description>
       <product>82801JI (ICH10 Family) USB2 EHCI Controller #2</product>
       <vendor>Intel Corporation</vendor>
       <physid>1a.7</physid>
       <businfo>pci@0000:00:1a.7</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="ehci_hcd" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="pm" >Power Management</capability>
        <capability id="debug" >Debug port</capability>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;18" />
        <resource type="memory&quot; value=&quot;fbaf8000-fbaf83ff" />
       </resources>
      </node>
      <node id="multimedia" claimed="true" class="multimedia" handle="PCI:0000:00:1b.0">
       <description>Audio device</description>
       <product>82801JI (ICH10 Family) HD Audio Controller</product>
       <vendor>Intel Corporation</vendor>
       <physid>1b</physid>
       <businfo>pci@0000:00:1b.0</businfo>
       <version>00</version>
       <width units="bits">64</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="HDA Intel" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="pm" >Power Management</capability>
        <capability id="msi" >Message Signalled Interrupts</capability>
        <capability id="pciexpress" >PCI Express</capability>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;22" />
        <resource type="memory&quot; value=&quot;fbaf4000-fbaf7fff" />
       </resources>
      </node>
      <node id="pci:3" claimed="true" class="bridge" handle="PCIBUS:0000:02">
       <description>PCI bridge</description>
       <product>82801JI (ICH10 Family) PCI Express Root Port 1</product>
       <vendor>Intel Corporation</vendor>
       <physid>1c</physid>
       <businfo>pci@0000:00:1c.0</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="pcieport" />
       </configuration>
       <capabilities>
        <capability id="pci" />
        <capability id="pciexpress" >PCI Express</capability>
        <capability id="msi" >Message Signalled Interrupts</capability>
        <capability id="pm" >Power Management</capability>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;27" />
        <resource type="ioport&quot; value=&quot;c000(size=4096)" />
        <resource type="memory&quot; value=&quot;fbc00000-fbcfffff" />
        <resource type="memory&quot; value=&quot;cc000000-cc1fffff(prefetchable)" />
       </resources>
        <node id="storage" claimed="true" class="storage" handle="PCI:0000:02:00.0">
         <description>SATA controller</description>
         <product>JMB360 AHCI Controller</product>
         <vendor>JMicron Technology Corp.</vendor>
         <physid>0</physid>
         <businfo>pci@0000:02:00.0</businfo>
         <logicalname>scsi10</logicalname>
         <version>02</version>
         <width units="bits">32</width>
         <clock units="Hz">33000000</clock>
         <configuration>
          <setting id="driver" value="ahci" />
          <setting id="latency" value="0" />
         </configuration>
         <capabilities>
          <capability id="storage" />
          <capability id="pm" >Power Management</capability>
          <capability id="pciexpress" >PCI Express</capability>
          <capability id="bus_master" >bus mastering</capability>
          <capability id="cap_list" >PCI capabilities listing</capability>
          <capability id="emulated" >Emulated device</capability>
         </capabilities>
         <resources>
          <resource type="irq&quot; value=&quot;16" />
          <resource type="ioport&quot; value=&quot;cc00(size=8)" />
          <resource type="ioport&quot; value=&quot;c880(size=4)" />
          <resource type="ioport&quot; value=&quot;c800(size=8)" />
          <resource type="ioport&quot; value=&quot;c480(size=4)" />
          <resource type="ioport&quot; value=&quot;c400(size=16)" />
          <resource type="memory&quot; value=&quot;fbc00000-fbc01fff" />
         </resources>
          <node id="cdrom" claimed="true" class="disk" handle="SCSI:10:00:00:00">
           <description>DVD reader</description>
           <product>iHDS118   5</product>
           <vendor>ATAPI</vendor>
           <physid>0.0.0</physid>
           <businfo>scsi@10:0.0.0</businfo>
           <logicalname>/dev/cdrom</logicalname>
           <logicalname>/dev/dvd</logicalname>
           <logicalname>/dev/scd3</logicalname>
           <logicalname>/dev/sr3</logicalname>
           <dev>11:3</dev>
           <version>RL0B</version>
           <configuration>
            <setting id="ansiversion" value="5" />
            <setting id="status" value="nodisc" />
           </configuration>
           <capabilities>
            <capability id="removable" >support is removable</capability>
            <capability id="audio" >Audio CD playback</capability>
            <capability id="dvd" >DVD playback</capability>
           </capabilities>
          </node>
        </node>
      </node>
      <node id="pci:4" claimed="true" class="bridge" handle="PCIBUS:0000:01">
       <description>PCI bridge</description>
       <product>82801JI (ICH10 Family) PCI Express Root Port 6</product>
       <vendor>Intel Corporation</vendor>
       <physid>1c.5</physid>
       <businfo>pci@0000:00:1c.5</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="pcieport" />
       </configuration>
       <capabilities>
        <capability id="pci" />
        <capability id="pciexpress" >PCI Express</capability>
        <capability id="msi" >Message Signalled Interrupts</capability>
        <capability id="pm" >Power Management</capability>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;28" />
        <resource type="ioport&quot; value=&quot;b000(size=4096)" />
        <resource type="memory&quot; value=&quot;fbb00000-fbbfffff" />
        <resource type="ioport&quot; value=&quot;cff00000(size=1048576)" />
       </resources>
        <node id="network" claimed="true" class="network" handle="PCI:0000:01:00.0">
         <description>Ethernet interface</description>
         <product>RTL8111/8168B PCI Express Gigabit Ethernet controller</product>
         <vendor>Realtek Semiconductor Co., Ltd.</vendor>
         <physid>0</physid>
         <businfo>pci@0000:01:00.0</businfo>
         <logicalname>eth0</logicalname>
         <version>03</version>
         <serial>00:25:22:35:fb:36</serial>
         <size>1000000000</size>
         <capacity>1000000000</capacity>
         <width units="bits">64</width>
         <clock units="Hz">33000000</clock>
         <configuration>
          <setting id="autonegotiation" value="on" />
          <setting id="broadcast" value="yes" />
          <setting id="driver" value="r8169" />
          <setting id="driverversion" value="2.3LK-NAPI" />
          <setting id="duplex" value="full" />
          <setting id="ip" value="192.168.2.37" />
          <setting id="latency" value="0" />
          <setting id="link" value="yes" />
          <setting id="multicast" value="yes" />
          <setting id="port" value="MII" />
          <setting id="speed" value="1GB/s" />
         </configuration>
         <capabilities>
          <capability id="pm" >Power Management</capability>
          <capability id="msi" >Message Signalled Interrupts</capability>
          <capability id="pciexpress" >PCI Express</capability>
          <capability id="msix" >MSI-X</capability>
          <capability id="vpd" >Vital Product Data</capability>
          <capability id="bus_master" >bus mastering</capability>
          <capability id="cap_list" >PCI capabilities listing</capability>
          <capability id="rom" >extension ROM</capability>
          <capability id="ethernet" />
          <capability id="physical" >Physical interface</capability>
          <capability id="tp" >twisted pair</capability>
          <capability id="mii" >Media Independent Interface</capability>
          <capability id="10bt" >10MB/s</capability>
          <capability id="10bt-fd" >10MB/s (full duplex)</capability>
          <capability id="100bt" >100MB/s</capability>
          <capability id="100bt-fd" >100MB/s (full duplex)</capability>
          <capability id="1000bt" >1GB/s</capability>
          <capability id="1000bt-fd" >1GB/s (full duplex)</capability>
          <capability id="autonegotiation" >Auto-negotiation</capability>
         </capabilities>
         <resources>
          <resource type="irq&quot; value=&quot;30" />
          <resource type="ioport&quot; value=&quot;b800(size=256)" />
          <resource type="memory&quot; value=&quot;cffff000-cfffffff(prefetchable)" />
          <resource type="memory&quot; value=&quot;cfff8000-cfffbfff(prefetchable)" />
          <resource type="memory&quot; value=&quot;fbbe0000-fbbfffff(prefetchable)" />
         </resources>
        </node>
      </node>
      <node id="usb:4" claimed="true" class="bus" handle="PCI:0000:00:1d.0">
       <description>USB Controller</description>
       <product>82801JI (ICH10 Family) USB UHCI Controller #1</product>
       <vendor>Intel Corporation</vendor>
       <physid>1d</physid>
       <businfo>pci@0000:00:1d.0</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="uhci_hcd" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;23" />
        <resource type="ioport&quot; value=&quot;9880(size=32)" />
       </resources>
      </node>
      <node id="usb:5" claimed="true" class="bus" handle="PCI:0000:00:1d.1">
       <description>USB Controller</description>
       <product>82801JI (ICH10 Family) USB UHCI Controller #2</product>
       <vendor>Intel Corporation</vendor>
       <physid>1d.1</physid>
       <businfo>pci@0000:00:1d.1</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="uhci_hcd" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;19" />
        <resource type="ioport&quot; value=&quot;9c00(size=32)" />
       </resources>
      </node>
      <node id="usb:6" claimed="true" class="bus" handle="PCI:0000:00:1d.2">
       <description>USB Controller</description>
       <product>82801JI (ICH10 Family) USB UHCI Controller #3</product>
       <vendor>Intel Corporation</vendor>
       <physid>1d.2</physid>
       <businfo>pci@0000:00:1d.2</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="uhci_hcd" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;18" />
        <resource type="ioport&quot; value=&quot;a000(size=32)" />
       </resources>
      </node>
      <node id="usb:7" claimed="true" class="bus" handle="PCI:0000:00:1d.7">
       <description>USB Controller</description>
       <product>82801JI (ICH10 Family) USB2 EHCI Controller #1</product>
       <vendor>Intel Corporation</vendor>
       <physid>1d.7</physid>
       <businfo>pci@0000:00:1d.7</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="driver" value="ehci_hcd" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="pm" >Power Management</capability>
        <capability id="debug" >Debug port</capability>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;23" />
        <resource type="memory&quot; value=&quot;fbafa000-fbafa3ff" />
       </resources>
      </node>
      <node id="pci:5" claimed="true" class="bridge" handle="PCIBUS:0000:03">
       <description>PCI bridge</description>
       <product>82801 PCI Bridge</product>
       <vendor>Intel Corporation</vendor>
       <physid>1e</physid>
       <businfo>pci@0000:00:1e.0</businfo>
       <version>90</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <capabilities>
        <capability id="pci" />
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
       <resources>
        <resource type="ioport&quot; value=&quot;d000(size=4096)" />
        <resource type="memory&quot; value=&quot;fbd00000-fbdfffff" />
        <resource type="memory&quot; value=&quot;cc200000-cc2fffff(prefetchable)" />
       </resources>
        <node id="storage" claimed="true" class="storage" handle="PCI:0000:03:00.0">
         <description>Mass storage controller</description>
         <product>PDC40718 (SATA 300 TX4)</product>
         <vendor>Promise Technology, Inc.</vendor>
         <physid>0</physid>
         <businfo>pci@0000:03:00.0</businfo>
         <logicalname>scsi0</logicalname>
         <logicalname>scsi1</logicalname>
         <logicalname>scsi2</logicalname>
         <logicalname>scsi3</logicalname>
         <version>02</version>
         <width units="bits">32</width>
         <clock units="Hz">66000000</clock>
         <configuration>
          <setting id="driver" value="sata_promise" />
          <setting id="latency" value="72" />
          <setting id="maxlatency" value="18" />
          <setting id="mingnt" value="4" />
         </configuration>
         <capabilities>
          <capability id="storage" />
          <capability id="pm" >Power Management</capability>
          <capability id="bus_master" >bus mastering</capability>
          <capability id="cap_list" >PCI capabilities listing</capability>
          <capability id="rom" >extension ROM</capability>
          <capability id="emulated" >Emulated device</capability>
         </capabilities>
         <resources>
          <resource type="irq&quot; value=&quot;21" />
          <resource type="ioport&quot; value=&quot;dc00(size=128)" />
          <resource type="ioport&quot; value=&quot;d800(size=256)" />
          <resource type="memory&quot; value=&quot;fbdff000-fbdfffff" />
          <resource type="memory&quot; value=&quot;fbdc0000-fbddffff" />
          <resource type="memory&quot; value=&quot;cc200000-cc207fff(prefetchable)" />
         </resources>
          <node id="disk" claimed="true" class="disk" handle="SCSI:00:00:00:00">
           <description>ATA Disk</description>
           <product>WDC WD5000AAJS-0</product>
           <vendor>Western Digital</vendor>
           <physid>0</physid>
           <businfo>scsi@0:0.0.0</businfo>
           <logicalname>/dev/sda</logicalname>
           <dev>8:0</dev>
           <version>12.0</version>
           <serial>WD-WCAPW5877893</serial>
           <size units="bytes">500107862016</size>
           <configuration>
            <setting id="ansiversion" value="5" />
            <setting id="signature" value="66c89b20" />
           </configuration>
           <capabilities>
            <capability id="partitioned" >Partitioned disk</capability>
            <capability id="partitioned:dos" >MS-DOS partition table</capability>
           </capabilities>
            <node id="volume" claimed="true" class="volume" handle="">
             <description>Linux filesystem partition</description>
             <physid>1</physid>
             <businfo>scsi@0:0.0.0,1</businfo>
             <logicalname>/dev/sda1</logicalname>
             <logicalname>/big1</logicalname>
             <dev>8:1</dev>
             <version>3.6</version>
             <serial>44664d37-5eae-496e-bbea-65d3995bf52e</serial>
             <size>500105216000</size>
             <capacity>500105217024</capacity>
             <configuration>
              <setting id="filesystem" value="reiserfs" />
              <setting id="hash" value="r5" />
              <setting id="label" value="big1" />
              <setting id="mount.fstype" value="reiserfs" />
              <setting id="mount.options" value="rw,relatime" />
              <setting id="state" value="mounted" />
             </configuration>
             <capabilities>
              <capability id="primary" >Primary partition</capability>
              <capability id="journaled" />
              <capability id="reiserfs" >Linux ReiserFS</capability>
              <capability id="initialized" >initialized volume</capability>
             </capabilities>
            </node>
          </node>
          <node id="cdrom:0" claimed="true" class="disk" handle="SCSI:01:00:00:00">
           <description>DVD reader</description>
           <product>iHDS118   5</product>
           <vendor>ATAPI</vendor>
           <physid>1</physid>
           <businfo>scsi@1:0.0.0</businfo>
           <logicalname>/dev/cdrom1</logicalname>
           <logicalname>/dev/dvd1</logicalname>
           <logicalname>/dev/scd0</logicalname>
           <logicalname>/dev/sr0</logicalname>
           <dev>11:0</dev>
           <version>RL0A</version>
           <configuration>
            <setting id="ansiversion" value="5" />
            <setting id="status" value="nodisc" />
           </configuration>
           <capabilities>
            <capability id="removable" >support is removable</capability>
            <capability id="audio" >Audio CD playback</capability>
            <capability id="dvd" >DVD playback</capability>
           </capabilities>
          </node>
          <node id="cdrom:1" claimed="true" class="disk" handle="SCSI:02:00:00:00">
           <description>DVD reader</description>
           <product>iHDS118   5</product>
           <vendor>ATAPI</vendor>
           <physid>2</physid>
           <businfo>scsi@2:0.0.0</businfo>
           <logicalname>/dev/cdrom3</logicalname>
           <logicalname>/dev/dvd3</logicalname>
           <logicalname>/dev/scd1</logicalname>
           <logicalname>/dev/sr1</logicalname>
           <dev>11:1</dev>
           <version>RL0A</version>
           <configuration>
            <setting id="ansiversion" value="5" />
            <setting id="status" value="nodisc" />
           </configuration>
           <capabilities>
            <capability id="removable" >support is removable</capability>
            <capability id="audio" >Audio CD playback</capability>
            <capability id="dvd" >DVD playback</capability>
           </capabilities>
          </node>
          <node id="cdrom:2" claimed="true" class="disk" handle="SCSI:03:00:00:00">
           <description>DVD reader</description>
           <product>iHDS118   5</product>
           <vendor>ATAPI</vendor>
           <physid>3</physid>
           <businfo>scsi@3:0.0.0</businfo>
           <logicalname>/dev/cdrom2</logicalname>
           <logicalname>/dev/dvd2</logicalname>
           <logicalname>/dev/scd2</logicalname>
           <logicalname>/dev/sr2</logicalname>
           <dev>11:2</dev>
           <version>RL0A</version>
           <configuration>
            <setting id="ansiversion" value="5" />
            <setting id="status" value="nodisc" />
           </configuration>
           <capabilities>
            <capability id="removable" >support is removable</capability>
            <capability id="audio" >Audio CD playback</capability>
            <capability id="dvd" >DVD playback</capability>
           </capabilities>
          </node>
        </node>
      </node>
      <node id="isa" claimed="true" class="bridge" handle="PCI:0000:00:1f.0">
       <description>ISA bridge</description>
       <product>82801JIR (ICH10R) LPC Interface Controller</product>
       <vendor>Intel Corporation</vendor>
       <physid>1f</physid>
       <businfo>pci@0000:00:1f.0</businfo>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="isa" />
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
       </capabilities>
      </node>
      <node id="storage" claimed="true" class="storage" handle="PCI:0000:00:1f.2">
       <description>SATA controller</description>
       <product>82801JI (ICH10 Family) SATA AHCI Controller</product>
       <vendor>Intel Corporation</vendor>
       <physid>1f.2</physid>
       <businfo>pci@0000:00:1f.2</businfo>
       <logicalname>scsi4</logicalname>
       <logicalname>scsi5</logicalname>
       <logicalname>scsi6</logicalname>
       <logicalname>scsi7</logicalname>
       <logicalname>scsi8</logicalname>
       <logicalname>scsi9</logicalname>
       <version>00</version>
       <width units="bits">32</width>
       <clock units="Hz">66000000</clock>
       <configuration>
        <setting id="driver" value="ahci" />
        <setting id="latency" value="0" />
       </configuration>
       <capabilities>
        <capability id="storage" />
        <capability id="msi" >Message Signalled Interrupts</capability>
        <capability id="pm" >Power Management</capability>
        <capability id="bus_master" >bus mastering</capability>
        <capability id="cap_list" >PCI capabilities listing</capability>
        <capability id="emulated" >Emulated device</capability>
       </capabilities>
       <resources>
        <resource type="irq&quot; value=&quot;29" />
        <resource type="ioport&quot; value=&quot;a880(size=8)" />
        <resource type="ioport&quot; value=&quot;a800(size=4)" />
        <resource type="ioport&quot; value=&quot;a480(size=8)" />
        <resource type="ioport&quot; value=&quot;a400(size=4)" />
        <resource type="ioport&quot; value=&quot;a080(size=32)" />
        <resource type="memory&quot; value=&quot;fbafc000-fbafc7ff" />
       </resources>
        <node id="disk:0" claimed="true" class="disk" handle="SCSI:04:00:00:00">
         <description>ATA Disk</description>
         <product>SAMSUNG HD400LJ</product>
         <physid>0</physid>
         <businfo>scsi@4:0.0.0</businfo>
         <logicalname>/dev/sdb</logicalname>
         <dev>8:16</dev>
         <version>ZZ10</version>
         <serial>S0H2J10L501320</serial>
         <size units="bytes">400088457216</size>
         <configuration>
          <setting id="ansiversion" value="5" />
          <setting id="signature" value="00071d16" />
         </configuration>
         <capabilities>
          <capability id="partitioned" >Partitioned disk</capability>
          <capability id="partitioned:dos" >MS-DOS partition table</capability>
         </capabilities>
          <node id="volume:0" claimed="true" class="volume" handle="">
           <description>Linux raid autodetect partition</description>
           <physid>1</physid>
           <businfo>scsi@4:0.0.0,1</businfo>
           <logicalname>/dev/sdb1</logicalname>
           <dev>8:17</dev>
           <capacity>393999286272</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
           </capabilities>
          </node>
          <node id="volume:1" claimed="true" class="volume" handle="">
           <description>Linux swap volume</description>
           <physid>2</physid>
           <businfo>scsi@4:0.0.0,2</businfo>
           <logicalname>/dev/sdb2</logicalname>
           <dev>8:18</dev>
           <version>1</version>
           <serial>564859eb-c05f-4f34-ac5d-446322fd0f16</serial>
           <size>5198487840</size>
           <capacity>5199888384</capacity>
           <configuration>
            <setting id="filesystem" value="swap" />
            <setting id="pagesize" value="1365" />
           </configuration>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
            <capability id="swap" >Linux swap</capability>
            <capability id="initialized" >initialized volume</capability>
           </capabilities>
          </node>
          <node id="volume:2" claimed="true" class="volume" handle="">
           <description>Linux filesystem partition</description>
           <physid>3</physid>
           <businfo>scsi@4:0.0.0,3</businfo>
           <logicalname>/dev/sdb3</logicalname>
           <logicalname>/boot</logicalname>
           <dev>8:19</dev>
           <version>3.6</version>
           <serial>89f5bb14-89ec-4e15-91b3-4b6481becf05</serial>
           <size>888143872</size>
           <capacity>888143872</capacity>
           <configuration>
            <setting id="filesystem" value="reiserfs" />
            <setting id="hash" value="r5" />
            <setting id="label" value="boot" />
            <setting id="mount.fstype" value="reiserfs" />
            <setting id="mount.options" value="rw,relatime,notail" />
            <setting id="state" value="mounted" />
           </configuration>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="bootable" >Bootable partition (active)</capability>
            <capability id="journaled" />
            <capability id="reiserfs" >Linux ReiserFS</capability>
            <capability id="initialized" >initialized volume</capability>
           </capabilities>
          </node>
        </node>
        <node id="disk:1" claimed="true" class="disk" handle="SCSI:05:00:00:00">
         <description>ATA Disk</description>
         <product>SAMSUNG HD400LJ</product>
         <physid>1</physid>
         <businfo>scsi@5:0.0.0</businfo>
         <logicalname>/dev/sdc</logicalname>
         <dev>8:32</dev>
         <version>ZZ10</version>
         <serial>S0H2J1FL500690</serial>
         <size units="bytes">400088457216</size>
         <configuration>
          <setting id="ansiversion" value="5" />
          <setting id="signature" value="000a7073" />
         </configuration>
         <capabilities>
          <capability id="partitioned" >Partitioned disk</capability>
          <capability id="partitioned:dos" >MS-DOS partition table</capability>
         </capabilities>
          <node id="volume:0" claimed="true" class="volume" handle="">
           <description>Linux raid autodetect partition</description>
           <physid>1</physid>
           <businfo>scsi@5:0.0.0,1</businfo>
           <logicalname>/dev/sdc1</logicalname>
           <dev>8:33</dev>
           <capacity>393999286272</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
           </capabilities>
          </node>
          <node id="volume:1" claimed="true" class="volume" handle="">
           <description>Linux raid autodetect partition</description>
           <physid>2</physid>
           <businfo>scsi@5:0.0.0,2</businfo>
           <logicalname>/dev/sdc2</logicalname>
           <dev>8:34</dev>
           <capacity>5199888384</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
           </capabilities>
          </node>
          <node id="volume:2" claimed="true" class="volume" handle="">
           <description>Linux filesystem partition</description>
           <physid>3</physid>
           <businfo>scsi@5:0.0.0,3</businfo>
           <logicalname>/dev/sdc3</logicalname>
           <dev>8:35</dev>
           <capacity>888143872</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
           </capabilities>
          </node>
        </node>
        <node id="disk:2" claimed="true" class="disk" handle="SCSI:06:00:00:00">
         <description>ATA Disk</description>
         <product>SAMSUNG HD400LJ</product>
         <physid>2</physid>
         <businfo>scsi@6:0.0.0</businfo>
         <logicalname>/dev/sdd</logicalname>
         <dev>8:48</dev>
         <version>ZZ10</version>
         <serial>S0H2J1FL500948</serial>
         <size units="bytes">400088457216</size>
         <configuration>
          <setting id="ansiversion" value="5" />
          <setting id="signature" value="000e8d8c" />
         </configuration>
         <capabilities>
          <capability id="partitioned" >Partitioned disk</capability>
          <capability id="partitioned:dos" >MS-DOS partition table</capability>
         </capabilities>
          <node id="volume:0" claimed="true" class="volume" handle="">
           <description>Linux raid autodetect partition</description>
           <physid>1</physid>
           <businfo>scsi@6:0.0.0,1</businfo>
           <logicalname>/dev/sdd1</logicalname>
           <dev>8:49</dev>
           <capacity>393999286272</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
           </capabilities>
          </node>
          <node id="volume:1" claimed="true" class="volume" handle="">
           <description>Linux raid autodetect partition</description>
           <physid>2</physid>
           <businfo>scsi@6:0.0.0,2</businfo>
           <logicalname>/dev/sdd2</logicalname>
           <dev>8:50</dev>
           <capacity>5199888384</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
           </capabilities>
          </node>
          <node id="volume:2" claimed="true" class="volume" handle="">
           <description>Linux filesystem partition</description>
           <physid>3</physid>
           <businfo>scsi@6:0.0.0,3</businfo>
           <logicalname>/dev/sdd3</logicalname>
           <dev>8:51</dev>
           <capacity>888143872</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
           </capabilities>
          </node>
        </node>
        <node id="disk:3" claimed="true" class="disk" handle="SCSI:07:00:00:00">
         <description>ATA Disk</description>
         <product>SAMSUNG HD400LJ</product>
         <physid>3</physid>
         <businfo>scsi@7:0.0.0</businfo>
         <logicalname>/dev/sde</logicalname>
         <dev>8:64</dev>
         <version>ZZ10</version>
         <serial>S0H2J1UL604487</serial>
         <size units="bytes">400088457216</size>
         <configuration>
          <setting id="ansiversion" value="5" />
          <setting id="signature" value="00036885" />
         </configuration>
         <capabilities>
          <capability id="partitioned" >Partitioned disk</capability>
          <capability id="partitioned:dos" >MS-DOS partition table</capability>
         </capabilities>
          <node id="volume:0" claimed="true" class="volume" handle="">
           <description>Linux raid autodetect partition</description>
           <physid>1</physid>
           <businfo>scsi@7:0.0.0,1</businfo>
           <logicalname>/dev/sde1</logicalname>
           <dev>8:65</dev>
           <capacity>393999286272</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
           </capabilities>
          </node>
          <node id="volume:1" claimed="true" class="volume" handle="">
           <description>Linux raid autodetect partition</description>
           <physid>2</physid>
           <businfo>scsi@7:0.0.0,2</businfo>
           <logicalname>/dev/sde2</logicalname>
           <dev>8:66</dev>
           <capacity>5199888384</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
           </capabilities>
          </node>
          <node id="volume:2" claimed="true" class="volume" handle="">
           <description>Linux filesystem partition</description>
           <physid>3</physid>
           <businfo>scsi@7:0.0.0,3</businfo>
           <logicalname>/dev/sde3</logicalname>
           <dev>8:67</dev>
           <capacity>888143872</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
           </capabilities>
          </node>
        </node>
        <node id="disk:4" claimed="true" class="disk" handle="SCSI:08:00:00:00">
         <description>ATA Disk</description>
         <product>WDC WD1001FALS-0</product>
         <vendor>Western Digital</vendor>
         <physid>4</physid>
         <businfo>scsi@8:0.0.0</businfo>
         <logicalname>/dev/sdg</logicalname>
         <dev>8:96</dev>
         <version>05.0</version>
         <serial>WD-WMATV6817591</serial>
         <size units="bytes">1000204886016</size>
         <configuration>
          <setting id="ansiversion" value="5" />
          <setting id="signature" value="00090d91" />
         </configuration>
         <capabilities>
          <capability id="partitioned" >Partitioned disk</capability>
          <capability id="partitioned:dos" >MS-DOS partition table</capability>
         </capabilities>
          <node id="volume" claimed="true" class="volume" handle="">
           <description>Linux filesystem partition</description>
           <physid>1</physid>
           <businfo>scsi@8:0.0.0,1</businfo>
           <logicalname>/dev/sdg1</logicalname>
           <logicalname>/big0</logicalname>
           <dev>8:97</dev>
           <version>3.6</version>
           <serial>edd667de-639f-4d4a-aeef-4d80637f9d50</serial>
           <size>1000203091968</size>
           <capacity>1000203091968</capacity>
           <configuration>
            <setting id="filesystem" value="reiserfs" />
            <setting id="hash" value="r5" />
            <setting id="label" value="big0" />
            <setting id="mount.fstype" value="reiserfs" />
            <setting id="mount.options" value="rw,relatime" />
            <setting id="state" value="mounted" />
           </configuration>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="journaled" />
            <capability id="reiserfs" >Linux ReiserFS</capability>
            <capability id="initialized" >initialized volume</capability>
           </capabilities>
          </node>
        </node>
        <node id="disk:5" claimed="true" class="disk" handle="SCSI:09:00:00:00">
         <description>ATA Disk</description>
         <product>SAMSUNG HD400LJ</product>
         <physid>5</physid>
         <businfo>scsi@9:0.0.0</businfo>
         <logicalname>/dev/sdk</logicalname>
         <dev>8:160</dev>
         <version>ZZ10</version>
         <serial>S0H2J1UL604486</serial>
         <size units="bytes">400088457216</size>
         <configuration>
          <setting id="ansiversion" value="5" />
          <setting id="signature" value="00078403" />
         </configuration>
         <capabilities>
          <capability id="partitioned" >Partitioned disk</capability>
          <capability id="partitioned:dos" >MS-DOS partition table</capability>
         </capabilities>
          <node id="volume:0" claimed="true" class="volume" handle="">
           <description>Linux raid autodetect partition</description>
           <physid>1</physid>
           <businfo>scsi@9:0.0.0,1</businfo>
           <logicalname>/dev/sdk1</logicalname>
           <dev>8:161</dev>
           <capacity>393999286272</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
           </capabilities>
          </node>
          <node id="volume:1" claimed="true" class="volume" handle="">
           <description>Linux raid autodetect partition</description>
           <physid>2</physid>
           <businfo>scsi@9:0.0.0,2</businfo>
           <logicalname>/dev/sdk2</logicalname>
           <dev>8:162</dev>
           <capacity>5199888384</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
            <capability id="multi" >Multi-volumes</capability>
           </capabilities>
          </node>
          <node id="volume:2" claimed="true" class="volume" handle="">
           <description>Linux filesystem partition</description>
           <physid>3</physid>
           <businfo>scsi@9:0.0.0,3</businfo>
           <logicalname>/dev/sdk3</logicalname>
           <dev>8:163</dev>
           <capacity>888143872</capacity>
           <capabilities>
            <capability id="primary" >Primary partition</capability>
           </capabilities>
          </node>
        </node>
      </node>
      <node id="serial" class="bus" handle="PCI:0000:00:1f.3">
       <description>SMBus</description>
       <product>82801JI (ICH10 Family) SMBus Controller</product>
       <vendor>Intel Corporation</vendor>
       <physid>1f.3</physid>
       <businfo>pci@0000:00:1f.3</businfo>
       <version>00</version>
       <width units="bits">64</width>
       <clock units="Hz">33000000</clock>
       <configuration>
        <setting id="latency" value="0" />
       </configuration>
       <resources>
        <resource type="memory&quot; value=&quot;fbafe000-fbafe0ff" />
        <resource type="ioport&quot; value=&quot;400(size=32)" />
       </resources>
      </node>
    </node>
    <node id="scsi:0" claimed="true" class="storage" handle="SCSI:11">
     <physid>1</physid>
     <businfo>usb@1:2</businfo>
     <logicalname>scsi11</logicalname>
     <configuration>
      <setting id="driver" value="usb-storage" />
     </configuration>
     <capabilities>
      <capability id="emulated" >Emulated device</capability>
      <capability id="scsi-host" >SCSI host adapter</capability>
     </capabilities>
      <node id="disk" claimed="true" class="disk" handle="SCSI:11:00:00:00">
       <description>SCSI Disk</description>
       <physid>0.0.0</physid>
       <businfo>scsi@11:0.0.0</businfo>
       <logicalname>/dev/sdf</logicalname>
       <dev>8:80</dev>
       <size units="bytes">1500301910016</size>
       <configuration>
        <setting id="signature" value="d699346b" />
       </configuration>
       <capabilities>
        <capability id="partitioned" >Partitioned disk</capability>
        <capability id="partitioned:dos" >MS-DOS partition table</capability>
       </capabilities>
        <node id="volume" claimed="true" class="volume" handle="">
         <description>Linux filesystem partition</description>
         <physid>1</physid>
         <businfo>scsi@11:0.0.0,1</businfo>
         <logicalname>/dev/sdf1</logicalname>
         <logicalname>/nobackup/pozzoQatBac</logicalname>
         <dev>8:81</dev>
         <version>3.6</version>
         <serial>ffe2a3bd-8a63-4022-b3e7-0ffdf87d3dd5</serial>
         <size>1500299264000</size>
         <capacity>1500299265024</capacity>
         <configuration>
          <setting id="filesystem" value="reiserfs" />
          <setting id="hash" value="r5" />
          <setting id="label" value="pozzoQatBac" />
          <setting id="mount.fstype" value="reiserfs" />
          <setting id="mount.options" value="rw,relatime" />
          <setting id="state" value="mounted" />
         </configuration>
         <capabilities>
          <capability id="primary" >Primary partition</capability>
          <capability id="journaled" />
          <capability id="reiserfs" >Linux ReiserFS</capability>
          <capability id="initialized" >initialized volume</capability>
         </capabilities>
        </node>
      </node>
    </node>
    <node id="scsi:1" claimed="true" class="storage" handle="SCSI:12">
     <physid>2</physid>
     <businfo>usb@1:3</businfo>
     <logicalname>scsi12</logicalname>
     <configuration>
      <setting id="driver" value="usb-storage" />
     </configuration>
     <capabilities>
      <capability id="emulated" >Emulated device</capability>
      <capability id="scsi-host" >SCSI host adapter</capability>
     </capabilities>
      <node id="disk" claimed="true" class="disk" handle="SCSI:12:00:00:00">
       <description>SCSI Disk</description>
       <physid>0.0.0</physid>
       <businfo>scsi@12:0.0.0</businfo>
       <logicalname>/dev/sdh</logicalname>
       <dev>8:112</dev>
       <size units="bytes">500107862016</size>
       <configuration>
        <setting id="signature" value="8e417084" />
       </configuration>
       <capabilities>
        <capability id="partitioned" >Partitioned disk</capability>
        <capability id="partitioned:dos" >MS-DOS partition table</capability>
       </capabilities>
        <node id="volume" claimed="true" class="volume" handle="">
         <description>Linux filesystem partition</description>
         <physid>1</physid>
         <businfo>scsi@12:0.0.0,1</businfo>
         <logicalname>/dev/sdh1</logicalname>
         <logicalname>/nobackup/amati-backup</logicalname>
         <dev>8:113</dev>
         <version>3.6</version>
         <serial>aeca697f-4934-4845-9dcf-93fa8a474ecc</serial>
         <size>500105216000</size>
         <capacity>500105217024</capacity>
         <configuration>
          <setting id="filesystem" value="reiserfs" />
          <setting id="hash" value="r5" />
          <setting id="label" value="amati-backup" />
          <setting id="mount.fstype" value="reiserfs" />
          <setting id="mount.options" value="rw,relatime" />
          <setting id="state" value="mounted" />
         </configuration>
         <capabilities>
          <capability id="primary" >Primary partition</capability>
          <capability id="journaled" />
          <capability id="reiserfs" >Linux ReiserFS</capability>
          <capability id="initialized" >initialized volume</capability>
         </capabilities>
        </node>
      </node>
    </node>
    <node id="scsi:2" claimed="true" class="storage" handle="SCSI:13">
     <physid>3</physid>
     <businfo>usb@1:5</businfo>
     <logicalname>scsi13</logicalname>
     <configuration>
      <setting id="driver" value="usb-storage" />
     </configuration>
     <capabilities>
      <capability id="emulated" >Emulated device</capability>
      <capability id="scsi-host" >SCSI host adapter</capability>
     </capabilities>
      <node id="disk" claimed="true" class="disk" handle="SCSI:13:00:00:00">
       <description>SCSI Disk</description>
       <physid>0.0.0</physid>
       <businfo>scsi@13:0.0.0</businfo>
       <logicalname>/dev/sdi</logicalname>
       <dev>8:128</dev>
       <size units="bytes">1500301910016</size>
       <configuration>
        <setting id="signature" value="abf3e0fb" />
       </configuration>
       <capabilities>
        <capability id="partitioned" >Partitioned disk</capability>
        <capability id="partitioned:dos" >MS-DOS partition table</capability>
       </capabilities>
        <node id="volume" claimed="true" class="volume" handle="">
         <description>Linux filesystem partition</description>
         <physid>1</physid>
         <businfo>scsi@13:0.0.0,1</businfo>
         <logicalname>/dev/sdi1</logicalname>
         <logicalname>/nobackup/guy-prilicla-bac</logicalname>
         <dev>8:129</dev>
         <version>3.6</version>
         <serial>d178dfae-7029-4dc2-97b7-c72ab365acaa</serial>
         <size>1500299264000</size>
         <capacity>1500299265024</capacity>
         <configuration>
          <setting id="filesystem" value="reiserfs" />
          <setting id="hash" value="r5" />
          <setting id="label" value="guy-prilicla-bac" />
          <setting id="mount.fstype" value="reiserfs" />
          <setting id="mount.options" value="rw,relatime" />
          <setting id="state" value="mounted" />
         </configuration>
         <capabilities>
          <capability id="primary" >Primary partition</capability>
          <capability id="journaled" />
          <capability id="reiserfs" >Linux ReiserFS</capability>
          <capability id="initialized" >initialized volume</capability>
         </capabilities>
        </node>
      </node>
    </node>
    <node id="scsi:3" claimed="true" class="storage" handle="SCSI:14">
     <physid>5</physid>
     <businfo>usb@2:1</businfo>
     <logicalname>scsi14</logicalname>
     <configuration>
      <setting id="driver" value="usb-storage" />
     </configuration>
     <capabilities>
      <capability id="emulated" >Emulated device</capability>
      <capability id="scsi-host" >SCSI host adapter</capability>
     </capabilities>
      <node id="disk" claimed="true" class="disk" handle="SCSI:14:00:00:00">
       <description>SCSI Disk</description>
       <physid>0.0.0</physid>
       <businfo>scsi@14:0.0.0</businfo>
       <logicalname>/dev/sdj</logicalname>
       <dev>8:144</dev>
       <size units="bytes">1500301910016</size>
       <configuration>
        <setting id="signature" value="ae4d37ee" />
       </configuration>
       <capabilities>
        <capability id="partitioned" >Partitioned disk</capability>
        <capability id="partitioned:dos" >MS-DOS partition table</capability>
       </capabilities>
        <node id="volume" claimed="true" class="volume" handle="">
         <description>Linux filesystem partition</description>
         <physid>1</physid>
         <businfo>scsi@14:0.0.0,1</businfo>
         <logicalname>/dev/sdj1</logicalname>
         <logicalname>/nobackup/zorbTachoBac</logicalname>
         <dev>8:145</dev>
         <version>3.6</version>
         <serial>3607a7fa-2d5f-452d-b481-fe47aa926c8d</serial>
         <size>1500299264000</size>
         <capacity>1500299265024</capacity>
         <configuration>
          <setting id="filesystem" value="reiserfs" />
          <setting id="hash" value="r5" />
          <setting id="label" value="zorbTachoBac" />
          <setting id="mount.fstype" value="reiserfs" />
          <setting id="mount.options" value="rw,relatime" />
          <setting id="state" value="mounted" />
         </configuration>
         <capabilities>
          <capability id="primary" >Primary partition</capability>
          <capability id="journaled" />
          <capability id="reiserfs" >Linux ReiserFS</capability>
          <capability id="initialized" >initialized volume</capability>
         </capabilities>
        </node>
      </node>
    </node>
  </node>
  <node id="network" disabled="true" claimed="true" class="network" handle="">
   <description>Ethernet interface</description>
   <physid>1</physid>
   <logicalname>vboxnet0</logicalname>
   <serial>0a:00:27:00:00:00</serial>
   <configuration>
    <setting id="broadcast" value="yes" />
    <setting id="multicast" value="yes" />
   </configuration>
   <capabilities>
    <capability id="ethernet" />
    <capability id="physical" >Physical interface</capability>
   </capabilities>
  </node>
</node>
root@tacho:~#

---

### Post by TopicMapper333 on 2011-01-02
I have learned something interesting about this.  Could my problem be defective USB cabling?  Time will tell, but I have made a pretty interesting discovery.  I have made a study of all my USB cables.  I have found a few that MAY be masquerading as USB 2.0 cables when in fact they are USB 1 cables.  Here is the relevant passage from the USB 2.0 spec:

-----------------------------

Marking: The cable must be legibly marked using contrasting color permanent ink.

A. Minimum marking information for high-/full-speed cable must include:

USB SHIELDED <Gauge/2C + Gauge/2C> UL CM 75 oC &#8212; UL Vendor ID.

B. Minimum marking information for low-speed cable shall include:
USB specific marking is not required for low-speed cable.

---------------------------------------------------------

It turns out that some of my cable wiring was printed with the above USB 2.0 legend EXCEPT for the word "SHIELDED".  As I think about it, it seems to me that my whole mysterious problem might be that one or more cables have been unshielded ones.  Apparently, at least 4 USB 2.0 devices I have purchased were supplied with unshielded cables, or at least with cables whose markings do not conform to the USB 2.0 spec.

---

