---
title: "Including Ubuntu in the Bootloader"
date: 2008-08-07
forum: Hardware
---

### Post by pugalenthi_i on 2008-08-07
Hi,i have two harddisks.The first harddisk is master which has xp and Opensuse(DualBoot).so it has the opensuse bootloader..Later on i have installed Ubuntu8.04 in my second harddisk which is a slave harddisk..So is there any possibity to include ubuntu in Opensuse's Bootloader..So that i can boot OpenSUSE,Ubuntu and XP from Opensuse's bootloader...:(:(

---

### Post by Jaggernaut on 2008-08-07
Do you know what bootloader Opensuse uses, GRUB, LILO etc?

---

### Post by Jaggernaut on 2008-08-07
Actually it doesn't really matter what bootloader you are using. What you have to do is to find the configuration file for the bootloader and add one section for ubuntu. There are a lot of information on the net on how to do that.

Typically the configuration file are placed in (if you are using grub):
/boot/grub/grub.conf or /boot/grub/menu.lst

---

### Post by pugalenthi_i on 2008-08-07
thanks..i will try and let u know....

---

