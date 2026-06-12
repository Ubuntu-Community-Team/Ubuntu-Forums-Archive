---
title: "Acer Aspire 1690 notebook problem"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by rida on 2005-08-15
Hi everyone!
my name is Andrea and I'm a newbie user of linux...
I want to change definitely to Linux from Windows...

 ](*,) So my problem is:

I have an [Acer Aspire 1690 notebook](http://global.acer.com/products/notebook/as1690.htm) and when I tried to install the Kubuntu Linux at the end of installation (after the reboot) the system alert me that there is an
PnPBIOS problem
and when I have to see the Kdm login, I don't see nothing...

I was thinking that was a problem of my card video but the xorg.conf it's correct...

Who knows the solution?!?! :?

thanks in advance...

---

### Post by eyck on 2005-09-14
HI,
I think the problem is that certain sort of notebooks have special hardware that is not recognised by the kernel.
The question is how the notebook boots ?
Do you have a multiboot system ?
I have a acer 1692 and I use Suse Linux 9.3 and Windows XP. When the system boots, the grub loader allows select what OS do you want and also edit the boot parameters to disable. The config file of grub is locate /boot/grub/menu.lst.
This file is plain text and you can edit it and insert for example:

title linuxsample
kernel (hd0,3) /vmlinuz ide=nodma apm=off acpi=off vga=normal
initrd (hd0,3) /initrd 

How this works ?
The title appears when the system boots, if you select this entry the system tries to boot the partition 4 of the first hard disk, the kernel locate on /vmlinuz with the options disable dma, disable power management (apm), disable acpi, and vga normal. Then execute the pseudoautoexec initrd, this depends of the distribution you use. I think the most difficult distribution to manage is debian. It's more simply suse or mandrake, but you have to have special attention to the fact that a notebook isn't a PC. 
If you have the chance to install the distribution on a PC, do you have more probabilities of sucess.

Regards

---

### Post by chatuser on 2005-11-23
- edit /boot/grub/menu.lst
- change acpi=off to noapic
- reboot your computer

Everything works now, damn ACPI !!

---

