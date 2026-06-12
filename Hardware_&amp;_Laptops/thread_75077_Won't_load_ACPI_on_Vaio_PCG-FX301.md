---
title: "Won't load ACPI on Vaio PCG-FX301"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by axcairns on 2005-10-13
Hey all,

I just got my Breezy install cd hot off bittorrent and installed it on my Sony Vaio PCG-FX301 laptop. This laptop previously ran Hoary ok but because of a few niggles I decided to wipe the drive and install Breezy fresh. 

First reboot during the install process worked ok and everything came up ok including X and Gnome. However, when I rebooted for the first time following installation, the boot hung at the step 'Loading ACPI modules...'. 

Help!

Allan

---

### Post by axcairns on 2005-10-15
Never mind - reinstalled with acpi=off. It spends 99% of it's time plugged in anyway.

Allan

---

### Post by az on 2005-10-15
If acpi is not running, Ubuntu will try to use apm....  So you should be good to go.  

If you do not have any power management, check your bios settings to see what is enabled or disabled.  Often you can use one or the other or both....

---

### Post by ninja_indiano on 2005-11-12
[QUOTE=azz]If acpi is not running, Ubuntu will try to use apm....  So you should be good to go.  

If you do not have any power management, check your bios settings to see what is enabled or disabled.  Often you can use one or the other or both....[/QUOTE]


If you installed you OS with acpi=off you can turn back it on (if the kernel you have suports it) just going to the grub and delete the line that says acpi=off

/boot/grub/grub.conf.


if you use lilo

/etc/lilo.conf

if you use lilo you have to reconstruct the boot sector using the command "lilo".


Sorry if it's too late....but just found out a few hours...

---

