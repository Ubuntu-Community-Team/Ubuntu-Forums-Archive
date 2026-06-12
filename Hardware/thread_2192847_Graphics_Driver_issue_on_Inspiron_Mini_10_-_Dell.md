---
title: "Graphics Driver issue on Inspiron Mini 10 - Dell"
date: 2013-12-10
forum: Hardware
---

### Post by nlakes2 on 2013-12-10
[COLOR=#333333][FONT=UbuntuRegular]I'm trying to install Ubuntu 12.04 LTS on a Dell Inspiron Mini 10 and although the live CD worked fine, now I've installed it, the graphics driver appears to be having some serious issues.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][Like so]("http://i.imgur.com/9MUbFJ2.jpg")[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I'm not the best at Ubuntu or Linux, so clear advice how I can find and install a working driver would be great.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Many thanks.[/FONT][/COLOR]

---

### Post by Bashing-om on 2013-12-10
nlakes2; Hi ! Welcome to the forum .

Try this:
Boot the install with the boot parameter "nomodeset" -> recommended driver install;

As soon as the bios screen clears, depress and hold the shift key -> grub boot menu,
With the top entry (non recovery) kernel line high lighted , depress the "e" key for edit mode -> boot parameters screen;
Arrow down and across to the terms "quiet splash" and insert also the term "nomodeset" - with out the quotes-,
Key combo ctl+x to continue the boot process to the GUI login, degraded graphics at this point is OK.
Login here and now to install a driver:

Left side of the screen is the launcher -> System Settings -> Additional Drivers;
Install the recommended driver. This procedure assumes that you have a working internet connection, and that 3rd party repositories have been enabled (Software Sources).

[INDENT][INDENT]hope this helps[/INDENT][/INDENT]

---

### Post by nlakes2 on 2013-12-10
Thanks for the suggestion. I've added nomodeset and hit ctrl + x but I'm booting up into a black screen now. 

Have you any other suggestions? Otherwise, can you recommend another user friendly distro to try to install on this old PC?

EDIT: I should also add I've tried booting in failsafe graphics mode too, which did not work either.

EDIT2: I have found the command line in GRUB, can someone tell me perhaps how to force install basic graphics drivers via command line?

---

### Post by Bashing-om on 2013-12-10
nlakes2; Hey,

A quick look-about, you have the GMA 500 chip set for graphics. That has been problematic.
See if these links provide a solution: This one offers 3 possibilities, as well as lots more documentation on other aspects.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

In depth, and not directed to a new user, but with good back ground info:
[https://wiki.archlinux.org/index.php/Poulsbo](https://wiki.archlinux.org/index.php/Poulsbo)

Looks very likely that it is workable;
[INDENT][INDENT]there is a way
[/INDENT][/INDENT]

---

