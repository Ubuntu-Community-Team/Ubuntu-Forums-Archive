---
title: "Toshiba M40X doesnt wake up after suspend"
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by Jergar on 2005-11-13
I have Ubuntu 5.10 installed on the notebook. When aktivate suspend to disk (in the logout dialog) the notebook is suspending. But the wakeup is not working. 

What is wrong?

Wolf

---

### Post by AppleCrow on 2005-11-13
Hi,

I've also a Toshiba M40X and I've not problem with sleep or suspend to ram mode (after editing the acpi-support file to enable it)
My video card is a i915.

But what's the one you have?

---

### Post by Jergar on 2005-11-13
Which acpi file did you have modified? I have nothing edited.
My graphic is also a 915.

---

### Post by AppleCrow on 2005-11-13
I've edited /etc/defaut/acpi-support and remove the # front of ACPI_SLEEP line.
But suspend mode works out of the box, if I remember well.

On my laptop I've removed any existing partitions to install Ubuntu as main operating system.

I've edited configuration's files only to enable CPU throttling on my Celeron M, disable/enable CPU throttling when on AC/battery, and enable suspend to RAM.

---

### Post by ranf on 2005-11-13
[QUOTE=Jergar]I have Ubuntu 5.10 installed on the notebook. When aktivate suspend to disk (in the logout dialog) the notebook is suspending. But the wakeup is not working. 

What is wrong?
[/QUOTE]
Suspend to disk is usually called hibernate.
You need to tell the kernel where the swap partition is. This is done by editing the file 
`/boot/grub/menu.lst'.
For me the kopt line looks like this:
# kopt=root=/dev/hda4 ro resume=/dev/hda3 acpi=force

The part with resume= is what you need. To find out what your swap partition is, type:
```
sudo fdisk -l /dev/hda
```

---

### Post by Jergar on 2005-11-14
Thanks it was working now. I have modified the  /etc/default/acpi-support and the menu.lst from Grub. 

Thanks again

---

