---
title: "Brightness cannot be changed on 8600M GT"
date: 2012-07-08
forum: Hardware
---

### Post by farukdgn on 2012-07-08
Hi. I can't set brightness on my laptop. Has 8600M GT in it. How can I solve? :confused:

---

### Post by Redblade20XX on 2012-07-08
Do you have the proprietary graphics card driver installed or the open-source one?

- Red

---

### Post by farukdgn on 2012-07-09
I couldn't change brightness while I wasn't using any drivers from "Restricted Drivers". (If you mean open source driver is that)
I tried to install recommended one there, but I still can't change brightness.

---

### Post by Redblade20XX on 2012-07-09
> **farukdgn said:**
> I couldn't change brightness while I wasn't using any drivers from "Restricted Drivers". (If you mean open source driver is that)
I tried to install recommended one there, but I still can't change brightness.

Can you tell us your system specifically?
What version of the NVidia drivers you have installed?

You can try pushing the **acpi_backlight=vendor** kernel parameter.
Take a look here: [https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

If that doesn't work can you try this?
[http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32](http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32)

- Red

---

### Post by farukdgn on 2012-07-10
> **Redblade20XX said:**
> Can you tell us your system specifically?
What version of the NVidia drivers you have installed?

You can try pushing the **acpi_backlight=vendor** kernel parameter.
Take a look here: [https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

If that doesn't work can you try this?
[http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32](http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32)

- Red

Hi again. I'm beginner to Ubuntu. I tried to do first one but I couldn't do. I installed Boot Repair. But I don't know how to write acpi_backlight=vendor option. There's a list that doesn't contain this option.
For second one, I don't see xorg.conf file in X11 folder.
I don't have any NVidia drivers installed now, because it has problems for me. Versions of drivers aren't shown in Restricted Drivers.
My system:
 Intel T9300 CPU
 Ubuntu 12.04 + Windows 7 + OS X Lion
 GeForce 8600M GT GPU
 3GB 677 MHZ RAM
Thanks.

---

### Post by YannBuntu on 2012-07-12
Hello

> **farukdgn said:**
> I installed Boot Repair. But I don't know how to write acpi_backlight=vendor option. There's a list that doesn't contain this option.

You can click the "Edit GRUB configuration file" button then add/remove any option in the GRUB_CMDLINE_LINUX_DEFAULT line then save the file. Then click Apply.

[IMG]http://pix.toile-libre.org/upload/img/1312988983.png[/IMG]

---

