---
title: "How Can I Enable My Card Reader In Ubuntu?"
date: 2008-11-01
forum: Hardware
---

### Post by taurusx5 on 2008-11-01
I can't enable my card reader in ubuntu. The following is output of: fdisk -l and cat /etc/mtab. Please let me know what to do to enable my built-in card reader. Thanks!


[B]sudo fdisk -l
[sudo] password for x: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d764d75

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9327 74919096 83 Linux
/dev/sda2 9328 9729 3229065 5 Extended
/dev/sda5 9328 9729 3229033+ 82 Linux swap / Solaris

x@xx:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/scd0 /media/cdrom0 udf ro,nosuid,nodev,user=x 0 0[/B]


.

---

### Post by PmDematagoda on 2008-11-01
After you plug in the card reader, post the output of:-
```
dmesg | tail -25
```

---

### Post by taurusx5 on 2008-11-01
> **PmDematagoda said:**
> After you plug in the card reader, post the output of:-
```
dmesg | tail -25
```

Hi, PmDematagoda. Thank you for replying, I appreciate this a million times. Here's the output of what you had requested:

[B]x@xx:~$ dmesg | tail -25
[   32.964648] cs: IO port probe 0xa00-0xaff: clean.
[   33.095244] intel8x0_measure_ac97_clock: measured 55465 usecs
[   33.095248] intel8x0: clocking to 48000
[   33.858189] lp: driver loaded but no devices found
[   34.485703] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   35.513411] EXT3 FS on sda1, internal journal
[   40.864352] ppdev: user-space parallel port driver
[   42.130032] audit(1225557439.071:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4898 profile="/usr/sbin/cupsd" namespace="default"
[   45.471464] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   45.471469] vboxdrv: Successfully done.
[   45.471472] vboxdrv: Found 1 processor cores.
[   45.471476] vboxdrv: fAsync=0 u64DiffCores=1.
[   45.471536] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   45.471540] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
[   51.168179] [drm] Initialized drm 1.1.0 20060810
[   51.173626] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 18
[   51.173636] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   51.173738] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   51.173749] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   51.173806] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   75.137267] UDF-fs: Partition marked readonly; forcing readonly mount
[   75.201885] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'SCARFACE', timestamp 2003/08/06 20:07 (1f10)
[   75.366086] NET: Registered protocol family 17
[  273.826599] tifm0 : demand removing card from socket 0:3
[  285.377359] tifm_core: MMC/SD card detected in socket 0:3
[/B]

.

---

### Post by PmDematagoda on 2008-11-02
Well, your card reader is being detected according to this:-
```
[ 273.826599] tifm0 : demand removing card from socket 0:3
[ 285.377359] tifm_core: MMC/SD card detected in socket 0:3
```
however it seems a little strange. What kind of computer or setup are you using Ubuntu on?

---

### Post by taurusx5 on 2008-11-02
> **PmDematagoda said:**
> Well, your card reader is being detected according to this:-
```
[ 273.826599] tifm0 : demand removing card from socket 0:3
[ 285.377359] tifm_core: MMC/SD card detected in socket 0:3
```
however it seems a little strange. What kind of computer or setup are you using Ubuntu on?

Hi there... I'm using ubuntu on a Gateway. Before installing ubuntu 8 months ago, I had XP on it and the card reader worked. I don't understand why ubuntu isn't reading my card.

.

---

### Post by tony_wh on 2008-12-19
Hello all

I'm a n00b around here.  I'm now running Ubuntu 8.10 in a sony VAIO TX2 (after a calamitous crash with windows).

Last week my SD card was working - now it's not!

Like previous posts, my dmesg shows that the card insertion is being detected by the kernel (tifm_core: MMC/SD card detected in socket 0:3
) but it's not appearing when I try fdisk -l.

I've tried including titm_sd in /etc/modules (didn't work).

Any clues?

Thanks

---

### Post by kdrpic on 2008-12-19
Hi all,

I am new to this 

I have the same problem that i have been reading about for some time but cant seem to find a fix.

If I can do anything to help this problem be resolved please let me know.

Gateway M275 
Ubuntu 8.04 - the Hardy Heron

---

