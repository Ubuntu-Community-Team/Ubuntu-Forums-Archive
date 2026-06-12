---
title: "Hidden Ubuntu install?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Dispenser on 2009-11-03
I'm wondering if it is possible to install Ubuntu on my computer at work so that it still boots strait into windows vista (for my boss' sanity) while a hotkey will allow to you boot Ubuntu before windows loads.

Thanks in advance,
PEZ

---

### Post by Fatman_UK on 2009-11-03
You can do it with a bit of GRUB magic, but he'll still see the "press esc to enter bootloader menu" message.

Put two primary partitions on your disk. Install Vista into the first one and Ubuntu into the second one. Choose to install the GRUB bootloader when it asks.

Hopefully it should detect both installs and set up the bootloader menu correctly. If not you'll need to fiddle with /boot/grub/menu.lst, but it's not too hard.

---

### Post by Dispenser on 2009-11-03
That wont work.  Is it possible to modify the GRUB time interval before it auto boots?  So it will display GRUB for like 1 second and then boot strait to windows without any intervention?

---

### Post by drs305 on 2009-11-03
> **Dispenser said:**
> That wont work.  Is it possible to modify the GRUB time interval before it auto boots?  So it will display GRUB for like 1 second and then boot strait to windows without any intervention?

Yes. You can even set the timeout to 0 if you wish so you will never even see the menu. In grub you would display it by hitting ESC. In grub 2 you reveal the menu by holding down the shift key.

And you can set it up to automatically boot to either OS (Windows for now, Ubuntu after you convert him/her ;-)  ).

---

### Post by ManiacDan on 2009-11-03
If you're looking for a completely discrete solution, you can install ubuntu to a bootable flash drive or to a truecrypt bootable partition on the existing drive.

Having GRUB auto-boot into Windows unless otherwise told is probably the best option if it's just for the boss's sanity.

-Dan

---

### Post by Dispenser on 2009-11-04
Thank you! ):P

---

