---
title: "Boot CD for 9.10 Installed on External HD"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by MetalAZ on 2009-11-08
I have an old celeron laptop with 768MB of RAM and the internal hard drive died on me yesterday.  So, I removed it (it was causing the whole system to freeze with live CDs) and hooked up a 500GB USB external hard drive.  I installed Ubuntu 9.10 onto it, which seemed to go fine and then followed the directions (I copied and pasted to prevent error) at [http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/) to make a boot cd since my BIOS doesn't support booting off USB.

When I boot off the created boot cd I just get a grub prompt instead of a menu.  So, I tried typing the following at the prompts:

```

first:
kernel /boot/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent

then:
initrd /boot/initrd.lz

finally:
boot

```

It looked like it started to work since I started seeing text scroll down the screen, but then I started seeing stdin:0 over and over and over again.  It just keeps repeating.

Anyone know what the problem might be?

---

