---
title: "Stuck on last step in fixing DSDT"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by Ryanson on 2007-05-20
Hello all.

I am on a toshiba satellite laptop, and I'm having a few problems getting the DSDT fixed. I'm following these instructions:

*Upgrade your BIOS to version 3.30.
*Download the custom DSDT file for the P100-343 (3.30) from [http://acpi.sourceforge.net/](http://acpi.sourceforge.net/) (via the view menu).
*Backup your "/boot/initrd.img-xxx" and "/boot/vmlinuz-xxx" files (Only for safety).
*Do a "sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml" (Is case sensitive!).
*Do a "sudo dpkg-reconfigure linux-image-$(uname -r)".
*Reboot.


But I am stuck on "*Do a "sudo dpkg-reconfigure linux-image-$(uname -r)".".

I can't seem to figure out exactly what to put in to make it work. Sorry if this seems dumb, but I've not had much experiance with this sort of thing. Any help would be greatly appreciated.

Thanks, 
   -Ryan

---

### Post by xenoph0be on 2007-05-20
> **Ryanson said:**
> 

But I am stuck on "*Do a "sudo dpkg-reconfigure linux-image-$(uname -r)".".



Paste that command into a terminal window and it should work as it is. 
> 

user@computer:~$ echo linux-image-$(uname -r)
linux-image-2.6.20-15-generic


Jacob

---

### Post by Ryanson on 2007-05-21
Ha, well now I really feel dumb...But oh well, it works now.

Thank you so much sir, you've made my night.

---

### Post by xenoph0be on 2007-05-21
> **Ryanson said:**
> Ha, well now I really feel dumb...But oh well, it works now.

Thank you so much sir, you've made my night.

Not a problem at all...  Glad that I could help.

Jacob

---

### Post by snafu_az on 2007-05-23
I have also followed the steps but DSDT.aml doesn't appear to load at boot.  I'm still getting the message ....

[    0.000000] ACPI: Vendor "PTLTD " System "  DSDT  " Revision 0x6040000 has a 
known ACPI BIOS problem.
[    0.000000] ACPI: Reason: Multiple problems. This is a non-recoverable error
[    0.000000] ACPI: Disabling ACPI support

This is the same DSDT.aml file I have been using for over a year in SUSE 10.0.  I copied it to /etc/initramfs-tools/DSDT.aml and then ran sudo dpkg-reconfigure linux-image-$(uname -r) , which didn't give any errors.  When I reboot and select linux-image-2.6.20-15-generic it still tries to load the BIOS DSDT instead of my file.

I even recompiled dsdt.dsl with iasl to create a new DSDT.aml and it still doesn't load.

Is the a boot switch I need to add to grub ? like acpi=?

Thanks

---

### Post by snafu_az on 2007-05-29
I appended acpi=force to the vmlinuz line of /boot/grub/menu.lst and it loaded from my recompiled DSDT.aml.

Snafu_az

---

