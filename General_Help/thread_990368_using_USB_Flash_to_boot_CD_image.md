---
title: "using USB Flash to boot CD image"
date: 2008-11-22
forum: General Help
---

### Post by MrUmunhum on 2008-11-22
Hi group,
  I need to boot the LiveCD imsgae from a USB stick.  I downloaded ubuntu-8.10-desktop-i386.iso, mounted it as a loopback, then copied it to the Flash. 
  My problem is that my laptop does not support booting from USB. So what I did was to copy the kernel and initrd files to my hard drive and boot from there, The kernel boot up but fails to mount the squashfs file system. My Grub,conf entry looks like this:[INDENT]title USB_Stick
        root (hd0,5)
        kernel /boot/ubuntu/vmlinuz ro root=LABEL=USB_Stick
        initrd /boot/ubuntu/initrd.gz
[/INDENT]I have found some posting about 'root=LABEL' not working?

So anyone have any ideas?

---

