---
title: "boot stucks for some seconds..."
date: 2010-01-15
forum: Hardware
---

### Post by stathis21 on 2010-01-15
hi,
yesterday i installed ubuntu to a fujitsu siemens laptop(amilo pi1536)...
but till now boot stucks for 10-15sec...i commented out this line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" from /etc/default/grub
and i found that boot stucks here...
ACPI: EC: non-query interrupt received, switching to interrupt mode
...
this laptop isnt mine...i installed ubuntu to my friend laptop,who is tired of windows,and he wants to try ubuntu(without dualboot)..any ideas how to fix it???

thank you!

([SIZE="2"][/SIZE]sorry for my poor english)

---

### Post by d3v1150m471c on 2010-01-15
so reverse it so that it runs the splash.

---

### Post by stathis21 on 2010-01-15
> **d3v1150m471c said:**
> so reverse it so that it runs the splash.

with or without splash...boot stucks here...
that ACPI: EC: non-query interrupt received, switching to interrupt mode means???

---

### Post by IcarusR on 2010-01-15
You could try adding these boot options, one at a time...
noacpi
acpi=off

More info on boot options 
[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options]("https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options")

Having googled this it would appear to be a bug that shows up with your model of laptop. 
So the above suggestions may not work.
[https://bugs.launchpad.net/suse/+source/acpi/+bug/100110]("https://bugs.launchpad.net/suse/+source/acpi/+bug/100110")

---

### Post by stathis21 on 2010-01-21
looking here [https://bugs.launchpad.net/suse/+source/acpi/+bug/100110](https://bugs.launchpad.net/suse/+source/acpi/+bug/100110)
i found this


> 
Upstream has decided that modifiying the DSDT is too risky in general to be something enabled in commonly shipped kernels, as it is possible to write DSDTs which damage your hardware. It is therefore unlikely we will resurect this DSDT patch for Karmic or later.

The upstream approach is to detect the bad machines and to work round the bad entries in the DSDT at DSDT execute time. In this case that might include detecting and 'adjusting' the sleeps which are faulty as we execute them. In order to achieve this we would need to ensure we have correctly identified these sleeps. At the URL below is a kernel (kernels will be there shortly) with a debug patch applied which atttempts to detect these sleeps and eliminate them (note this is specific to the sleeps for this machine):

    [http://people.canonical.com/~apw/lp100110-karmic/](http://people.canonical.com/~apw/lp100110-karmic/)

Could those of you who are affected try the kernel below and report whether it helps or not. In either case please include dmesg output from the boot with this kernel. Thanks!



any ideas on how to apply this patch???
([http://people.canonical.com/~apw/lp100110-karmic/](http://people.canonical.com/~apw/lp100110-karmic/))
(this file includes only source code i think)

---

