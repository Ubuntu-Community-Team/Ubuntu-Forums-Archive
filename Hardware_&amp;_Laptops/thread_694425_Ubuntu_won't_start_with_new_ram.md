---
title: "Ubuntu won't start with new ram"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by anthony.canucks on 2008-02-12
I recently purchased 2 new sticks of ram for my laptop. Since then windows XP boots fine but Ubuntu won't start. I can select it at the GRUB screen but it just says starting up and doesn't do anything.

I tried sticking the old ram back in and it's fine but I need to figure out how to get the new ram to work.

---

### Post by erginemr on 2008-02-12
As you may also know, there is an item for a "memory test" in the Grub menu. Did you try checking your memory with this tool?

---

### Post by bigken on 2008-02-12
you might need to tweak the voltage in the bios most ram runs at 1.8v but some need to be set at 2.1v

what type of ram have you bought ?

---

### Post by anthony.canucks on 2008-02-12
I ram memtest and it was fine.

The computer boots with either stick of ram but not both together.

[http://www.ncix.com/products/index.php?sku=23832&vpn=RM12864AC667&manufacture=CRUCIAL%20TECHNOLOGY](http://www.ncix.com/products/index.php?sku=23832&vpn=RM12864AC667&manufacture=CRUCIAL%20TECHNOLOGY)

thats the ram I bought.


edit:
It freezes up at "Setting up standard PCI resources"

It does boot correctly with ACPI off

---

### Post by Fechter on 2008-02-12
And what is the other stick of yours? If we have the 2 stick details we can solve it. Have you tried to overclock? Have you set the needed voltage for both sticks? Hve you set the proper frequiency?

---

### Post by erginemr on 2008-02-12
Setting "acpi=off" is not the best thing to do, because it means shutting down an entire range of functionalities related to acpi. Could you please try:
```
acpi_irq_balance
```
and also
```
pci=noacpi
```
after the following community manual:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Using "acpi_irq_balance" has also been the remedy of another Ubuntu user somewhere within the forums.

EDIT: If either one works, check if the suspend & software shut-down functionalities of your computer are still working...

---

### Post by anthony.canucks on 2008-02-12
it's two sticks of the same type.

The bios doesn't let me change those settings, but everything seems stable in memtest and windows.

I'll try the other options as soon as I'm finished my homework.

I realize that booting with ACPI off isn't great. I was just saying that it works for some reason.

---

### Post by bigken on 2008-02-12
remove both chips and try the new one in both slots

---

### Post by anthony.canucks on 2008-02-12
already tried.

there is 2 new chips (both the same kind, crucial rendition).

both work if I use one at a time (in either slot).

won't work if I use them both together.

---

### Post by anthony.canucks on 2008-02-12
none of the options work and now my desktop settings are messed up as well.

---

### Post by erginemr on 2008-02-12
> **anthony.canucks said:**
> none of the options work and now my desktop settings are messed up as well.

Messed?? What do you mean with that? These changes on ACPI, I believe, are made temporarily via Grub boot menu and should wash away on a new reboot...

EDIT: Can you please try one more thing: 
Try to boot your computer with the Ubuntu Live CD, and if possible, the Live CD of another Linux distro. This way, we can perhaps narrow down the possibilities.

---

### Post by erginemr on 2008-02-12
FYI, the following thread poster has also a similar problem, with unfortunately no remedy so far:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=691755](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=691755)

And another one:
[http://ubuntuforums.org/archive/index.php/t-257012.html](http://ubuntuforums.org/archive/index.php/t-257012.html)

---

### Post by erginemr on 2008-02-12
I think I have found it. With reference to the following thread:
[http://ubuntuforums.org/showthread.php?t=574494&highlight=maximum+memory+ram+kernel](http://ubuntuforums.org/showthread.php?t=574494&highlight=maximum+memory+ram+kernel)

Ubuntu 32 bit kernel is said to support 3 GB **[Correction: 2 GB]** maximum memory, and for more, one has to use Ubuntu 64 bit.

The link you gave for the RAM was for a 1 MB module (so 1+1=2 GB), but if you have installed more than 2 GB, then we might be looking at the right direction.

---

### Post by anthony.canucks on 2008-02-12
I have 2GB of ram.

I'm not sure why the desktop started to mess up, it's fine now.

---

### Post by erginemr on 2008-02-12
So does that mean that your problem has been solved? If so, which boot config option did you use? To make it permanent, you need to edit your "/boot/grub/menu.lst" file and add that option to the corresponding line.

---

### Post by anthony.canucks on 2008-02-13
no, the problem is still happening. The desktop is just working properly again.

I can still boot with ACPI off but I would like to figure out how to enable it.

None of the previous options worked.

---

