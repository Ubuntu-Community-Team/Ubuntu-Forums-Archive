---
title: "installation on msi 6390 v3 problem"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by jgw on 2009-06-03
I have been trying to install ubuntu on a new system.  I am using an msi 6390 v3 motherboard.  it has a built in prosavage8 video controller.  I had a 9.04 version, on a hard disk, so I tried that first.  The boot failed.  I then tried to reinstall with, first, a 9.04 cd, then an 8.10 cd, and, finally, an 8.04 cd.  The 9.04 and 8.10 cds threw "ubuntu" on the screen and then froze.  The 8.04 cd got as far as the installation screen.  Once the install button was pushed the screen went blank with a small white blinking cursor in the upper left hand side of the screen.  This is a mystery.  Oh, I have also removed the hard drive and re-formatted it just for the heck of it although I suspect it makes no difference.

I suspect the graphics controller but am not sure.  

Anybody have any thoughts?

---

### Post by dstew on 2009-06-03
There are a number of possibilities. Do you know that the Ubuntu CDs are good? Have you booted them on other computers? Did you do the disk integrity check (menu item)?

If the disks are good, then you might have an incompatibility between the Live CD Linux kernel and your hardware. It could be the graphics controller, but often is is other motherboard systems, such as the APIC (advanced programmable interrupt controller) or the ACPI (advanced configuration and power interface). If you think you are having this kind of trouble, you have several options. You can try to boot the Linux kernel using parameters that turn off the modules for this hardware. You add these to the end of the kernel line, accessed by I think F6 at the opening menu. To turn of the interrupt controller, use **noapic** and **nolapic**. To turn off the ACPI, use **acpi=off**. There are other kernel parameters, but these are commonly tried. Here's an [old thread]("http://ubuntuforums.org/archive/index.php/t-148761.html") that talks about it.

The other option is to try to install using the [Alternate Install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). It installs the same Ubuntu desktop system, but uses a text-based installer that works with a wider variety of motherboards.

---

### Post by jgw on 2009-06-03
Thank you for the reply.  

The cd's should be fine as I have used them before.  There is an option (f6), on the install screen, to disable acpi.  I will try that one again.  I have also just replaced my memory - just in case.  

I will make a run with the alternate installer.  I should also mention that this motherboard has a hewlett packard bios.  I am tempted to re-flash with an msi bios but fear I can REALLY screw things up.

I should also mention that when I try and check the cd the machine does exactly the same thing.  blanks the screen, inserts a small white on the upper left hand and simply hangs (the cd is never accessed)

Thanks again........

---

