---
title: "Kernel Panic when booting with ACPI on, using a laptop computer"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Binary.Side on 2009-05-12
I am currently installing ubuntu 8.10-i386, I have verified the MD5 of both the image and the CD I've written and I am confident that my CD is not corrupted. The system I have here is a Gateway M350WVN laptop and the plan is to run ubuntu on it. As I said, I am still in the process of installing, so this is no case of "it has been working before but then I did xy and now I'm entirely doomed."

This is the output I get after I boot from CD and select to either run LiveCD or the installation:
```

crc error
Kernel panic - not syncing: VFS: Unable to mount fs on unknown-block(0,0)

```

I decided to change the boot commands for the installation, disabling ACPI, this way I was able to complete the installation and I am currently booting with these settings:
(difference to the default configuration are marked red)
```

uuid  fde0711e-b1fb-469d-baa3-c1f7c76cbac5
kernel  /boot/vmlinuz-2.6.27-7-generic root=UUID=fde0711e-b1fb-469d-baa3-c1f7c76cbac5 ro quiet splash [color="Red"]acpi=ht apm=power_off[/color]
initrd  /boot/initrd.img-2.6.27-7-generic
quiet

```

This solved the issue of kernel panic, however since this is a laptop, I would prefer to run the system with ACPI fully enabled, since this way battery management would be enabled. Furthermore I believe I could solve the issue of the Wireless-Network device not being recognized. I have already went through a good dozen of other threads, most however ended up suggesting disabling ACPI or were (in my opinion) unrelated to my problem. Is there a way to solve this issue while having ACPI enabled?
I tried this as an alternative configuration:
```

uuid  fde0711e-b1fb-469d-baa3-c1f7c76cbac5
kernel  /boot/vmlinuz-2.6.27-7-generic root=[color="Red"]/dev/sda5[/color] ro quiet splash
initrd  /boot/initrd.img-2.6.27-7-generic
quiet

```
I've basically tried everything I've got, /dev/sda, /dev/sda1, /dev/sda2 and finally /dev/sda5. Figuring I'd just randomly try everything I have.

sudo fdisk -l /dev/sda:
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d067d06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         486     3903763+  82  Linux swap / Solaris
/dev/sda2             487        4864    35166285    5  Extended
/dev/sda5             487        4864    35166253+  83  Linux

```

---

