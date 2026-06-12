---
title: "usb mouse and iPod dont't work without restarting"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by tseo on 2008-03-15
Hello

I have an USB mouse and an iPod Nano. I saw lots of threads about the iPod but I doubt I should use the fstab file for the mouse.

When I just plug any of these they don't work, iPod is not even charging. When I reboot everything works. What can I do? Please be advised that I am not very technically aware.

Thanks

---

### Post by tseo on 2008-03-18
It seems that all usb devices don't work until rebooting.

Here are 'dmesg | tail' and 'mount' before and after reboot:
Usb devices currently connected are iPod Nano, Kingston stick and USB mouse.

mount after:
```
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hda on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=ivan)
/dev/sdb2 on /media/NANONANO type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sdc1 on /media/KINGSTON type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev)
```

dmesg after:```

[   84.692000] Bluetooth: RFCOMM TTY layer initialized
[   84.692000] Bluetooth: RFCOMM ver 1.8
[   89.048000] NET: Registered protocol family 17
[   94.324000] UDF-fs: No VRS found
[   94.352000] ISO 9660 Extensions: Microsoft Joliet Level 1
[   94.380000] ISOFS: changing to secondary root
[  109.000000] Clocksource tsc unstable (delta = -249978450 ns)
[  129.520000] kjournald starting.  Commit interval 5 seconds
[  129.520000] EXT3 FS on sda3, internal journal
[  129.520000] EXT3-fs: mounted filesystem with ordered data mode.
```

mount before:
```
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hda on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=ivan)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev)

```

dmesg before:

```
ivan@ivan-laptop:~$ dmesg | tail
[  181.656000] [<f88856a0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  181.656000] Disabling IRQ #7
[  183.000000] Clocksource tsc unstable (delta = -249984346 ns)
[  483.344000] kjournald starting.  Commit interval 5 seconds
[  483.344000] EXT3 FS on sda3, internal journal
[  483.344000] EXT3-fs: mounted filesystem with ordered data mode.
[ 6769.288000] usbcore: registered new interface driver libusual
[ 6769.292000] Initializing USB Mass Storage driver...
[ 6769.292000] usbcore: registered new interface driver usb-storage
[ 6769.292000] USB Mass Storage support registered.
```

---

