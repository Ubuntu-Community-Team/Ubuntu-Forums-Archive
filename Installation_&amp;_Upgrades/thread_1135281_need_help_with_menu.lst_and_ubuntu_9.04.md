---
title: "need help with menu.lst and ubuntu 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by ac3raven on 2009-04-24
So I did a noobish thing and decided to keep the 8.10 menu.lst on my system, thinking that would be a good idea, because I dual-boot, but as soon as I rebooted after the upgrade (not fresh install), I realized how stupid that was.  I get error 15.

So, where can I find a generic menu.lst to copy and paste, so I can boot into 9.04 again?

---

### Post by jimmyboy09 on 2009-04-24
I have the same exact problem, and I don't know how to remedy the situation since the farthest I get is grub bootloader.  (From there, I "boot" into intrepid, and freeze at a blank screen).

Any help for me as well would be appreciated.

Thanks.

---

### Post by ac3raven on 2009-04-24
I found this in someone elses post:

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,0)
kernel      /boot/vmlinuz-2.6.28-11-generic root=/dev/md0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

That works to boot into ubuntu, but the root=/dev/md0 doesn't apply to my system, so when I booted in, I was taken to a shell.  I removed that part, and the same thing happened because it couldn't find the root.

---

### Post by ac3raven on 2009-04-24
also, putting your uuid into the menu.lst entry help.  to find that, type

```
uuid
```

in grub console

---

