---
title: "Using Kboot to boot USB stick..."
date: 2008-11-28
forum: Hardware
---

### Post by evolve08 on 2008-11-28
I'm attempting to use Kboot in order to boot Ubuntu 8.10 on a laptop -- the bios does not support booting from a USB drive by default.

The default kboot commands are not working for 8.10, it gives me the error:> mount: mounting /dev/sda2 on /mnt/tmp/<long hash> failed: No such device or address

I looked in the menu.lst and clearly the command is wrong it is:```
title		Ubuntu, kernel
kernel	/boot/linux quiet usbboot=sda2 t_root=/dev/sda2 t_ro t_quiet t_splash
initrd	/boot/ramdisk
boot
```

I looked around for a command that would boot 8.10 but this was the best I could find, and I don't think it works, though I'm gonna test it now:```
title Run Ubuntu 8.10 from USB DISK
kernel /boot/vmlinuz file=/preseed/ubuntu.seed boot=casper usbboot=sda2
initrd /boot/initrd.gz
boot
```

Does anyone have a kboot command which works, in order to boot from a USB stick?

---

