---
title: "[SOLVED] Boot hang ACPI problem ASUS A8M Laptop"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by Slade Winstone on 2008-01-05
Hi,

I'm running an Asus A8M Laptop running Gutsy 2.6.22-14-generic.

Like a lot of people, I've been struggling with boot hang or lock relating to ACPI problems and the upgrade from Feisty to the Gutsy 2.6.22-14 kernel.

I did actually manage to get a working system by specifying acpi=off at boot.   I have now found kernel boot parameters that will allow ACPI to run giving me the Fesity functionality that I have been missing. 

Instead of setting **acpi=off** to disable all ACPI (which previously was the only way of booting my A8M), I now use **nosmp noapic** which allows some ACPI functionality and a good boot :)

Add to the end of defoptions and the end of the current kernel in /boot/grub/menu.lst
**nosmp noapic**

As an aside, this looks like it could be a general problem with many ASUS bios as I've googled a couple of people reporting the same issue and there are some posts on the kernel list archives relating to this. 

I hope this helps somebody else...

Slade.

---

### Post by Slade Winstone on 2008-01-15
Hi again,

Actually this is only semi-solved... switching the ACPI on again and now I'm suffering the notorious lock/hang bug.  Sigh.... :confused: :( It looks like I'll be going back to acpi=off...

I'll try various fixes I've picked p in a couple of threads and report back if I can get ACPI working without the horror hang!

Slade.

---

