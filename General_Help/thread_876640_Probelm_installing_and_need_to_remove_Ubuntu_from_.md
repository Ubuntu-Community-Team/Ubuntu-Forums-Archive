---
title: "Probelm installing and need to remove Ubuntu from grub"
date: 2008-07-31
forum: General Help
---

### Post by gresch on 2008-07-31
ok, so i recently tried to install ubuntu 8.04 on my computer using Wubi. Unfortunately, every time I've tried to install it i get an error (1512), text flashes across the screen and it eventually stops in the middle of installing and nothing happens. I've tried uninstalling and reinstalling several times, but it has'nt worked. even though i've uninstalled them, each attempt still remains on the boot selection thing (i think its called grub). Does anyone know what might be causing this error, and how I can remove these uninstalled ubuntu attempts from the boot menu? The version of windows i am using is Vista, and my computer is a Toshiba Satellite A305-S6858. Also, I do not have a working copy of linux on the computer, but the live cd works on it perfectly.

---

### Post by Kobalt on 2008-08-01
I think if you remove Ubuntu grub is gone as well. What remains in your case, I believe, is the boot selector of Windows. To remove the Ubuntu entry in this selector, go in your Windows Config Panel > System. Click the Advanced tab and go in the Boot and recovery settings. 
From there you can modify manually the boot sequence and remove Ubuntu, you can also select how long the operating systems selector is displayed, and so on.

---

### Post by ago on 2008-08-01
To uninstall see [https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1](https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1)

---

