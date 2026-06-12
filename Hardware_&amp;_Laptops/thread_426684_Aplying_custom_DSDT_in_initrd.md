---
title: "Aplying custom DSDT in initrd"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by HugoPalma on 2007-04-28
Hi all,

i'm using feisty and i'm trying to apply a custm dsdt using the method described here [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml).

So, i've got the DSDT.aml file and i copied it to the root / dir. From what i understand that should do it, right ?
As you can guess, it doesn't.
The result of the command "dmesg | grep "Looking for DSDT in initramfs" is :

[   17.481824] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

Any ideas of what i'm missing ?

Thanks.

---

### Post by HugoPalma on 2007-04-28
I think the problem is that i have to create a file of initramfs type with the DSDT.aml in it.

I'm trying to use mkinitramfs but i can't figure out how to add my DSDT.aml to it. Again, any help would be great.

---

### Post by teppic on 2007-05-01
Copy DSDT.aml to /etc/initramfs-tools and then run "sudo update-initramfs -u -k `uname -r`" to update the image. Reboot and dmesg should show something like:

[   24.163146] ACPI: Looking for DSDT in initramfs... successfully read 22788 by
tes from /DSDT.aml.
[   24.163210] ACPI (tbget-0297): Table [DSDT] replaced by host OS [20060707]

---

### Post by HugoPalma on 2007-05-02
> **teppic said:**
> Copy DSDT.aml to /etc/initramfs-tools and then run "sudo update-initramfs -u -k `uname -r`" to update the image. Reboot and dmesg should show something like:

[   24.163146] ACPI: Looking for DSDT in initramfs... successfully read 22788 by
tes from /DSDT.aml.
[   24.163210] ACPI (tbget-0297): Table [DSDT] replaced by host OS [20060707]

Thanks, that worked great.....

---

### Post by octesian on 2008-01-05
Thank you!  After days of upgrading, downgrading, compiling and screaming all at dial-up speeds, my sound finally works!

---

