---
title: "booting from grub gives console messages"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by chucky500 on 2009-09-15
G'day all...

Have Ubuntu v8.10, which installed some months ago.

Finally got grub going, which I invoke from Partition Magic (PM) (this is a multi-boot Windows-Linux machine).  Ubuntu is over on the second hard-drive, where the boot (grub) partition resides in an extended partition, device /dev/sdb5.  The main Ubuntu install is on a primary partition, /dev/sdb2.  Both are ext3 filesystems, although for awhile I had turned them into ext2 partitions, since I was getting the PM error #510 (choking on the ext3 attribute somehow).  I have used PM for years, although am now using gparted from the CD.  I may eventually convert from BootMagic to grub to do the booting as well on this machine.  Anyways, that's another aside.  I should be back to ext3 on both these partitions, and I have a Linux swap partition on the first harddrive.

My problem is that when I boot Ubuntu (the install at /dev/sdb2) with grub, I get a stream of error messages on the console (no windowing yet), and things come screeching to a halt with the Caps Lock and Scroll Lock lights on my keyboard flashing away.  Maybe I haven't booted correctly?  I can boot Ubuntu from the CD without any problems, except I get the BIOS pre-2000 ACPI-force message at startup.  Yes, this machine is getting along in years, but it works and is paid for.  I hate to junk stuff that seems to have life left in it, and it works fine.

I probably am not doing the boot correctly in grub.  As I recall, my grub commands (at the grub> prompt) were:

grub> find /vmlinuz
(hd1,1)     -- makes sense, first primary partition after the extended partition, 2nd hd
grub> kernel /vmlinuz root=(hd1,1)  -- not certain if this was the command, as I may
                                                         have done the root parameter differently
grub> boot

A short pause ensued, and then I got the stream of error messages.

I suspect I am not invoking the kernel correctly.  A friend of mine who set up Ubuntu on an HP laptop (vintage 2002), used somewhat different commands in his menu.lst file:

title        Linux Ubuntu 8.10 sda3-grub
uuid        0d86d470-55fb-4ac2-b5c1-efb059c988f0
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=0d86d470-55fb-4ac2-b5c1-efb059c988f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

I assume there is not a problem trying to boot by hand from the grub> prompt, although I have noted there is a warning in the grub manual grub.pdf that the prompt mode is an emulator.

Do I need to use the generic version of the vmlinuz as in the menu.lst above?  I'm clue-less as to where that UUID string came from.

Ubuntu is replacing RH Linux v8.0 in these partitions.  I don't remember having all these problems with grub and booting for RH, but it's been years (2002).

Thanks for any help!

Chuck

---

### Post by chucky500 on 2009-09-17
Anybody got any ideas as to what to do here?

---

