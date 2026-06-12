---
title: "After 9.10 beta installaion, boot alway gets into Busybox"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by zxlstoner on 2009-10-13
I are trying to install on my external hard drive through USB connection. (Win XP on insider hard drive)
Everything is Ok when installation, except that when the install CD is ejected, the computer cannot restart itself. it keeps on spawning and seems being in a deadlock loop.
 I restarted the computer myself. 
Then I boost from USB, I cannot see the Grub menu. I chose the first to get into ubuntu. But, it's stuck always into the busybox, with some error info on PCI (no parent found for the drive.....)
What should I do to fix the problem.
Thanks!
The error info picture is attached.
[IMG]http://farm3.static.flickr.com/2534/4010632500_74c99659b0_o.jpg[/IMG]

---

### Post by dstew on 2009-10-14
This usually means that the kernel modules cannot operate you hardware properly. You can try to get around this by editing the kernel line (hit 'e' at the grub menu) to change how the kernel behaves.

You don't show much of the error messages, but it looks like the PCI system cannot locate the boot disk. You can alter the kernel line by adding kernel parameters such as **all_generic_ide** or **acpi=off** or **noapic** or **nolapic** to try to get it to boot. Remember, you are using a beta version that may never have been tested on your type of machine. Here is an old [How-To about kernel parameters]("http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html").

---

