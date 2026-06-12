---
title: "thermal.ko fan.ko error"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by grinchy on 2006-01-18
Ok so I know that this might be an old problem that was fixed a long time ago but I have trawled the web (and these forums) and have found very little.

My problem is that when I boot my T21 (using apm, not acpi) I get two errors.

FATAL: Error inserting fan (/lib/modules/2.6.12-9-686/kernel/drivers/acpi/fan.k o): No such device
FATAL: Error inserting thermal (/lib/modules/2.6.12-9-686/kernel/drivers/acpi/thermal.ko): No such device

The 'No such device' leads me to think that the device hasn't been made, but my question is this: How can I stop loading all acpi modules?

It is not as simple as apm=on acpi=off as boot arguments.

---

### Post by ULffuntu on 2006-02-16
Yeah me too, any luck with that?

---

### Post by RainKap on 2006-04-04
At least it looks as though I'm suffering in company. My system is a desktop with an old AT motherboard, carrying a PII 300MHz with 512MB RAM, that I'm using as the basis for a file server for my home network - text-only install of Breezy.

As a "bonus", just before the error messages for the fan.ko and thermal.ko modules, I get an error message:

ACPI unable to locate RSDP.

I'll be interested to see whether anybody can shed light on this!

Ian

---

### Post by admrt on 2006-04-05
I'm still trying to find the solution for the same thing. One option is, of course, recompling the kernel without ACPI support. Another way would be a matter of mounting the initial ramdisk image and deleting those 2 modules. I haven't tried yet. But concerning the other message you get "ACPI unable to locate RSDP", I have solved it by adding acpi=off to the grub line where you specify the kernel. Something like this:

kernel /boot/vmlinuz-2.6.12-9-386 acpi=off root=/dev/hda1 ro quiet splash

Luigi

---

### Post by RainKap on 2007-03-01
Thanks, Luigi, for the pointer to the fix for the RSDP error; I have put the "acpi=off" phrase into the appropriate lines of /boot/grub/menu.lst and it's happy now. I also noticed that since I upgraded to Xubuntu v6.10 the thermal.ko and fan.ko error have gone away.

Cheers

Ian

---

