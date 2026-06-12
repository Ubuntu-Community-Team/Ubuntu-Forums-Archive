---
title: "USB HD: All of a sudden I cannot access it but can see it"
date: 2008-05-12
forum: Hardware
---

### Post by nine7six on 2008-05-12
I store all of my Media on a portable WD HD, it worked fine yesterday and all of a sudden today when I plug it in, the icon will pop-up on my desktop, I can access properties and it shows the correct size, etc. When I double check on the icon I get three folders, but these are links to the computers HD (twice) and the DVD-ROM. I have tried a re-boot with the HD plugged in and I get the same issues.

I'm running Ubuntu 8.04.

When I type:
```
sudo fdisk -l
```
Into a terminal window (with the USB HD connected) I get:

```

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11485    92253231   83  Linux
/dev/sda2           11486       11978     3960022+   5  Extended
/dev/sda5           11486       11978     3959991   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   c  W95 FAT32 (LBA)


```

When I type:
```

 sudo mount /dev/sdb1

```

I get:
```

mount: /dev/sdb1 already mounted or /media/My Book busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/My Book


```

Contents of etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b995613d-3977-4dff-b43a-328f26396491 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8b89cf24-5524-4b0e-957d-05f4cd10b30c none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Any help is greatly appreciated. :)

---

### Post by nine7six on 2008-05-12
sorry, here are the contents of etc/mtab

```

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/nine7six/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=nine7six 0 0
/dev/scd0 /media/New udf ro,nosuid,nodev,uhelper=hal,uid=1000 0 0
/dev/sdb1 /media/My\040Book vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```

Thanks again.

---

### Post by nine7six on 2008-05-13
Anyone know what I can look into?

---

### Post by nine7six on 2008-05-13
I took the HD into work and when I plug it into my work PC (Windows XP) it recognizes the HD no problem and allows me to play music from it, watch a video off it, etc. Hope this helps narrow the problem down.

---

### Post by nine7six on 2008-05-13
When I type
```

dmesg|grep usb
```

In a terminal window I get

```

[   25.354126] usbcore: registered new interface driver usbfs
[   25.354148] usbcore: registered new interface driver hub
[   25.354331] usbcore: registered new device driver usb
[   25.369586] usb usb1: configuration #1 chosen from 1 choice
[   25.473415] usb usb2: configuration #1 chosen from 1 choice
[   25.577284] usb usb3: configuration #1 chosen from 1 choice
[   25.681221] usb usb4: configuration #1 chosen from 1 choice
[   23.622938] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   25.792189] usb usb5: configuration #1 chosen from 1 choice
[   23.917388] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   39.015809] usb 5-2: device descriptor read/64, error -110
[   54.160159] usb 5-2: device descriptor read/64, error -110
[   54.167251] usb 5-2: new high speed USB device using ehci_hcd and address 3
[   69.207484] usb 5-2: device descriptor read/64, error -110
[   84.262360] usb 5-2: device descriptor read/64, error -110
[   84.279260] usb 5-2: new high speed USB device using ehci_hcd and address 4
[   89.296374] usb 5-2: device descriptor read/8, error -110
[   94.373821] usb 5-2: device descriptor read/8, error -110
[   94.422560] usb 5-2: new high speed USB device using ehci_hcd and address 5
[   99.439712] usb 5-2: device descriptor read/8, error -110
[  104.517137] usb 5-2: device descriptor read/8, error -110
[  104.629189] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  104.658581] usb 2-1: configuration #1 chosen from 1 choice
[  106.893711] usbcore: registered new interface driver hci_usb
[  327.169086] usb 5-7: new high speed USB device using ehci_hcd and address 7
[  338.943451] usb 5-7: new high speed USB device using ehci_hcd and address 8
[  339.130607] usb 5-7: configuration #1 chosen from 1 choice
[  339.263079] usbcore: registered new interface driver libusual
[  339.265130] usbcore: registered new interface driver hiddev
[  339.290172] input: Western Digital My Book ES as /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.1/input/input10
[  339.306995] input,hidraw0: USB HID v1.11 Device [Western Digital My Book ES] on usb-0000:00:1d.7-7
[  339.307013] usbcore: registered new interface driver usbhid
[  339.307017] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  341.416944] usbcore: registered new interface driver usb-storage
[  341.417583] usb-storage: device found at 8
[  341.417586] usb-storage: waiting for device to settle before scanning
[  340.229985] usb-storage: device scan complete
[  422.743357] usb 5-7: reset high speed USB device using ehci_hcd and address 8
[  437.794121] usb 5-7: device descriptor read/64, error -110
[  452.871721] usb 5-7: device descriptor read/64, error -110
[  455.022371] usb 5-7: reset high speed USB device using ehci_hcd and address 8
[  470.091496] usb 5-7: device descriptor read/64, error -110
[  483.130271] usb 5-7: device descriptor read/64, error -110
[  485.363437] usb 5-7: reset high speed USB device using ehci_hcd and address 8
[  488.289065] usb 5-7: device descriptor read/8, error -110
[  493.375198] usb 5-7: device descriptor read/8, error -110
[  493.453938] usb 5-7: reset high speed USB device using ehci_hcd and address 8
[  498.473555] usb 5-7: device descriptor read/8, error -110
[  503.559298] usb 5-7: device descriptor read/8, error -110
[  503.618789] usb 5-7: USB disconnect, address 8
[  503.804456] usb 5-7: new high speed USB device using ehci_hcd and address 9
[  518.860615] usb 5-7: device descriptor read/64, error -110
[  533.932714] usb 5-7: device descriptor read/64, error -110
[  533.976292] usb 5-7: new high speed USB device using ehci_hcd and address 10
[  549.036118] usb 5-7: device descriptor read/64, error -110
[  564.117820] usb 5-7: device descriptor read/64, error -110
[  564.151489] usb 5-7: new high speed USB device using ehci_hcd and address 11
[  569.171074] usb 5-7: device descriptor read/8, error -110
[  574.256525] usb 5-7: device descriptor read/8, error -110
[  574.329546] usb 5-7: new high speed USB device using ehci_hcd and address 12
[  579.349145] usb 5-7: device descriptor read/8, error -110
[  584.434657] usb 5-7: device descriptor read/8, error -110
[ 6150.682295] usb 5-1: new high speed USB device using ehci_hcd and address 13
[ 6150.869382] usb 5-1: configuration #1 chosen from 1 choice
[ 6150.884420] usb-storage: device found at 13
[ 6150.884426] usb-storage: waiting for device to settle before scanning
[ 6150.908980] input: Western Digital My Book ES as /devices/pci0000:00/0000:00:1d.7/usb5/5-1/5-1:1.1/input/input11
[ 6150.930124] input,hidraw0: USB HID v1.11 Device [Western Digital My Book ES] on usb-0000:00:1d.7-1
[ 6152.879220] usb-storage: device scan complete

```

---

### Post by nine7six on 2008-05-13
No one has any ideas?

---

### Post by dma_k on 2011-08-13
> **nine7six said:**
> No one has any ideas?

Check [superuser answer]("http://superuser.com/questions/176959/external-usb-drive-is-failing/208759#208759").

---

