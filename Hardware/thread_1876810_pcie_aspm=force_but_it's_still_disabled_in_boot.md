---
title: "pcie_aspm=force but it's still disabled in boot?"
date: 2011-11-06
forum: Hardware
---

### Post by scottbomb on 2011-11-06
I have pcie_aspm=force in my grub, and I removed "quiet splash" so I could see what was going on during boot. Interestingly, I noticed this line:

[   1.423518] e100e0000:02:00.0: Disabling ASPM L0s L1

Isn't the grub edit mentioned above supposed to prevent that or is this something different?

This is an IBM Thinkpad T60 running Xubuntu 11.10.

---

### Post by scottbomb on 2011-11-09
I got the above msg on TTY1 after the boot. I learned to enable boot-logging and I now see this in dmesg:

[   0.000000] PCIe ASPM is forcedly enabled

Then later on...

[   0.249577] ACPI _OSC control for PCIe not granted, disabling ASPM

So apparently, either the BIOS or the kernel is not letting me force ASPM. I wonder why? From what I read in this phoronix forum, I might just be SOL:

[http://phoronix.com/forums/showthread.php?56460-The-Leading-Cause-Of-The-Recent-Linux-Kernel-Power-Problems/page4&](http://phoronix.com/forums/showthread.php?56460-The-Leading-Cause-Of-The-Recent-Linux-Kernel-Power-Problems/page4&)

My laptop is burning about 15 - 22 watts (!) even with Jupiter. Most of the time, it idles at 16 watts. I had already added i915.i915_enable_rc6=1 to my grub command line. I then proceeded to add i915.i915_enable_fbc=1 and i915.lvds_downclock=1 and now powertop reports a range of 10-16 watts with occasional spikes to 22 watts. Oh well. From everything I've read about this, there doesn't seem to be much of anything else that can be done.

---

### Post by scottbomb on 2011-11-10
I was seeing this in the boot log which seemed to be responsible for the system not allowing me to force ASPM:

ACPI _OSC control request failed (AE_NOT_FOUND), returned control mask 0x1d

I bought the computer used, about a year ago. The boot log also told me my BIOS was outdated. I went to IBM/Lenovo's website to check for a newer BIOS. Lo and behold, my BIOS was very outdated, so I updated it.

I'm no longer seeing the above-mentioned error, however, the #@$(*#@ thing still won't let me force ASPM according to this message: 

[    0.164778] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it

This is AFTER I see this line (just after the CMD_LINE is invoked):

[    0.000000] PCIe ASPM is forcedly enabled

NOTE: I've seen that message every time. However, later in the log, this one always appears:

[    1.269089] e1000e 0000:02:00.0: Disabling ASPM L0s L1

So no matter what I do, the kernel (or is it the BIOS??) refuses to turn on ASPM.

---

### Post by scottbomb on 2011-11-11
Red Hat may have found the answer. I hope the Ubuntu devs are testing it:

[https://lkml.org/lkml/2011/11/10/467](https://lkml.org/lkml/2011/11/10/467)

---

### Post by scottbomb on 2011-11-12
Researching further (as I learn to poke around the Linux OS) I took a look here:

cat /sys/module/pcie_aspm/parameters/policy

When running on A/C, is returns:
[default] performance powersave

When running on battery:
default performance [powersave]

Therefore, I do believe the line pcie_apsm=force IS actually working. Perhaps the motherboard just toggles it off only when using the network device, hence:

[    1.242802] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
...
[    1.242855] e1000e 0000:02:00.0: Disabling ASPM L0s L1

To summarize, my theory is that ASPM is actually forced on for everything EXCEPT the networking hardware. Does anyone know if this is correct?

---

