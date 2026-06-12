---
title: "Why will PCLinuxOS boot and not Ubuntu?"
date: 2009-09-06
forum: Hardware
---

### Post by MartyBuntu on 2009-09-06
So, I have a Toshiba Satellite A30 with the latest BIOS update.
My main workstation and my wife's laptop (Dell Inspiron 5150) run Jaunty, so I thought I get this one going as well.

I have tried these distros and they all freeze during the boot sequence **unless** the "acpi=off" boot parameter is passed:

1. Ubuntu 8.10
2. Ubuntu 9.04
3. Mint 7
4. Fedora 11


These distros *will* boot without passing extra parameters at boot time (default):

1. Puppy Linux
2. PCLinuxOS

Some Googling has turned me on to information that this particular laptop doesn't play well with ACPI and Linux. But why does PCLinuxOS work, with full power saving features and battery monitoring may I add? 

PCLinux is okay, I've actually used it quite a bit 2-3 years ago, but I'd rather have Jaunty running, or at least Mint.


Lastly, if I do decide to boot and install with **acpi=off**, are there any features I will be missing, or possible problems down the road?

Thanks.

---

### Post by wojox on 2009-09-06
It shouldn't. This is from the boot options help file:

> This parameter disables the whole ACPI system. This may prove very useful, for example, if your computer does not support ACPI or if you think the ACPI implementation might cause some problems (for instance random reboots or system lockups).

---

### Post by MartyBuntu on 2009-09-06
Thanks. I'll try a Jaunty install tomorrow probably. We'll see how it goes.

---

