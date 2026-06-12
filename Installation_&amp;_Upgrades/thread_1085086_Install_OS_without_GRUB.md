---
title: "Install OS without GRUB"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by xiontinsu on 2009-03-02
Right now I'm running the Win7 beta, and while I love it, it has some funny things, like not being able to repair/reinstall its boot loader from the iso. I want to triple with kubuntu 7/vista/kubu, but I don't want GRUB to install when I install ubuntu to the partition. I'd rather just enter it manually into the Win7 boot loader... Any ideas?

---

### Post by Rallg on 2009-03-02
Consider booting via a USB device. Of course, the device would have to be attached and selected at boot time.

For example, if you have an empty USB stick, make it bootable (I suggest finding the HP boot device utility, which runs on Windows), and put some kind of DOS on it. Then, use grub4dos (which you can download from its site). In the menu.lst on the USB, you can edit so that it will boot to the Ubuntu on your hard drive.

Keep in mind that on the USB, grub4dos will think it is hd0 and your hard drive is hd1.

If you want to do it that way, then when you install Ubuntu on your hard drive, after going through the partitioner you will come to a screen that summarizes what you want to do. Choose the "Advanced" tab, and install grub on the same ext3 (or ext2, whatever) partition as your Ubuntu system, NOT on (hd0,0) which would otherwise be the default.

There are other ways to do it, but since you seem to be in a transition mode, the above is relatively painless and can be undone later. Just remember to use that "Advanced" tab, and pick the correct place to put grub! Do this the right way, and you never touch Windows or the hard drive MBR.

---

