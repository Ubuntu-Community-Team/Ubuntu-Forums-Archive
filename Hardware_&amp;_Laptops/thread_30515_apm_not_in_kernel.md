---
title: "apm not in kernel?"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by Censorydep on 2005-04-29
I have apm in my /etc/modules and have removed acpi from the system.  But, apm won't run.  At the recommendation of someone on the IRC channel, I tried >sudo modprobe apm, which produced the following error:
FATAL: Error inserting apm (/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/apm.ko): No such device

I am not even sure where to go from here.  Any suggestions or troubleshooting steps would be appreciated.

Thanks

---

### Post by garyw on 2005-08-01
I'm having the same problem. I want to use apm, so I try to load the kernel module and get that same error. If I try to MAKEDEV apm_bios, I get an error that MADEDEV doesn't know how to create that device.

So, if I can't make the device and udev doesn't automatically, then I can't load the kernel module, then I can't use apm.

Does anyone have a solution to this problem?

---

### Post by az on 2005-08-01
If I set my bois to acpi, I cannot load the apm module.  If I set my bios to APM/ACPI and the acpi modules are loaded, I cannot load APM.

If I set the bios to APM/ACPI and prevent the acpi modules from loading, I can successfully load APM.

If I set my bios to APM (only), the ACPI modules are not loaded and I can just load APM.

Basically, you cannot have both APM and ACPI loaded at the same time.  Even loading ACPI and unloading it prevents subsequent APM modules loading until you reboot.  

I hope this helps.

---

### Post by garyw on 2005-08-01
Thanks for your reply. I actually found a workable solution on another ubuntu forum. A person suggested that I add the following to my grub kernel line:

acpi=off amp=on

I did that and it worked like a charm.

---

