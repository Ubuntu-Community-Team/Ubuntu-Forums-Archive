---
title: "end_request: I/O error, dev sr0, sector 0"
date: 2009-08-25
forum: Hardware
---

### Post by rwittke on 2009-08-25
[SIZE=1]I freshly installed Ubuntu 9.04 from alternative cd image. (REASON: EXT4 and cryptsetup LUKS)

Since installation Im not longer able to write images to cd or read written cds.[/SIZE][SIZE=1] :-([/SIZE]
[SIZE=1] I was searching thru forum sites, but all time answer was check scsi cable or change cd writer.

Attached a log extract what I got in syslog when inserting a disc.

Aug 25 14:15:19 <hostname> kernel: [90706.183166] end_request: I/O error, dev sr0, sector 0
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.183180] Buffer I/O error on device sr0, logical block 0
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.183189] Buffer I/O error on device sr0, logical block 1
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.183201] Buffer I/O error on device sr0, logical block 2
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.183208] Buffer I/O error on device sr0, logical block 3
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.183215] Buffer I/O error on device sr0, logical block 4
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.183222] Buffer I/O error on device sr0, logical block 5
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.183229] Buffer I/O error on device sr0, logical block 6
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.183236] Buffer I/O error on device sr0, logical block 7
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.211531] end_request: I/O error, dev sr0, sector 0
Aug 25 14:15:19 [/SIZE][SIZE=1]<hostname>[/SIZE][SIZE=1] kernel: [90706.211543] Buffer I/O error on device sr0, logical block 0

Before installation writer was working very well. Attached some information about my system:
Release 5.0, Gnome 2.26.1 (Ubuntu 2009-05-06), Kernel 2.6.28-15-generic (#49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009), GCC 4.3.3 (i486-linux-gnu), lenovo ThinkPad R61 (8943-DMG)

Now some details about cd writer:

sudo sdparm /dev/sr0
    /dev/sr0: MATSHITA  DVD-RAM UJ-860    RB01  [cd/dvd]
Read write error recovery mode page:
  AWRE        1  [cha: y, def:  1, sav:  1]
  ARRE        0  [cha: y, def:  0, sav:  0]
  PER         0  [cha: y, def:  0, sav:  0]
Write parameters (MMC) mode page:
  BUFE        1  [cha: y, def:  1, sav:  1]
  WR_T        0  [cha: y, def:  0, sav:  0]
  MULTI_S     0  [cha: y, def:  0, sav:  0]
Informational exceptions control mode page:
  EWASC       0  [cha: y, def:  0, sav:  0]
  DEXCPT      1  [cha: y, def:  1, sav:  1]
  MRIE        0  [cha: y, def:  0, sav:  0]

sudo hdparm /dev/sr0

/dev/sr0:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

less /etc/fstab | grep scd0
/dev/scd0       /media/cdrom0   iso9660 user,udf,noauto,exec,utf8 0       0

ls -la /dev/..
brw-rw----+ 1 root cdrom 11, 0 2009-08-24 13:03 /dev/sr0
lrwxrwxrwx 1 root root 3 2009-08-24 13:03 /dev/scd0 -> sr0
lrwxrwxrwx 1 root root 3 2009-08-24 13:03 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2009-08-24 13:03 /dev/cdrw -> sr0


sudo lshw
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-860
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RB01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

sudo lsscsi -v
[0:0:0:0]    disk    ATA      HITACHI HTS54161 SB4I  /dev/sda dir: /sys/bus/scsi/devices/0:0:0:0  [/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0]
[3:0:0:0]    cd/dvd  MATSHITA DVD-RAM UJ-860   RB01  /dev/sr0 dir: /sys/bus/scsi/devices/3:0:0:0  [/sys/devices/pci0000:00/0000:00:1f.1/host3/target3:0:0/3:0:0:0]

udi = '/org/freedesktop/Hal/devices/storage_model_DVD_RAM_UJ_860'
  access_control.file = '/dev/sr0'  (string)
  access_control.type = 'cdrom'  (string)
  block.device = '/dev/sr0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_DVD_RAM_UJ_860'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom', 'access_control'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host_scsi_device_lun0'  (string)
  info.product = 'DVD-RAM UJ-860'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_DVD_RAM_UJ_860'  (string)
  info.vendor = 'MATSHITA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host3/target3:0:0/3:0:0:0/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrdl = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 4234  (0x108a)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 4234  (0x108a)  (int)
  storage.cdrom.write_speeds = {'4234', '2822', '2117', '1411'} (string list)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = 'RB01'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'DVD-RAM UJ-860'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = ''  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 372013056  (0x162c7800)  (uint64)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'MATSHITA'  (string)


[/SIZE]

---

### Post by rwittke on 2009-08-25
**When I run Ubuntu 8.04 from Live USB Stick (Created with unetbootin) cd is properly working.**

---

