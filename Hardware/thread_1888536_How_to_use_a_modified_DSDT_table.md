---
title: "How to use a modified DSDT table?"
date: 2011-11-29
forum: Hardware
---

### Post by yeagle on 2011-11-29
Hi,

I am trying to use a modified DSDT table. The DSDT table of my BIOS contais
(like many) several errors. I disassembled the table with iasl, fixed some
of the errors and recompiled it. Now I want to use my repaired DSDT table.

As far as I know, there are two ways to do that:
1. Recompile the kernel with the new DSDT table.
2. Use initramfs to load the DSDT table (without changing the kernel).

I don't want to recompile the whole kernel, so I decided to do it as
described above in Method 2. I did the following:
I copied the new DSDT.aml file to /etc/initramfs-tools/ and ran the
command:
update-initramfs -u
which gave me the following:
```
update-initramfs: Generating /boot/initrd.img-2.6.38-12-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda2
cryptsetup: WARNING: could not determine root device from /etc/fstab
cryptsetup: WARNING: target cryptswap1 has a random key, skipped
```(I don't really know what exactly those warnings mean, but I don't
think they have anything to do with the problem. Tell me if I'm wrong ;) )

I rebooted my System and checked the kernel messages:
dmesg | grep -i dsdt
```
[    0.000000] ACPI: DSDT 3f5f2000 07881 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.183517] ACPI: EC: Look up EC in DSDT
```That doesn't look like my machine uses the new DSDT table...
I think there should be some message, telling me, that the DSDT table was
loaded from the initramfs or anything like that, but that message is
obviously missing...


Am I missing something?
What do I have to do, that my machine loads the modified DSDT table
(without recompiling the kernel)?

Oh, and I tried this on two different machines (my Notebook and my Netbook)
and it doesn't work on both of them.
They both run Ubuntu 11.04

---

### Post by yeagle on 2011-12-09
Ok, I found the solution at [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=9a9e0d685553af76cb6ae2af93cca4913e7fcd47](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commit;h=9a9e0d685553af76cb6ae2af93cca4913e7fcd47)

in short: The feature to load the DSDT from initramfs has been disabled, because the early loading of the initramfs caused other problems.

So at the moment there's no other way than recompiling the kernel with the custom DSDT file.

---

