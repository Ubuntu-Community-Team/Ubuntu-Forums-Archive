---
title: "Cant install on VIGLEN MPC-l, kernel panic"
date: 2008-10-22
forum: General Help
---

### Post by ChrisBean on 2008-10-22
Hi all,

I've got a Viglen MPC-L computer which was running Ubuntu 8.04.  I have had to put in a new hard drive, and now I cannot install a new copy of Ubuntu, without getting a Kernel Panic during the install.

Does anyone here have any experience with the MPC-L? or know what I can do?

Thanks

---

### Post by IckySplat on 2008-10-23
You need to pass a couple of parameters to the kernel to get it to boot ... The magic incantation is...

pnpbios=off noacpi acpi=off

If you're trying a fresh install you will need to pass these values to the linux kernel when booting from the cdrom/dvd; Look at the various options on the install media boot menu, one will allow you to add extra boot options.

You will also need to add these setting to the grub menu.lst
edit the /boot/grub/menu.lst
find these lines...
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5

add the following line
# defoptions=quiet splash pnpbios=off noacpi acpi=off

then run 
# update-grub

Good luck

---

### Post by ChrisBean on 2008-10-23
Hi IckySplat,
I am booting via usb, and typing the 'magic incarnation' seems to be working.  Thank you so much for your help.  I've just had to abort the install as my TV upstairs decided it wouldn;t support the video resolution.  Nevertheless, I am a step closer to getting it installed.

Cheers

---

