---
title: "Boot LiveCD from USB Drive w/ GRUB as bootloader"
date: 2008-08-30
forum: General Help
---

### Post by retrovertigo on 2008-08-30
I've had nothing but trouble getting syslinux to work, maybe it has something to do with the size of my flash drive? (8GB)  Anyway, I decided to repurpose this USB drive to boot both SystemRescueCD and a few LiveCDs, among them Ubuntu 8.04.1.  I was able to get it to start booting, but it hangs before ever starting X.  The last thing that shows up on the screen is the usb stick itself being detected.  I checked /var/log/dmesg after rebooting but this information wasn't saved to the log.

Anyway, here are the relevant lines of my menu.lst file.  Is there a kernel parameter that I am leaving out, maybe?

```
title		Ubuntu Desktop 8.04.1 LiveCD (i386)
root		(hd0,5)
kernel		/casper/vmlinuz
initrd		/casper/initrd.gz
```

---

