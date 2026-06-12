---
title: "How to install 8.04 with existing Linux distro without overriding mbr"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by frojnd on 2009-05-22
Hello there.

What I wanna do is to install ubuntu 8.04. I already have openSuse 11.1 installed. But I'd like to try 8.04 LTS. I will install it on usb stick. But when it comes to point of choosing MBR (if there is any), I don't wanna to use ubuntu's mbr or bootloader but suse's.

On short, how can I achieve after installation is complete. That I'd still have suse's bootloader but with option to choose ubuntu to boot?

---

### Post by frojnd on 2009-05-22
I've installed ubuntu on /dev/sda7 
I used entire partition for /
Format it into ext3
Swap partition was already made
I clicked on advance and unthick where it says to install bootloader (I wanna use suse one)

I rebooted into suse. I've mounted /dev/sda7 to /mnt/
mount /dev/sda7 /mnt

I've enter /mnt/boot/
and do a ls: abi-2.6.24-16-generic  config-2.6.24-16-generic  initrd.img-2.6.24-16-generic  initrd.img-2.6.24-16-generic.bak  memtest86+.bin  System.map-2.6.24-16-generic  vmlinuz-2.6.24-16-generic

Those are the files that are on ubuntu partition /dev/sda7 currently mounted on /mnt/

I've also checked what's the /dev/dsk-byid/ for sda7:
lrwxrwxrwx 1 root root 10 2009-05-22 14:50 ata-TOSHIBA_MK1234GSX_27KLTKHBT-part7 -> ../../sda7



So I started to edit suse /boot/grub/menu.lst
```
## xubuntu 8.04 LTS
title Xubuntu [/boot/vmlinuz-2.6.24-16-generic]
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-16-generic root/dev/disk/by-id/ata-TOSHIBA_MK1234GSX_27KLTKHBT-part7 ro
initrd /boot/initrd.img-2.6.24-16-generic

```

I have saved this and reboot. When selecting from menu xubuntu, it start booting but at some point it sopped:
The message was smth like this: 

[13.33302022] /build/buldd/linux-2.6.24/drivers/hid/usbhid/linux-kernel:
v2.6:USB HID core driver

---

### Post by frojnd on 2009-05-22
Is this because I didn't select /boot partition for ubuntu? I also don't have /boot partition for suse...

Any suggestions would be much appreciated.

---

### Post by frojnd on 2009-05-22
SOLVED, thanx to joeDeuce from freenode :)

The entry for ubuntu in suse's /boot/grub/menu.lst looks like this now:
```
## xubuntu 8.04 LTS
#
title Xubuntu [/boot/vmlinuz-2.6.24-16-generic]
root (hd0,6)
uuid 2e08a82e-277c-4be4-a8a4-f651e032f1aa
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2e08a82e-277c-4be4-a8a4-f651e032f1aa ro
initrd /boot/initrd.img-2.6.24-16-generic

```

---

