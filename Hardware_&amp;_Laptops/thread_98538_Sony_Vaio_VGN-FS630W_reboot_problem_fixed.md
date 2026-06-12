---
title: "Sony Vaio VGN-FS630W reboot problem fixed"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by drakeoutlaw on 2005-12-03
I installed Ubuntu Breezy Badger 5.10 on a brand new Sony Vaio VGN-FS630W laptop. Along with numerous other issues one was that the machine hangs on reboot. Everything shuts down but the machine fails to reboot. The fix is to put "reboot=h" at the end of the kernel line in /boot/grub/menu.lst.

Mine now looks like this:

kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash acpi_sleep=s3_bios reboot=h
    
This should work with FS series Viao equipped with Phoenix bios.

Cheers:cool:

---

### Post by ProdyGee on 2005-12-03
Hi
I have the same problem on my toshiba satellite A10-S503.
I inserted reboot=h into my menu.lst, and now I can reboot, but after I can't boot into gnome. It stops after the backgrond appears. 
Bye

---

### Post by drakeoutlaw on 2005-12-03
Try one by one:


reboot=s
reboot=c
reboot=c,w
reboot=w,c

Also you will find more info in [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/). Thats where I found my solution.

Apparently, the OS needs to hand over control to the bios in order for the machine to do a warm or cold boot. To really understand the whole thing one has to read the kernel documentation (kernel parameters) available in the kernel-doc package.

---

