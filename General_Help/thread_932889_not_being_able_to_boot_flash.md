---
title: "not being able to boot flash"
date: 2008-09-28
forum: General Help
---

### Post by Somenoob on 2008-09-28
This doesn't pertain to any ubuntu variant. I was wondering what is there to do when you can't boot from a usb pen/thumb on a modern machine that's supposed to have that capability? 
There's nothing wrong with my USB flash drive, I tried to boot an OS from it on my laptop and it works perfectly.

---

### Post by nowshining on 2008-09-28
did you try looking the bios? is it (the option to boot from a usb drive) turned on in the bios??

---

### Post by Somenoob on 2008-09-29
> **nowshining said:**
> did you try looking the bios? is it (the option to boot from a usb drive) turned on in the bios??

Yeah, in fact "removable" is the first boot value.

---

### Post by C.S.Cameron on 2008-09-29
What happens when you try to boot the flash?
Does it boot the hard drive instead or just fails to find a boot device? 
Do you get a grub error like 17 or 21?

---

### Post by Somenoob on 2008-09-29
> **C.S.Cameron said:**
> What happens when you try to boot the flash?
Does it boot the hard drive instead or just fails to find a boot device? 
Do you get a grub error like 17 or 21?

If I manually boot from flash it just states there's nothing to boot from.

---

### Post by C.S.Cameron on 2008-09-29
On some of my newer machines the flash drive is listed under hard drives in bios, if yours is the same, is your flash listed as the first hard disk?
Removable as first in boot order may not be enough.
The name of the flash drive is usually shown in the boot order and not just removable, something like JetFlash or such.

---

### Post by Somenoob on 2008-09-29
> **C.S.Cameron said:**
> On some of my newer machines the flash drive is listed under hard drives in bios, if yours is the same, is your flash listed as the first hard disk?
Removable as first in boot order may not be enough.
The name of the flash drive is usually shown in the boot order and not just removable, something like JetFlash or such.

Problem solved :)

Apparently it was just detected incorrectly as a HDD(anyone know why? seems to be a common glitch among the newest computers)
thanks man, live distros run so much better on flash drives.

---

### Post by C.S.Cameron on 2008-09-29
I suspect that the guys that write BIOS have a inside tip that mechanical drives will soon be obsoleted by SSD's.

---

