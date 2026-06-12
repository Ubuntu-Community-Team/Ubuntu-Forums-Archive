---
title: "Can not install on Alienware m7700 (Clevo 900)"
date: 2011-04-10
forum: Hardware
---

### Post by fekauffman on 2011-04-10
The one deviation from the stock m7000 system is that this machine has a dual-core processor. I have found old references in the forum to this laptop that seemed to indicate that people had no trouble getting past the boot.

When attempting to install any version of Ubuntu (or even from from the CD), during boot up, the machine just powers off. The last item shown on screen is:

kernel thread helper

This laptop will install/run any version of Windows without issue (other than usual Windows trouble).

Anyone have any recent experience with this particular hardware or this situation?

---

### Post by fekauffman on 2011-04-10
Was able to get around this by going into the boot options and enabling the acpi=off switch using the F6 options (press escape while booting).

The next hurdle seems to be a graphical issue. I just have a page of snow right now when booting the installer. :)

The last text I saw on screen seemed to be about configuring sound.

---

### Post by fekauffman on 2011-04-16
Did some digging, gave up on digging, and just went back and tried it.

The ACPI off (or ACPI workarounds) bit is mandatory. I do not know why I was getting the snowcrash, but that was not persistent.

Turning of ACPI via the grub bootloader is here:

[http://ubuntuforums.org/showthread.php?t=935461](http://ubuntuforums.org/showthread.php?t=935461)

---

