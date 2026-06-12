---
title: "Suspend/Hibernate ThinkPad T30"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by woodsworth on 2006-02-19
Hello all, just freshly installed Kubuntu, having recently migrated from MEPIS. Anyway, I've been trying to get Suspend/Hibernate to work, and I'm halfway there. Fn+F12 suspends to disk (hibernates) but Fn+F4 does nothing. I went through the instructions for installing Breezy on a T42, purged "splash" from /boot/grub/menu.lst, but still no dice. I had Suspend and Hibernate working in MEPIS with a custom kernel that I didn't compile myself. Suspending to disk is nice, but I would like to have my computer sleep as well as hibernate. Can anyone help?

---

### Post by JELaVallee on 2006-02-19
[QUOTE=woodsworth]I had Suspend and Hibernate working in MEPIS with a custom kernel that I didn't compile myself. Suspending to disk is nice, but I would like to have my computer sleep as well as hibernate. Can anyone help?[/QUOTE]

woodsworth,

I've been having similar issues with Ubuntu Breezy on a T43p... started a thread here: [http://www.ubuntuforums.org/showthread.php?t=133227](http://www.ubuntuforums.org/showthread.php?t=133227)

Are you booting with acpi=off?

Do you also have the batter-power lockup issue I describe in my thread?

I'm trying to narrow this down to a specific set of modules/services on notebooks/thinkpads.

cheers,
Etienne

---

### Post by mjg59 on 2006-02-20
Edit /etc/default/acpi-support, uncomment the line starting #ACPI_SLEEP, save, reboot and it should work.

---

### Post by woodsworth on 2006-02-20
[QUOTE=mjg59]Edit /etc/default/acpi-support, uncomment the line starting #ACPI_SLEEP, save, reboot and it should work.[/QUOTE]

That worked. Thank you.

---

