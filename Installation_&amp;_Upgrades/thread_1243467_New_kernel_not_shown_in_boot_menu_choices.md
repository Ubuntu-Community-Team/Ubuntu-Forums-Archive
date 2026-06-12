---
title: "New kernel not shown in boot menu choices"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2009-08-18
Today's Upgrade gave a new Kernel "2.6.28.15"

However, I accidentally clicked upon "keep the current menu"
After the usual reboot, the new kernel does not show in the list of choices for booting. How do I get the new kernel to show up?

Thanks,

---

### Post by Bachstelze on 2009-08-18
```
sudo update-grub
```

---

### Post by Cheesemill on 2009-08-18
```
 
sudo update-grub

```
 
*Edit - Beaten to it* :)

---

### Post by wil08son on 2009-08-18
I run that code and get this.

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

But I only get 2.6.28-11 in GRUB. :confused:

---

### Post by presence1960 on 2009-08-18
> **wil08son said:**
> I run that code and get this.

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

But I only get 2.6.28-11 in GRUB. :confused:

You are going to have to manually edit the menu.lst file to include the kernels you wish to use. You can see how to build a kernel entry by looking at the existing one on there already.

next time choose to use the package maintainer version of menu.lst. (lesson learned)

Or you can uninstall 2.6.28-15 in synaptic and then reinstall it.

---

### Post by Oldhacker on 2009-08-19
This morning, the Update Manager told me again that there was a "new" kernel, which turned out to be the same 2.6.28.15-generic that I installed yesterday.

After letting it re-install the "new" kernel, I decided not to be lazy and got out the trusty gedit and added the new kernel to menu.lst (after first backing up menu.lst to menubackup.lst.)
Hopefully, I won't be nagged for a while now. ;-)

Thanks for the help

---

