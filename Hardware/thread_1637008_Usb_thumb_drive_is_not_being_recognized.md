---
title: "Usb thumb drive is not being recognized"
date: 2010-12-03
forum: Hardware
---

### Post by legacymaker on 2010-12-03
so here is the problem:
my usb thumb drive that had worked on my current install of 10.04 now does not work. here are all the read outs:
~$ lsusb
Bus 002 Device 003: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
~$ dmesg | tail
[ 5047.975946] usb 1-2: configuration #1 chosen from 1 choice
[ 5647.849285] usb 1-2: USB disconnect, address 8
[ 5651.380051] usb 1-2: new high speed USB device using ehci_hcd and address 9
[ 5652.315869] usb 1-2: configuration #1 chosen from 1 choice
[ 6732.129288] usb 1-2: USB disconnect, address 9
[ 6751.260052] usb 1-1: new high speed USB device using ehci_hcd and address 10
[ 6752.215943] usb 1-1: configuration #1 chosen from 1 choice
[ 7340.295178] usb 1-1: USB disconnect, address 10
[ 7355.890058] usb 1-2: new high speed USB device using ehci_hcd and address 11
[ 7356.852150] usb 1-2: configuration #1 chosen from 1 choice
~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pat/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pat)
gvfs-fuse-daemon on /home/family/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=family)
gvfs-fuse-daemon on /home/don/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=don)
/dev/sdb1 on /media/BAA89E63A89E1DC7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
~$ dmesg | tail -50
[   11.305667]  (Note that use of the override may cause unknown side effects.)
[   11.305688] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   11.324829] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   11.564084] Console: switching to colour frame buffer device 80x30
[   11.743343] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   11.743352] nvidia 0000:05:00.0: setting latency timer to 64
[   11.744422] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.22  Wed Nov 11 05:08:25 PST 2009
[   11.793728] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[   11.794965] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   11.795557] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   11.795563]   alloc irq_desc for 16 on node 0
[   11.795565]   alloc kstat_irqs on node 0
[   11.795574] ndiswrapper 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   11.807697] ndiswrapper: using IRQ 16
[   12.159187] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   12.159194] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[   12.159227] Intel ICH 0000:00:04.0: setting latency timer to 64
[   12.170733] wlan0: ethernet device 00:24:8c:24:c3:51 using NDIS driver: bcmwl5, version: 0x364400a, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   12.170764] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   12.171244] usbcore: registered new interface driver ndiswrapper
[   12.186107] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.490056] intel8x0_measure_ac97_clock: measured 50651 usecs (2488 samples)
[   12.490060] intel8x0: clocking to 46905
[   70.530370] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   70.990785] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   73.140033] Clocksource tsc unstable (delta = -179950735 ns)
[   81.570033] wlan0: no IPv6 routers present
[ 4716.360048] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 4717.315966] usb 1-2: configuration #1 chosen from 1 choice
[ 4855.880229] usb 1-2: USB disconnect, address 4
[ 4858.910068] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 4859.886257] usb 1-1: configuration #1 chosen from 1 choice
[ 4872.931368] usb 1-1: USB disconnect, address 5
[ 4879.910054] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 4880.865189] usb 1-1: configuration #1 chosen from 1 choice
[ 4918.798583] usb 1-1: USB disconnect, address 6
[ 4934.550045] usb 1-6: new high speed USB device using ehci_hcd and address 7
[ 4935.446066] usb 1-6: configuration #1 chosen from 1 choice
[ 5042.060094] usb 1-6: USB disconnect, address 7
[ 5047.020051] usb 1-2: new high speed USB device using ehci_hcd and address 8
[ 5047.975946] usb 1-2: configuration #1 chosen from 1 choice
[ 5647.849285] usb 1-2: USB disconnect, address 8
[ 5651.380051] usb 1-2: new high speed USB device using ehci_hcd and address 9
[ 5652.315869] usb 1-2: configuration #1 chosen from 1 choice
[ 6732.129288] usb 1-2: USB disconnect, address 9
[ 6751.260052] usb 1-1: new high speed USB device using ehci_hcd and address 10
[ 6752.215943] usb 1-1: configuration #1 chosen from 1 choice
[ 7340.295178] usb 1-1: USB disconnect, address 10
[ 7355.890058] usb 1-2: new high speed USB device using ehci_hcd and address 11
[ 7356.852150] usb 1-2: configuration #1 chosen from 1 choice

I am not sure exactly what to do, all my permissions are on. 
please help.

---

### Post by tommcd on 2010-12-03
> **legacymaker said:**
> so here is the problem:
my usb thumb drive that had worked on my current install of 10.04 now does not work. 
So you are still using 10.04, and you did not do a dist-upgrade, is that correct?
Also, from the info you posted:
> **legacymaker said:**
> 
~$ lsusb
Bus 001 Device 011: ID 054c:0243 Sony Corp. MicroVault Flash Drive

~$ mount
/dev/sdb1 on /media/BAA89E63A89E1DC7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

Is that the flash drive? What is mounted on /media/BAA89E63A89E1DC7 ?
What file system is on the flash drive?

---

### Post by legacymaker on 2010-12-03
yes 10.10 was not installing properly, and 10.04 works pretty good.

> ~$ lsusb
Bus 001 Device 011: ID 054c:0243 Sony Corp. MicroVault Flash Driveyes that is the drive. I want to say it is a NTFS I know that when I first loaded ubuntu it was being read and mounted now I can't seem to find it.

---

### Post by tommcd on 2010-12-05
> **legacymaker said:**
> 
yes that is the drive. I want to say it is a NTFS I know that when I first loaded ubuntu it was being read and mounted now I can't seem to find it.
So, as I asked in my last post, What exactly is mounted on */media/BAA89E63A89E1DC7* ? 
(Note: The exact mount point *BAA89E63A89E1DC7* may change each time you insert the flash drive to a usb port.

To find out the file system on the flash drive, simply plug in the flash drive, then post the output of:
```
sudo fdisk -l
```
This will list all the partitions and their filesystem types that Ubuntu sees.
Flash drives are usually FAT16 or FAT32, unless you have reformatted them to NTFS.

---

