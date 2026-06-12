---
title: "usb camera mouting ?"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by Beire on 2005-03-08
I'm trying to manually mount my canon powershot a70 here.
When i plug it in libgphoto detects the camera and show the pictures in thumbnails. But that's not what i want, i want to mount it manually.

So i tried mount /dev/sda1

There's only 1 problem, i seem to have NO sda entries in /dev, problem ?

Here the kernel output when i plug in the camera:

```
Mar  8 15:10:56 localhost usb.agent[9697]:      libgphoto2: loaded successfully
Mar  8 15:16:12 localhost usb.agent[9898]:      libgphoto2: loaded successfully

```
Not much to see here huh ?

```
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
NVRM: not using NVAGP, AGPGART is loaded!!
NVRM: not using NVAGP, AGPGART is loaded!!
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8: BIOS error - no PSB
eth0: no IPv6 routers present
usb 3-2: new full speed USB device using uhci_hcd and address 2
usb 3-2: USB disconnect, address 2
usb 3-2: new full speed USB device using uhci_hcd and address 3

```

And these are the last lines of my dmesg output.

Any suggestions ?

---

### Post by rdario on 2005-03-08
[QUOTE=Beire]I'm trying to manually mount my canon powershot a70 here.
When i plug it in libgphoto detects the camera and show the pictures in thumbnails. But that's not what i want, i want to mount it manually.

So i tried mount /dev/sda1

There's only 1 problem, i seem to have NO sda entries in /dev, problem ?

Here the kernel output when i plug in the camera:

```
Mar  8 15:10:56 localhost usb.agent[9697]:      libgphoto2: loaded successfully
Mar  8 15:16:12 localhost usb.agent[9898]:      libgphoto2: loaded successfully

```
Not much to see here huh ?

```
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
NVRM: not using NVAGP, AGPGART is loaded!!
NVRM: not using NVAGP, AGPGART is loaded!!
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8: BIOS error - no PSB
eth0: no IPv6 routers present
usb 3-2: new full speed USB device using uhci_hcd and address 2
usb 3-2: USB disconnect, address 2
usb 3-2: new full speed USB device using uhci_hcd and address 3

```

And these are the last lines of my dmesg output.

Any suggestions ?[/QUOTE]
 try gtkam 
Applications ---> Graphics --> gtkam

---

### Post by Beire on 2005-03-08
[QUOTE=rdario]try gtkam 
Applications ---> Graphics --> gtkam[/QUOTE]
 i cana cces my camera, that's not the problem.
I want to mount it so i can reach it as a directory. Like my hard drives, and that is not working!

---

### Post by lordofkhemenu on 2005-03-08
[QUOTE=Beire]i cana cces my camera, that's not the problem.
I want to mount it so i can reach it as a directory. Like my hard drives, and that is not working![/QUOTE]
what's the output of 'less /etc/mtab' when your camera is connected and recognized?
Just as an example when I connect my Fuji S7000, this appears in my mtab (keep in mind, there is no entry for it -manually added or otherwise - in /etc/fstab):
 ```
/dev/sda1 /media/usbdisk vfat rw,nosuid,nodev,sync,noatime,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
``` 
gthumb automatically opens up when I connect the camera (too lazy to disable that right now)  and shows this in the path window:
 ```
/media/usbdisk/dcim//100_fuji
```
I'm thinkin' the mtab info will give you a heads up and idea where to start looking for that camera-- if it shows up there.

---

### Post by Beire on 2005-03-08
[QUOTE=lordofkhemenu]what's the output of 'less /etc/mtab' when your camera is connected and recognized?
Just as an example when I connect my Fuji S7000, this appears in my mtab (keep in mind, there is no entry for it -manually added or otherwise - in /etc/fstab):
 ```
/dev/sda1 /media/usbdisk vfat rw,nosuid,nodev,sync,noatime,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
``` 
gthumb automatically opens up when I connect the camera (too lazy to disable that right now)  and shows this in the path window:
 ```
/media/usbdisk/dcim//100_fuji
```
I'm thinkin' the mtab info will give you a heads up and idea where to start looking for that camera-- if it shows up there.[/QUOTE]
 this is my mtab output

```
/dev/hdd8 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hdd7 /boot ext3 rw 0 0
/dev/hdd1 /mnt/D ntfs rw,umask=0222 0 0
/dev/hdc1 /mnt/C ntfs rw,umask=0222 0 0
/dev/hdd5 /mnt/E ntfs rw,umask=0222 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0

```

---

