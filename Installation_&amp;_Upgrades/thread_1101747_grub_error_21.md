---
title: "grub error 21"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by your.name on 2009-03-20
i recently installed ubuntu on a windows xp computer to dual boot.
i installed ubuntu to a flash drive because i was having trouble correctly partitioning the hard drive. when i discovered that ubuntu ran very slowly from the flash drive i decided to abandon it and reformatted the flash drive for normal use. now the computer will not boot (i assume because the grub was on the flash drive) and i can't figure out how to get it to boot at all.

does anyone know how to get it to boot windows again?

ps i also tried putting in a live cd, but it won't boot from there either

---

### Post by jbrevik on 2009-03-20
> **your.name said:**
> i recently installed ubuntu on a windows xp computer to dual boot.
i installed ubuntu to a flash drive because i was having trouble correctly partitioning the hard drive. when i discovered that ubuntu ran very slowly from the flash drive i decided to abandon it and reformatted the flash drive for normal use. now the computer will not boot (i assume because the grub was on the flash drive) and i can't figure out how to get it to boot at all.

does anyone know how to get it to boot windows again?

ps i also tried putting in a live cd, but it won't boot from there either

This will probably take care of it:
[http://www.pendrivelinux.com/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/grub-error-21-after-full-install-to-usb-hard-drive/)

Wait a second! That wont work. Just insert your xp install cd and run in recovery mode. Once your in recovery mode run C:\WINDOWS\fixmbr

---

### Post by your.name on 2009-03-20
thanks!
i will try that

---

