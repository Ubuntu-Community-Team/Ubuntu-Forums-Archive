---
title: "AMD/Intel switchable graphics pavilion dv6 vgaswitcheroo not to be found 14.04"
date: 2014-10-23
forum: Hardware
---

### Post by youzava on 2014-10-23
I have a pavilion dv6 notebook with switchable graphics (AMD/Intel).
 Product number is A6P31EA#ABD. 

I have searched in total (not lying) 6 workdays trying to find an agreeable solution. 

I want to use the radeon open source driver but not with rpm but with oldschool vgaswitcheroo instead. 

I tried installing fglrx and had very bad performance while playing dota 2 with it and in general I don't like it. When I tried to install a recent beta fglrx, I get the no adapter detected error. I tried different builds, the download and compile yourself method for example. I edited the x.conf to get my graphics card recognized but to no avail. 

ANYWAY, I would much rather use open source. Vgaswitcheroo does not work. When I search for it in config, y is the answer but no solution I found as of yet made it possible for me to use vgaswitcheroo. So does anyone know how to compile a kernel with vgaswitcheroo so I can use the easy oldschool method? debugfs is mounted

I tried radeon.runpm=0, modeset=1, stopping lightdm but always "No such file or directory"

ACPI_call gives me an error and I don't know how to run the test.sh script. I can't find it in usr/bin.

My fan is making me crazy. 

Thanks in advance.

EDIT: I tried various methods to set my power profile to low, but none of the options worked. "No such file or directory" I will try specifically again and report the outcomes. I read something about vbios functionality. However, I got sidetracked and am now exploring options of flashing my bios to donovans version. Am trying to confirm which of his versions I need.

EDIT2: realized that donovans edits are made primarily for flashing with windows and I got a little scared Maybe I'll create 2 bootable partitions on my usb stick. 1 for flashing and 1 for recovery should I brick

EDIT3: switched switchable graphics to dynamic mode in bios. Still no vgaswitcheroo or rpm e.g. cat /sys/kernel/debug/vgaswitcheroo/switch -> no such file or directory.

If there is no answer can you tell me so?

---

### Post by youzava on 2014-10-23
After I switched to dynamic mode I tried xrandr --listproviders. Now only the Intel card is shown. Does this mean that ACPI CALL is now working?

---

