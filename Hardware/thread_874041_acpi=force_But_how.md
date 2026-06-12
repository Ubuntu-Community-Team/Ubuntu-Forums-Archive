---
title: "acpi=force But how?"
date: 2008-07-29
forum: Hardware
---

### Post by bro on 2008-07-29
A very old laptop states on boot that acpi is turned off because of too old bios and that it needs acpi=force to turn on. How do I try this? (I mean, in a way that is easily to revert if everything fails)

From /boot/grub/menu.lst
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a827eeb5-37a7-4d95-a450-945980a556a5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

---

### Post by cdtech on 2008-07-29
Just add "acpi=force" to the kernel options:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a827eeb5-37a7-4d95-a450-945980a556a5 ro quiet splash **acpi=force**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

**P.S.**
see also "[[COLOR="DarkRed"]boot-options[/COLOR]]("https://help.ubuntu.com/community/BootOptions")"

---

