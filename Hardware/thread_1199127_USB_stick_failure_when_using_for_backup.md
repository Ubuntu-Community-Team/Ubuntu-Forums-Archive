---
title: "USB stick failure when using for backup"
date: 2009-06-28
forum: Hardware
---

### Post by gdgilda on 2009-06-28
Hello,

I've been using kubuntu for a couple of years now (currently on kubuntu 8.04) and have run into a problem doing backups to a USB memory stick.  More specifically, I've been using rsync to run periodic backups to a 2GB Memorex TravelDrive stick that's consistently worked fine for me.  However, I've been wanting to move to a large capacity memory stick and keep running into what seems to be the same problem with a couple of different sticks that I've tried.  The current version is a 8GB sandisk cruzer.

The symptom is that I'm able to auto-mount the cruzer OK and start the rsync job.  About 10 minutes into the backup, rsync fails as follows:
rsync: write failed on "/media/disk/Documents/glenn/.mozilla-thunderbird/8pc78i69.Glenn/training.dat": Input/output error (5)
rsync error: error in file IO (code 11) at receiver.c(259) [receiver=2.6.9]
rsync: connection unexpectedly closed (36458 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=2.6.9]

Here's what I see in the system log that seems to be at the time that the trouble started:
Jun 28 14:13:00 louisville kernel: [ 3618.290917] usb 1-1: reset full speed USB device using ohci_hcd and address 4
Jun 28 14:13:15 louisville kernel: [ 3633.458239] usb 1-1: device descriptor read/64, error -110
Jun 28 14:13:30 louisville kernel: [ 3648.729604] usb 1-1: device descriptor read/64, error -110
Jun 28 14:13:30 louisville kernel: [ 3649.009460] usb 1-1: reset full speed USB device using ohci_hcd and address 4
Jun 28 14:13:45 louisville kernel: [ 3664.176883] usb 1-1: device descriptor read/64, error -110
Jun 28 14:14:01 louisville kernel: [ 3679.448266] usb 1-1: device descriptor read/64, error -110
Jun 28 14:14:01 louisville kernel: [ 3679.728101] usb 1-1: reset full speed USB device using ohci_hcd and address 4
Jun 28 14:14:06 louisville kernel: [ 3684.746138] usb 1-1: device descriptor read/8, error -110
Jun 28 14:14:11 louisville kernel: [ 3689.863220] usb 1-1: device descriptor read/8, error -110
Jun 28 14:14:11 louisville kernel: [ 3690.142232] usb 1-1: reset full speed USB device using ohci_hcd and address 4
Jun 28 14:14:16 louisville kernel: [ 3695.160191] usb 1-1: device descriptor read/8, error -110
Jun 28 14:14:22 louisville kernel: [ 3700.277277] usb 1-1: device descriptor read/8, error -110
Jun 28 14:14:22 louisville kernel: [ 3700.380440] usb 1-1: USB disconnect, address 4
Jun 28 14:14:22 louisville kernel: [ 3700.381171] sd 3:0:0:0: Device offlined - not ready after error recovery
Jun 28 14:14:22 louisville kernel: [ 3700.381581] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jun 28 14:14:22 louisville kernel: [ 3700.381586] end_request: I/O error, dev sdb, sector 2978784

So does anyone have any ideas why the kernel decided that it needed to reset the usb device in the middle of an rsync?

I've read the ubuntu help on USB devices and haven't found anything that seems to match my situation since the device seems to work for some time before eventually failing.  Please note that I've observed this symptom on more than one USB stick, so I'm confident it's not the stick itself.  My old trusty TravelDrive keeps on working but the limitations of having only 2GB size is a bit of a hassle :)

I've also attached a more detailed capture of the system log (which I've labelled in sections starting with ***).

Thanks!
Glenn

---

### Post by gdgilda on 2009-07-05
Hello again,

I've done a bit more digging and while I don't have a solution, I do have a bit more information that perhaps would shed more light.  If anyone has a suggestion, I'd appreciate any feedback.

First of all, I have tried inserting this memory stick into another linux system (RHEL5 based) and have been able to use it without any issues.  I notice that on this system that it is mounted as a usb2.0 high-speed device, unlike the system in which I'm having problems.

So the issue would seem to be either with my system hardware or hardy-heron.

Here is some information about my system configuration:
$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

Note:  The command listed below is issued after inserting the memory stick, which auto-mounts, and before I run the rsync which causes it to be reset and disappear.

$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 009: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 001 Device 003: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 001 Device 001: ID 0000:0000

$ lsmod | grep hci
ehci_hcd               37900  0
ohci1394               33584  0
ieee1394               93752  2 sbp2,ohci1394
ohci_hcd               26640  0
usbcore               146412  6 ehci_hcd,usblp,usb_storage,libusual,ohci_hcd

2nd note:  The usb stick when mounted actually shows up twice below, one as /media/disk type vfat and again as /media/U3 System type iso9660.  I am trying to do the rsync backup to /media/disk/Documents (Documents folder already exists).

$ mount -l
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw) []
/dev/sda5 on /media/hda5 type ext2 (rw) []
/dev/sda6 on /media/hda6 type xfs (rw) []
/dev/sda7 on /media/hda7 type xfs (rw) []
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,noatime,uhelper=hal,flush,uid=1000,utf8,shortname=lower) []
/dev/scd1 on /media/U3 System type iso9660 (ro,nosuid,nodev,noatime,uhelper=hal,uid=1000,utf8) [U3 System]

Thanks!

---

