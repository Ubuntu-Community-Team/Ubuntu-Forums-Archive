---
title: "Locks installing dapper on Acer Travelmate 529ATXV"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by jrh on 2006-06-19
Hi,

I'm trying to install Dapper on my old Acer Travelmate 529ATXV and the install CD freezes when booting in the "Mounting root filesystem" step . I also tried Xubuntu with the same results, hard lock on booting :-(

Anyone has tried to install ubuntu on this machine? any success?

I'm also confused as which package should I fill a bug against in launchpad ... does anyone know?

thanks.

---

### Post by 5-HT on 2006-06-19
You'll need to add 'pci=noacpi' to the kernel boot options.

During install, pressing either F5 or F6 (the menu will say) will bring up the install options. Simply add 'pci=noacpi' to the end of those options (before the '--').

If you've manage to install but can't boot, press 'Esc' when GRUB is loding and add 'pci=noacpi' to the boot options. You will then need to edit /boot/grub/menu.lst to append 'pci=noacpi' to the boot options so it'll use it everytime.

Here are some suggested changes you can make to menu.lst:

1. Append 'pci=noacpi' to ```
# kopt=root=/dev/hda1 ro 
``` 
The end result will be this ```
# kopt=root=/dev/hda1 ro pci=noacpi 
``` If you make this change, menu.lst will  be automatically updated everytime you upgrade your kernel to include that boot option. :)

2. Append 'pci=noacpi' to your main kernel (the # kopt= line will only take effect after a kernel upgrade).
This is what a kernel entry (yours may be different) may look like before the changes

```
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet 
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot 
``` 
This is what it'll look like after adding 'pci=noacpi'

```
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet acpi=noacpi
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot 
``` 

The problem seems to be due to an IRQ conflict and Acer's buggy ACPI.
You could file a bug report,  but I believe it is Acer's fault and not that of Ubuntu - so the report may not be looked at. 
If you make the changes I suggested, you should have no problems booting.

Hope that helps; post back if you have any problems.

---

