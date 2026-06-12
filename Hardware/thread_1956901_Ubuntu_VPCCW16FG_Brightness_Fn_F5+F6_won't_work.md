---
title: "Ubuntu VPCCW16FG Brightness Fn F5+F6 won't work"
date: 2012-04-11
forum: Hardware
---

### Post by rfictus on 2012-04-11
If anyone can help get my brightness shortcut keys working for my Vaio VPCCW16FG, would greatly appreciate. 
Running Ubuntu 11.10. Shortcut keys work and bar moves but screen back-light doesn't change. 
Stops working after installing the 'recommended updates (oneiric-updates)'.
*BUMP*

Could do a Ubuntu reinstall but would rather know which update is causing the problem.

---

### Post by rfictus on 2012-04-13
*bump**

---

### Post by rfictus on 2012-04-14
*bump* Just put a response here as well: [http://askubuntu.com/questions/55096/display-brightness-scaling-is-incorrect-on-a-vaio-cw/121977#121977](http://askubuntu.com/questions/55096/display-brightness-scaling-is-incorrect-on-a-vaio-cw/121977#121977)

---

### Post by coffeecat on 2012-04-15
Does your Vaio have a nvidia graphics card? A google search suggests it might. If so, have a look here:

[http://ubuntuforums.org/showpost.php?p=11613896&postcount=7](http://ubuntuforums.org/showpost.php?p=11613896&postcount=7)

With my VPCEJ1Z1E (with nvidia graphics), installing the proprietary nvidia driver and using the xorg.conf edit in that link works for me in 12.04. I didn't try it in 11.10.

Make sure you have the proprietary driver installed and one of those fixes may help you.

---

### Post by rfictus on 2012-04-15
Thanks coffeecat for your interest in my issue.

Tried the first (no success). The second, requires I enter these lines of code:

- acpi_backlight=vendor
- acpi_osi=Linux
- acpi_osi=
- acpi_osi=Linux acpi_backlight=vendor

but where precisely??


I've entered them in the GNU kernel grub area at start-up. After exiting, the system rejects and deletes the lines.

Am I doing it right??

---

### Post by coffeecat on 2012-04-15
> **rfictus said:**
> 
I've entered them in the GNU kernel grub area at start-up. After exiting, the system rejects and deletes the lines.

I'm not quite sure what you mean by that. If you add one or more of those options after "ro quiet splash", and then press crtl-X, the system should boot up with the options. It's s way of testing them, and if any work I can show you how to add them to the kernel line permanently.

For the first, are you sure you added the line to the correct part of /etc/X11/xorg.conf? It has to be within the Device section. This is my complete xorg.conf file for my Sony Vaio:

```

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
	Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection

```

I found that with my model Vaio, that was the only thing that worked. The grub options didn't help.

---

### Post by rfictus on 2012-04-15
Fixed! 

For Vaio's with nvidia backlight adjust issue (fn f5+f6), bar moving but no change in brightness.

This is this one you want: [http://ubuntuforums.org/showpost.php?p=11846307&postcount=44](http://ubuntuforums.org/showpost.php?p=11846307&postcount=44)

My case:

Ubuntu 11.10
All security update + recommended updates installed. Kernel version 17.

---

