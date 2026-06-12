---
title: "boot splash"
date: 2008-09-13
forum: General Help
---

### Post by Okar on 2008-09-13
hi,
when booting, the boot splash is not shown during the whole boot process, it's like:
grub->some seconds of plain text -> boot splash -> no boot splash, but plain text. it's about when mouting all file systems, therefore I can't stop the fsck anymore.
in menu.lst the splash option is provided. I also reinstalled the boot_splash package. any more ideas?
anyone got similar problems?

---

### Post by northern lights on 2008-09-13
The bootsplash not adhering to the settings set in menu.lst is unfortunately a common bug.

As for fsck, you might want to check [https://wiki.ubuntu.com/AutoFsck]("https://wiki.ubuntu.com/AutoFsck")

---

### Post by kokkus on 2008-09-13
**[COLOR="Blue"]How to fix this problem:[/COLOR]**

Edit

/boot/grub/menu.lst

change the following line

kernel          /boot/vmlinuz-2.6.26-5-generic root=UUID=801683d9-5e74-4ad6-91e9-6f05622ac006 ro

to

kernel          /boot/vmlinuz-2.6.26-5-generic root=UUID=801683d9-5e74-4ad6-91e9-6f05622ac006 ro quiet splash

Good luck:)

---

### Post by Okar on 2008-09-14
the "splash" option is being passed, the boot splash is displayed partly, but only partly and furthermore it varies from boot to boot, sometimes it is display during the whole boot, it's really strange actually oO

---

