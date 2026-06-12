---
title: "Working on fix for HDA-Intel"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by agentno4 on 2007-02-15
I have a Toshiba Satellite P105-S9312, which has the HDA-Intel chipset for audio,  that for the last 6 months I have been dealing with no sound in Ubuntu.  After a rediculous ammount of looking for answers, I may be on the verge of actually getting sound thanks to a tutorial I stumbled across - [found here]("http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems"). 

Now I followed along, and finally got my DSDT to compile with 0 errors, 1 warning.  The section titled "Incorporating the Fix into the Kernel," is where I get lost.  I am trying to use step 3 - Build-in Options for Kernel 2.6.9 and later since I am running kernel 2.6.17.11.  I found where you can include custom DSDT with "make xconfig."  This is where I'm stuck.  The tutorial then tells you to "Recompile your kernel, copy the bzImage, and modify your grub.conf to point to the new kernel." which I don't know how to do.  

Any help would be greatly appreciated.

---

### Post by renzokuken on 2007-02-15
i found this very useful.....

[http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel](http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel)

---

### Post by justo_yo on 2007-02-17
> **agentno4 said:**
> I have a Toshiba Satellite P105-S9312, which has the HDA-Intel chipset for audio,  that for the last 6 months I have been dealing with no sound in Ubuntu.  After a rediculous ammount of looking for answers, I may be on the verge of actually getting sound thanks to a tutorial I stumbled across - [found here]("http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems"). 

Now I followed along, and finally got my DSDT to compile with 0 errors, 1 warning.  The section titled "Incorporating the Fix into the Kernel," is where I get lost.  I am trying to use step 3 - Build-in Options for Kernel 2.6.9 and later since I am running kernel 2.6.17.11.  I found where you can include custom DSDT with "make xconfig."  This is where I'm stuck.  The tutorial then tells you to "Recompile your kernel, copy the bzImage, and modify your grub.conf to point to the new kernel." which I don't know how to do.  

Any help would be greatly appreciated.

I am in a similar situation with a toshiba P105-S6024 and I found some help here, since my computer is compatible with that one:
[http://www.linlap.com/tiki-index.php?page=Toshiba+Satellite+P105](http://www.linlap.com/tiki-index.php?page=Toshiba+Satellite+P105)
But I do not know how to do the simple steps with the DSDT.hex and dsdt.dsl files, any help?:confused:

---

