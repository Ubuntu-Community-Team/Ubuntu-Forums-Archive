---
title: "Thumb Drive Boot Ultimate BootCD with Grub2?"
date: 2009-11-19
forum: Hardware
---

### Post by paulisdead on 2009-11-19
Not really sure if this is the right place for this, or not.  Anyways, I'm trying to make an Uber thumb drive that multiboots 32/64bit ubuntu/debian/gentoo, ultimate bootcd, and eventuall ophcrack.  Gentoo's a whole other problem, but I've got it multibooting ubuntu and debian, and haven't tried ophcrack yet.  What can I say, even though I haven't run gentoo in like 3 years, I still love their livecds that have no GUI, but lots of nice tools and tons of drivers on their CDs.

I know UBCD uses syslinux, but am unsure what's really what on their CD, since they've renamed a few things.  Not sure if maybe I need to try to chainload syslinux.  Here's the grub.cfg I tried last
```
menuentry "Ubuntu Live 9.10 32bit" {
 loopback loop /boot/iso/ubuntu-9.10-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-9.10-desktop-i386.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}
 
menuentry "Ubuntu Live 9.10 64bit" {
 loopback loop /boot/iso/ubuntu-9.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-9.10-desktop-amd64.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}

menuentry "Ultimate Boot CD memdisk" {
 loopback loop /boot/iso/ubcd411-1.iso
 linux (loop)/boot/baslinux
 initrd (loop)/boot/baslinux.gz
}

menuentry "Gentoo 32bit" {
 loopback loop (hd0,0)/boot/iso/install-x86-minimal-20091103.iso
 linux (loop)/isolinux/gentoo root=/dev/ram0 root=/dev/ram0 init=/linuxrc  dokeymap looptype=squashfs loop=/image.squashfs cdroot cdboot initrd=gentoo.igz vga=791 --
 initrd (loop)/isolinux/gentoo.igz
}
menuentry "Gentoo 64bit" {
 loopback loop (hd0,0)/boot/iso/install-amd64-minimal-20091112.iso
 linux (loop)/isolinux/gentoo root=/dev/ram0 init=/linuxrc  dokeymap looptype=squashfs loop=/image.squashfs cdroot cdboot initrd=gentoo.igz vga=791 --
 initrd (loop)/isolinux/gentoo.igz
}


menuentry "debian installer amd64 netboot" {
  linux /boot/debian/linux auto=true priority=critical vga=normal --
  initrd /boot/debian/initrd.gz
}
```

I have tried syslinux and unetbootin for this.  I could get each one to bootup individually, but not multiboot.  For syslinux/unetbootin, I was following this guide [http://ubuntuforums.org/showpost.php?p=6659180&postcount=5](http://ubuntuforums.org/showpost.php?p=6659180&postcount=5).

I suppose that it's entirely possible that I could just bypass the UBCD menu system, and use grub2 to boot each of the floppy images from it.  This seems like a really cluttered menu.  It might be a solution if somebody knows of a way to create sub-menus, though.

---

### Post by paulisdead on 2009-11-20
OK, so I grabbed RC1 for ultimate bootcd 5.0, and it looks like it has support for loading everything from grub4dos now.  Is there a way I could chain load grub4dos from grub2?  It would certainly be easier to chainload their menu system than create my own.

---

### Post by DaveQB on 2012-03-13
How did you go with this? I am VERY interested in this.

Thanks.

---

### Post by sbandeira on 2012-10-13
I did it using grub2 (not grub4dos), memdisk and a lot of tries:

menuentry "UBCD 5.11" {
   linux16 /boot/iso/memdisk iso
   initrd16 /boot/iso/ubcd511.iso
}


adjust the directory where memdisk and ubcd iso are.
I've got memdisk binary from [http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.04.zip](http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.04.zip)

Hope that helps.
--
Silvio

---

### Post by overdrank on 2012-10-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

