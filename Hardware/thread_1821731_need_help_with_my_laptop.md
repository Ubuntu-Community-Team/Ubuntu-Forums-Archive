---
title: "need help with my laptop"
date: 2011-08-09
forum: Hardware
---

### Post by thelildrummaboy on 2011-08-09
I'm running a Acer Aspire 5734Z-4836.

Ran and install Ubuntu 11.04 32bit without running windows alongside. Everything is working properly but the brightness and/or backlight is still completely black. 

I found a code for a different model of an Aspire and didn't know if it was the same, I'm still new at Ubuntu. 

Where would I place this code? 
Terminal or in the boot manager while running the startup?

Any help would be awesome.

_**Code:**_
sudo gedit /etc/default/grub

Edit two lines to read as follows: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

---

### Post by Metaxa on 2011-08-10
On the left bar select Applications, in the search box type terminal.


Once it opens enter the following command:

sudo gedit /etc/default/grub

this will open a text file at which point you alter the file as stated by the post you found. Save the file. then run:

sudo update-grub

and then reboot your machine and things should be good.


Regards,

Metaxa

---

