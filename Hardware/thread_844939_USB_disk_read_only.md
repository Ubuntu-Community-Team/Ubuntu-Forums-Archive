---
title: "USB disk read only"
date: 2008-06-30
forum: Hardware
---

### Post by sn0m on 2008-06-30
Hi guys, can someone help me to change the my usb drive from read only to read/write.
I have a 40gig usb external disk but it dosen't let me write in it, unless i use gksudo.
Is there any way to change the read/write permission.
Kind regards
Sokol

---

### Post by smo0th on 2008-06-30
what are the default drive permissions?

you may try sudo chown -hR <yourusername> /media/<yourUSBdrive>

---

### Post by ukripper on 2008-06-30
> **sn0m said:**
> Hi guys, can someone help me to change the my usb drive from read only to read/write.
I have a 40gig usb external disk but it dosen't let me write in it, unless i use gksudo.
Is there any way to change the read/write permission.
Kind regards
Sokol

If it is ntfs drive then install ntfs-config from synpatic package manager and then go to Applications-->System tools-->ntfs-config

and tick everything there.

If taht doesn't work then post output of the following after plugging in your usb drive:
```
sudo fdisk -l
```

---

### Post by Odrodzona-Sarmacja on 2008-06-30
> **sn0m said:**
> Is there any way to change the read/write permission.

Sure. Edit your /etc/fstab and change settings for your hard drive from "default" to "nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000".

Good luck!

---

### Post by smo0th on 2008-06-30
nice, 3 different options, I'm curious what will work :roll: :-\"

---

### Post by Rocket2DMn on 2008-06-30
sn0m, if you are still having this problem, can you please post the outputs of
```
sudo fdisk -l
mount
cat /etc/fstab
sudo blkid
```

---

### Post by sn0m on 2008-07-02
Hi guys thanks for your help. Unfortunately the usb disk is not showing up at all now. Just to let you know that the disk is actually an old hdd from my laptop. I bougt an appliance that turns it into a usb disk, that initially maunted, now it is not mounted on at all
This is the output from the above command:
sn0m@sn0m-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd25bd25b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            7650        9700    16474657+  83  Linux
/dev/sda3            2551        7649    40957717+   b  W95 FAT32
/dev/sda4            9701        9733      265072+  82  Linux swap / Solaris

Partition table entries are not in disk order
sn0m@sn0m-laptop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sn0m/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sn0m)
/dev/sda3 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
sn0m@sn0m-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=f5d04e39-0dd8-4131-80ce-8082716fb7cc /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda4
UUID=1d3a1451-4221-4177-be06-a955039d5289 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
sn0m@sn0m-laptop:~$ sudo blkid
/dev/sda1: UUID="027C1D867C1D759F" TYPE="ntfs" 
/dev/sda2: UUID="f5d04e39-0dd8-4131-80ce-8082716fb7cc" TYPE="ext3" 
/dev/sda3: UUID="45B1-AC01" TYPE="vfat" 
/dev/sda4: TYPE="swap" UUID="1d3a1451-4221-4177-be06-a955039d5289" 
sn0m@sn0m-laptop:~$ 


Kind regards
Sokol

---

### Post by Rocket2DMn on 2008-07-02
OK, I think it is most likely a problem with the IDE to USB device/case.  Try unplugging the drive, then plugging it back in and immediately running
```
dmesg
```
Post the output here.  If possible, trying plugging the drive externally into a windows machine (assuming its formatted NTFS or FAT32) to see if it is recognized there.  If not, I would try plugging it directly into another laptop to see if it can even boot (or at least try by recognizing the disk).  Otherwise, I would suggest a new external converter/case.
I've had a fair share of problems with external cases before, it's a fairly common problem for people who put the disks and cases together themselves rather than buying them prebuilt.

---

### Post by sn0m on 2008-07-02
This is what i get from lspci

sn0m@sn0m-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
sn0m@sn0m-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


and

sn0m@sn0m-laptop:~$ sudo lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by sn0m on 2008-07-04
And this is what i get from dmesg
[   42.539622] Bluetooth: L2CAP ver 2.9
[   42.539628] Bluetooth: L2CAP socket layer initialized
[   42.581341] Bluetooth: RFCOMM socket layer initialized
[   42.581362] Bluetooth: RFCOMM TTY layer initialized
[   42.581364] Bluetooth: RFCOMM ver 1.8
[   43.791758] Registered led device: b43-phy0:radio
[   44.871439] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[   46.684239] [fglrx] GART Table is not in FRAME_BUFFER range 
[   46.684253] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   46.684256] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000
[   46.834898] [fglrx] interrupt source 20008000 successfully enabled
[   46.834907] [fglrx] enable ID = 0x00000004
[   46.835980] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   96.794846] Clocksource tsc unstable (delta = -174663377 ns)
[  119.776346] NET: Registered protocol family 10
[  119.777759] lo: Disabled Privacy Extensions
[  119.779423] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  119.781324] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   62.807468] NET: Registered protocol family 17
[   64.063165] wlan0: Initial auth_alg=0
[   64.063174] wlan0: authenticate with AP 00:19:5b:7a:4d:21
[   64.064604] wlan0: RX authentication from 00:19:5b:7a:4d:21 (alg=0 transaction=2 status=0)
[   64.064610] wlan0: authenticated
[   64.064613] wlan0: associate with AP 00:19:5b:7a:4d:21
[   64.067052] wlan0: RX AssocResp from 00:19:5b:7a:4d:21 (capab=0x431 status=0 aid=1)
[   64.067056] wlan0: associated
[   64.067061] wlan0: switched to short barker preamble (BSSID=00:19:5b:7a:4d:21)
[   64.068180] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  172.502411] wlan0: no IPv6 routers present
[  135.661867] atieventsd[4974]: segfault at 00000548 eip b7e385c0 esp bff51cb0 error 4
[  363.164817] atieventsd[6184]: segfault at 00000001 eip b7f11cc1 esp bfe8af40 error 4
[  580.277067] wlan0: deauthenticate(reason=3)
[  581.058424] ACPI: PCI interrupt for device 0000:06:06.0 disabled
[  581.261275] ACPI: PCI interrupt for device 0000:06:02.0 disabled
[  583.092967] Syncing filesystems ... done.
[  583.093260] PM: Preparing system for mem sleep
[  583.093830] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  583.094933] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
[  583.191270] PM: Entering mem sleep
[  583.191272] Suspending console(s)
[  583.191302] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  583.414947] sd 0:0:0:0: [sda] Stopping disk
[  584.412771] ACPI handle has no context!
[  584.412880] [fglrx] firegl_gps_setpowerdown .
[  584.429454] ACPI: PCI interrupt for device 0000:01:05.0 disabled
[  584.429614] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[  584.429885] ACPI: PCI interrupt for device 0000:00:14.5 disabled
[  584.430096] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[  584.430201] ACPI: PCI interrupt for device 0000:00:13.2 disabled
[  584.445504] ACPI: PCI interrupt for device 0000:00:13.1 disabled
[  584.445559] ACPI: PCI interrupt for device 0000:00:13.0 disabled
[  584.446300] Disabling non-boot CPUs ...
[    0.392126] Back to C!
[    0.486050] PM: Writing back config space on device 0000:00:01.0 at offset 9 (was 10001, writing cff1c001)
[    0.486072] PM: Writing back config space on device 0000:00:05.0 at offset 9 (was 0, writing fff0)
[    0.486075] PM: Writing back config space on device 0000:00:05.0 at offset 8 (was 0, writing fff0)
[    0.486078] PM: Writing back config space on device 0000:00:05.0 at offset 7 (was 101, writing 1f1)
[    0.486082] PM: Writing back config space on device 0000:00:05.0 at offset 6 (was 0, writing 30200)
[    0.486087] PM: Writing back config space on device 0000:00:05.0 at offset 1 (was 100000, writing 100004)
[    0.486097] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    0.486112] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[    0.486146] PM: Writing back config space on device 0000:00:13.0 at offset 3 (was 804008, writing 804010)
[    0.509198] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[    0.549337] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    0.549466] PM: Writing back config space on device 0000:00:14.1 at offset 3 (was 0, writing 4000)
[    0.549490] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    0.551214] PM: Writing back config space on device 0000:00:14.5 at offset 1 (was 4300017, writing 4300013)
[    0.551235] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 16
[    0.552257] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/atiixp.c:526: atiixp: codec reset timeout
[    0.554230] PM: Writing back config space on device 0000:00:14.6 at offset 1 (was 4300017, writing 4300013)
[    0.554250] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[    0.554906] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.554978] [fglrx] firegl_gps_setpowerup .
[    0.555055] PM: Writing back config space on device 0000:06:02.0 at offset 1 (was 6, writing 2)
[    0.555103] PM: Writing back config space on device 0000:06:06.0 at offset 1 (was 2900007, writing 2900003)
[    0.871066] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    0.871069] ata2.00: ACPI cmd ef/03:22:00:00:00:a0 filtered out
[    1.196222] ata2.00: configured for MWDMA2
[    1.330136] sd 0:0:0:0: [sda] Starting disk
[    2.962738] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    2.962741] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    2.970878] ata1.00: configured for UDMA/100
[    2.976459] sd 0:0:0:0: [sda] 156368016 512-byte hardware sectors (80060 MB)
[    2.976472] sd 0:0:0:0: [sda] Write Protect is off
[    2.976474] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.976491] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.976568] PM: Finishing wakeup.
[    2.976570] Restarting tasks ... done.
[    4.156419] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[    4.214868] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[    4.246952] b43-phy0: Broadcom 4318 WLAN found
[    4.316164] phy0: Selected rate control algorithm 'simple'
[    4.893098] 8139too Fast Ethernet driver 0.9.28
[    4.893179] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 19
[    4.896197] eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:bd:e2:eb, IRQ 19
[    4.896201] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.993809] input: b43-phy0 as /devices/virtual/input/input10
[    5.869166] Registered led device: b43-phy0:radio
[    5.917562] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.946567] eth0: link down
[    5.947716] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.118532] eth0: link down
[    6.119603] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.151432] input: b43-phy0 as /devices/virtual/input/input11
[    7.354543] Registered led device: b43-phy0:radio
[    7.403106] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.165096] wlan0: Initial auth_alg=0
[   35.165110] wlan0: authenticate with AP 00:19:5b:7a:4d:21
[   35.166725] wlan0: RX authentication from 00:19:5b:7a:4d:21 (alg=0 transaction=2 status=0)
[   35.166732] wlan0: authenticated
[   35.166737] wlan0: associate with AP 00:19:5b:7a:4d:21
[   35.169637] wlan0: RX AssocResp from 00:19:5b:7a:4d:21 (capab=0x431 status=0 aid=1)
[   35.169643] wlan0: associated
[   35.169651] wlan0: switched to short barker preamble (BSSID=00:19:5b:7a:4d:21)
[   35.171883] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.525684] wlan0: no IPv6 routers present
[ 1179.539431] atieventsd[6571]: segfault at 00000001 eip b7e6acc1 esp bfc36df0 error 4
[ 2412.948226] wlan0: deauthenticate(reason=3)
[ 2413.465836] ACPI: PCI interrupt for device 0000:06:06.0 disabled
[ 2413.544491] input: b43-phy0 as /devices/virtual/input/input12
[ 2414.700402] Registered led device: b43-phy0:radio
[ 2414.748853] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2414.968402] ACPI: PCI interrupt for device 0000:06:02.0 disabled
[ 2416.816508] Syncing filesystems ... done.
[ 2416.816798] PM: Preparing system for mem sleep
[ 2416.817395] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2416.818524] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
[ 2416.914483] PM: Entering mem sleep
[ 2416.914486] Suspending console(s)
[ 2416.914517] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2417.158158] sd 0:0:0:0: [sda] Stopping disk
[ 2418.208688] ACPI handle has no context!
[ 2418.208801] [fglrx] firegl_gps_setpowerdown .
[ 2418.227305] ACPI: PCI interrupt for device 0000:01:05.0 disabled
[ 2418.227462] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[ 2418.227732] ACPI: PCI interrupt for device 0000:00:14.5 disabled
[ 2418.227946] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[ 2418.228051] ACPI: PCI interrupt for device 0000:00:13.2 disabled
[ 2418.243442] ACPI: PCI interrupt for device 0000:00:13.1 disabled
[ 2418.243496] ACPI: PCI interrupt for device 0000:00:13.0 disabled
[ 2418.244234] Disabling non-boot CPUs ...
[    0.392304] Back to C!
[    0.486700] PM: Writing back config space on device 0000:00:01.0 at offset 9 (was 10001, writing cff1c001)
[    0.486722] PM: Writing back config space on device 0000:00:05.0 at offset 9 (was 0, writing fff0)
[    0.486726] PM: Writing back config space on device 0000:00:05.0 at offset 8 (was 0, writing fff0)
[    0.486729] PM: Writing back config space on device 0000:00:05.0 at offset 7 (was 101, writing 1f1)
[    0.486733] PM: Writing back config space on device 0000:00:05.0 at offset 6 (was 0, writing 30200)
[    0.486738] PM: Writing back config space on device 0000:00:05.0 at offset 1 (was 100000, writing 100004)
[    0.486748] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    0.486762] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[    0.486797] PM: Writing back config space on device 0000:00:13.0 at offset 3 (was 804008, writing 804010)
[    0.509385] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[    0.549523] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    0.549652] PM: Writing back config space on device 0000:00:14.1 at offset 3 (was 0, writing 4000)
[    0.549677] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    0.551387] PM: Writing back config space on device 0000:00:14.5 at offset 1 (was 4300017, writing 4300013)
[    0.551408] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 16
[    0.552431] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/atiixp.c:526: atiixp: codec reset timeout
[    0.554404] PM: Writing back config space on device 0000:00:14.6 at offset 1 (was 4300017, writing 4300013)
[    0.554424] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 16
[    0.555079] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.555150] [fglrx] firegl_gps_setpowerup .
[    0.555228] PM: Writing back config space on device 0000:06:02.0 at offset 1 (was 6, writing 2)
[    0.555276] PM: Writing back config space on device 0000:06:06.0 at offset 1 (was 2900007, writing 2900003)
[    0.871253] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    0.871256] ata2.00: ACPI cmd ef/03:22:00:00:00:a0 filtered out
[    1.180350] ata2.00: configured for MWDMA2
[    1.326210] sd 0:0:0:0: [sda] Starting disk
[    2.906720] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    2.906722] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    2.914863] ata1.00: configured for UDMA/100
[    2.919561] sd 0:0:0:0: [sda] 156368016 512-byte hardware sectors (80060 MB)
[    2.919574] sd 0:0:0:0: [sda] Write Protect is off
[    2.919577] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.919594] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.919672] PM: Finishing wakeup.
[    2.919674] Restarting tasks ... done.
[    3.587519] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[    3.644971] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[    3.681063] b43-phy0: Broadcom 4318 WLAN found
[    3.766209] phy0: Selected rate control algorithm 'simple'
[    3.790025] 8139too Fast Ethernet driver 0.9.28
[    3.790104] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 19
[    3.791641] eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:bd:e2:eb, IRQ 19
[    3.791643] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.866052] input: b43-phy0 as /devices/virtual/input/input13
[    5.509775] Registered led device: b43-phy0:radio
[    5.558266] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.587266] eth0: link down
[    5.588393] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.759217] eth0: link down
[    5.760300] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.792131] input: b43-phy0 as /devices/virtual/input/input14
[    6.991214] Registered led device: b43-phy0:radio
[    7.039695] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3071.768802] usb 3-1: new high speed USB device using ehci_hcd and address 2
[ 3071.903702] usb 3-1: configuration #1 chosen from 1 choice
[ 3072.142825] usbcore: registered new interface driver libusual
[ 3072.230822] Initializing USB Mass Storage driver...
[ 3072.234091] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3072.237350] usbcore: registered new interface driver usb-storage
[ 3072.237363] USB Mass Storage support registered.
[ 3072.239625] usb-storage: device found at 2
[ 3072.239631] usb-storage: waiting for device to settle before scanning
[ 3077.262934] usb-storage: device scan complete
[ 3077.264178] scsi 2:0:0:0: Direct-Access     TOSHIBA  MK4025GAS        1A   PQ: 0 ANSI: 2 CCS
[ 3077.278659] sd 2:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[ 3077.279460] sd 2:0:0:0: [sdb] Write Protect is off
[ 3077.279467] sd 2:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 3077.279472] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3077.280721] sd 2:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[ 3077.281510] sd 2:0:0:0: [sdb] Write Protect is off
[ 3077.281516] sd 2:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 3077.281521] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3077.281529]  sdb:<6>usb 3-1: reset high speed USB device using ehci_hcd and address 2
[ 1388.009074] usb 3-1: reset high speed USB device using ehci_hcd and address 2
[ 3185.411718] usb 3-1: reset high speed USB device using ehci_hcd and address 2
[ 3185.524273] usb 3-1: device descriptor read/64, error -71
[ 3185.741313] usb 3-1: device descriptor read/64, error -71
[ 3185.958330] usb 3-1: reset high speed USB device using ehci_hcd and address 2
[ 3186.070871] usb 3-1: device descriptor read/64, error -71
[ 3186.287913] usb 3-1: device descriptor read/64, error -71
[ 3186.505036] usb 3-1: reset high speed USB device using ehci_hcd and address 2
[ 3186.914866] usb 3-1: device not accepting address 2, error -71
[ 3187.027500] usb 3-1: reset high speed USB device using ehci_hcd and address 2
[ 3187.437323] usb 3-1: device not accepting address 2, error -71
[ 3187.437417] usb 3-1: USB disconnect, address 2
[ 3187.437670] sd 2:0:0:0: Device offlined - not ready after error recovery
[ 3187.437684] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3187.437694] end_request: I/O error, dev sdb, sector 0
[ 3187.437701] Buffer I/O error on device sdb, logical block 0
[ 3187.438255] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438263] Buffer I/O error on device sdb, logical block 0
[ 3187.438291] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438297] Buffer I/O error on device sdb, logical block 0
[ 3187.438316] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438322] Buffer I/O error on device sdb, logical block 0
[ 3187.438339] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438345] Buffer I/O error on device sdb, logical block 0
[ 3187.438355] ldm_validate_partition_table(): Disk read failed.
[ 3187.438368] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438374] Buffer I/O error on device sdb, logical block 0
[ 3187.438390] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438396] Buffer I/O error on device sdb, logical block 0
[ 3187.438412] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438418] Buffer I/O error on device sdb, logical block 0
[ 3187.438434] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438440] Buffer I/O error on device sdb, logical block 0
[ 3187.438451] Dev sdb: unable to read RDB block 0
[ 3187.438463] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438468] Buffer I/O error on device sdb, logical block 0
[ 3187.438485] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438507] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438524] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438541] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438559] sd 2:0:0:0: rejecting I/O to offline device
[ 3187.438568]  unable to read partition table
[ 3187.438651] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 3187.438727] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 3187.553856] usb 3-1: new high speed USB device using ehci_hcd and address 3
[ 3187.666419] usb 3-1: device descriptor read/64, error -71
[ 3187.883450] usb 3-1: device descriptor read/64, error -71
[ 3188.100478] usb 3-1: new high speed USB device using ehci_hcd and address 4
[ 3188.213014] usb 3-1: device descriptor read/64, error -71
[ 3188.430061] usb 3-1: device descriptor read/64, error -71
[ 3188.647083] usb 3-1: new high speed USB device using ehci_hcd and address 5
[ 3189.056995] usb 3-1: device not accepting address 5, error -71
[ 3189.169544] usb 3-1: new high speed USB device using ehci_hcd and address 6
[ 3189.579510] usb 3-1: device not accepting address 6, error -71
[ 3301.626499] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 3301.632180] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3301.634466] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3301.636566] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3301.638145] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3301.638151] psmouse.c: issuing reconnect request
[ 3306.866683] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 3306.868554] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3306.878570] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 3307.115947] usb 3-4: new high speed USB device using ehci_hcd and address 7
[ 3307.250841] usb 3-4: configuration #1 chosen from 1 choice
[ 3307.268393] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3307.276976] usb-storage: device found at 7
[ 3307.276988] usb-storage: waiting for device to settle before scanning
[ 1473.202775] usb-storage: device scan complete
[ 1473.203503] scsi 3:0:0:0: Direct-Access     TOSHIBA  MK4025GAS        1A   PQ: 0 ANSI: 2 CCS
[ 1473.205369] sd 3:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[ 1473.211054] sd 3:0:0:0: [sdb] Write Protect is off
[ 1473.211061] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 1473.211064] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1473.212143] sd 3:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[ 1473.212904] sd 3:0:0:0: [sdb] Write Protect is off
[ 1473.212907] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 1473.212909] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1473.212913]  sdb:<6>usb 3-4: reset high speed USB device using ehci_hcd and address 7
[ 3370.861864] usb 3-4: reset high speed USB device using ehci_hcd and address 7
[ 1522.281384] usb 3-4: reset high speed USB device using ehci_hcd and address 7
[ 1522.393784] usb 3-4: device descriptor read/64, error -71
[ 1522.614594] usb 3-4: device descriptor read/64, error -71
[ 1522.831402] usb 3-4: reset high speed USB device using ehci_hcd and address 7
[ 1522.943811] usb 3-4: device descriptor read/64, error -71
[ 1523.160606] usb 3-4: device descriptor read/64, error -71
[ 1523.377403] usb 3-4: reset high speed USB device using ehci_hcd and address 7
[ 1523.786939] usb 3-4: device not accepting address 7, error -71
[ 1523.899349] usb 3-4: reset high speed USB device using ehci_hcd and address 7
[ 3432.775693] usb 3-4: device not accepting address 7, error -71
[ 3432.776165] usb 3-4: USB disconnect, address 7
[ 3432.776427] sd 3:0:0:0: Device offlined - not ready after error recovery
[ 3432.776443] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3432.776452] end_request: I/O error, dev sdb, sector 0
[ 3432.776458] printk: 5 messages suppressed.
[ 3432.776464] Buffer I/O error on device sdb, logical block 0
[ 3432.777001] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777009] Buffer I/O error on device sdb, logical block 0
[ 3432.777035] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777041] Buffer I/O error on device sdb, logical block 0
[ 3432.777057] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777063] Buffer I/O error on device sdb, logical block 0
[ 3432.777079] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777084] Buffer I/O error on device sdb, logical block 0
[ 3432.777094] ldm_validate_partition_table(): Disk read failed.
[ 3432.777108] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777113] Buffer I/O error on device sdb, logical block 0
[ 3432.777128] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777134] Buffer I/O error on device sdb, logical block 0
[ 3432.777149] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777155] Buffer I/O error on device sdb, logical block 0
[ 3432.777170] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777176] Buffer I/O error on device sdb, logical block 0
[ 3432.777185] Dev sdb: unable to read RDB block 0
[ 3432.777196] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777202] Buffer I/O error on device sdb, logical block 0
[ 3432.777216] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777238] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777255] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777270] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777286] sd 3:0:0:0: rejecting I/O to offline device
[ 3432.777295]  unable to read partition table
[ 3432.777377] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 3432.777458] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 3432.896253] usb 3-4: new high speed USB device using ehci_hcd and address 8
[ 3433.008850] usb 3-4: device descriptor read/64, error -71
[ 3433.225822] usb 3-4: device descriptor read/64, error -71
[ 3433.442855] usb 3-4: new high speed USB device using ehci_hcd and address 9
[ 3433.555391] usb 3-4: device descriptor read/64, error -71
[ 3433.772447] usb 3-4: device descriptor read/64, error -71
[ 3433.989463] usb 3-4: new high speed USB device using ehci_hcd and address 10
[ 3434.399386] usb 3-4: device not accepting address 10, error -71
[ 3434.511910] usb 3-4: new high speed USB device using ehci_hcd and address 11
[ 3434.921845] usb 3-4: device not accepting address 11, error -71
[ 3493.347504] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 3493.348796] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3493.359683] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 3498.090674] usb 3-1: new high speed USB device using ehci_hcd and address 12
[ 3498.225554] usb 3-1: configuration #1 chosen from 1 choice
[ 3498.274085] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3498.283582] usb-storage: device found at 12
[ 3498.283593] usb-storage: waiting for device to settle before scanning
[ 3503.307379] usb-storage: device scan complete
[ 3503.308618] scsi 4:0:0:0: Direct-Access     TOSHIBA  MK4025GAS        1A   PQ: 0 ANSI: 2 CCS
[ 3503.323157] sd 4:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[ 3503.323914] sd 4:0:0:0: [sdb] Write Protect is off
[ 3503.323921] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 3503.323926] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3503.325037] sd 4:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[ 3503.325796] sd 4:0:0:0: [sdb] Write Protect is off
[ 3503.325802] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 3503.325806] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3503.325814]  sdb:<6>usb 3-1: reset high speed USB device using ehci_hcd and address 12
[ 3554.836763] usb 3-1: reset high speed USB device using ehci_hcd and address 12
[ 3582.096456] usb 3-1: USB disconnect, address 12
[ 3582.097238] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097247] end_request: I/O error, dev sdb, sector 0
[ 3582.097254] printk: 5 messages suppressed.
[ 3582.097260] Buffer I/O error on device sdb, logical block 0
[ 3582.097351] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097359] end_request: I/O error, dev sdb, sector 0
[ 3582.097364] Buffer I/O error on device sdb, logical block 0
[ 3582.097405] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097412] end_request: I/O error, dev sdb, sector 0
[ 3582.097417] Buffer I/O error on device sdb, logical block 0
[ 3582.097468] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097475] end_request: I/O error, dev sdb, sector 0
[ 3582.097480] Buffer I/O error on device sdb, logical block 0
[ 3582.097526] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097533] end_request: I/O error, dev sdb, sector 0
[ 3582.097538] Buffer I/O error on device sdb, logical block 0
[ 3582.097552] ldm_validate_partition_table(): Disk read failed.
[ 3582.097589] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097597] end_request: I/O error, dev sdb, sector 0
[ 3582.097602] Buffer I/O error on device sdb, logical block 0
[ 3582.097646] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097654] end_request: I/O error, dev sdb, sector 0
[ 3582.097658] Buffer I/O error on device sdb, logical block 0
[ 3582.097704] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097711] end_request: I/O error, dev sdb, sector 0
[ 3582.097716] Buffer I/O error on device sdb, logical block 0
[ 3582.097761] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097769] end_request: I/O error, dev sdb, sector 0
[ 3582.097774] Buffer I/O error on device sdb, logical block 0
[ 3582.097787] Dev sdb: unable to read RDB block 0
[ 3582.097823] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097830] end_request: I/O error, dev sdb, sector 0
[ 3582.097835] Buffer I/O error on device sdb, logical block 0
[ 3582.097879] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097886] end_request: I/O error, dev sdb, sector 0
[ 3582.097936] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097944] end_request: I/O error, dev sdb, sector 24
[ 3582.097987] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.097994] end_request: I/O error, dev sdb, sector 24
[ 3582.098023] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.098030] end_request: I/O error, dev sdb, sector 0
[ 3582.098073] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3582.098081] end_request: I/O error, dev sdb, sector 0
[ 3582.098092]  unable to read partition table
[ 3582.098176] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 3582.098257] sd 4:0:0:0: Attached scsi generic sg2 type 0

---

### Post by Rocket2DMn on 2008-07-04
OK, it would seem that the partition is corrupted.  We can try using ntfsfix, but its capacities are limited.
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```
Of course, make sure the drive is plugged in to run that second command.  It may not even recognize sdb1.

Your best bet is to plug it into a windows machine and see if you can fix the problem there, otherwise you will probably need to reformat the drive.  Before that time comes, you should try another converter.

---

