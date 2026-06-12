---
title: "Live CD does not boot"
date: 2010-10-13
forum: Hardware
---

### Post by rpher on 2010-10-13
I have created Live CDs for Ubuntu 10.10 64 bit, 10.10 32 bit and 10.4 32 bit. 
The 32 bit versions boot correctly on my desktop machine, so I am pretty sure the CDs are ok, but all of them crash during boot on my laptop.
The last messages output when using the 64 bit version are:
? kernel_init +0x0/0x1bd
? kernel_thread_helper +0x0/0x10

The other versions are practically identical (the numbers are different).

The laptop is a new Toshiba Satellite L630-130 with 4GB ram, Intel Core i3-350M Processor and Intel HM55 Express Chipset with Intel Graphics Media Accelerator HD.

I tried removing one of the memory modules, leaving it with 2GB, but that made no difference.

There are no other options with the machine, and presumably the live CD does does not use the hdd, so has no interest in what is installed on it, so I do not see what can be wrong.

I have searched the forums for similar problems with no result.

Have other people booted Ubuntu on a Toshiba Satellite L630-130, or is there some known incompatibility with this hardware?

---

### Post by davidmohammed on 2010-10-13
when you say it "crashes" - is this before or after you see the options such as "try without installing"?

If its after, maybe you need to change one or more of the boot options such as "noapic"

---

### Post by rpher on 2010-10-13
I boot from the CD.  I see an introductory message for a fraction of a second then nothing till it stops completely with a screenful of messages ending with those I mentioned initially.

I see no options.

Presumably the  kernel initialisation fails catastrophically.

---

### Post by mvillet on 2010-10-19
I also have a Toshiba L630 and encountered the same problem with Ubuntu 10.10; apparently it is some kind of conflict between the BIOS and ACPI. To fix this issue, I am currently using this patch:
[https://patchwork.kernel.org/patch/217842/](https://patchwork.kernel.org/patch/217842/)

Step-by-step: when booting off the live CD, hit F6 as the CD is loading to access the installation menu, then F6 again for boot options. Hit ESC to get out of the boot option dialog box, and after the ` -- ' in the now-visible boot text add 'acpi=copy_dsdt' ; the live CD will now boot and you can install Ubuntu as normal.

After installation, you need to change the boot manager to always boot using acpi=copy_dsdt, or you will always get the crash after starting. Follow these directions: [http://ubuntuforums.org/showthread.php?t=1323023](http://ubuntuforums.org/showthread.php?t=1323023)
but replace 'acpi=off' with 'acpi=copy_dsdt' . The first time you boot after install, you'll have to manually add the line to GRUB (enter the GRUB menu while booting, hit 'e' on the install you want to boot with, and add 'acpi=copy_dsdt' to the end of the line with 'ro   quiet splash'

I just did this installation and am still going to monitor to make sure temperatures, etc. are safe with this configuration, but so far things look OK - 40C for the hard drive, and low 50's for CPU. The system detects and uses 4 cores (I have an i5 chip but I think the i3 allows dual-threading in each of the two cores as well), battery monitor works, brightness works, and it looks like suspend upon closing the lid works properly as well!

You can follow these same steps and install Ubuntu using the 'acpi=off' option, but then ACPI is disabled, the system only uses one processor core and gets very hot - inefficient at best, dangerous for the computer at worst.

---

### Post by rpher on 2010-10-25
Many thanks for that detailed reply.
I will try it.

---

### Post by mvillet on 2010-10-25
Good luck, with this ACPI patch most things seem to be working OK now. Main issues are that the graphics card support is poor (I've left the ATI drivers off for this reason, but you've got Intel graphics and should be fine) and the headphone jack sound card output doesn't work (haven't put much time into trying to sort this one out yet though, curious to know if it's a problem for you as well).

---

