---
title: "Intel 82801G-How to config?"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by lancest on 2007-03-31
[COLOR="Navy"]My laptop:[/COLOR]
[https://wiki.ubuntu.com/LaptopTestingTeam/AsusW7J](https://wiki.ubuntu.com/LaptopTestingTeam/AsusW7J)
[COLOR="Navy"]My sound card:[/COLOR]
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
Supported by the the [SIZE="5"]snd_intel_hda module.[/SIZE]. How to add the following
**options snd_hda_intel model=3stack position_fix=1**
[SIZE="4"] Supposed to be in /etc/modules.conf (according to other distro's)[/SIZE]. Where is config file?

---

### Post by mikewhatever on 2007-03-31
What is exactly 'the other distro's'?
A search for modules.conf in 6.10 turnes up this:
> ~$ locate modules.conf
/var/lib/dpkg/info/libpam-modules.conffiles
/var/lib/dpkg/info/perl-modules.conffiles
/etc/gnome-vfs-2.0/modules/ssl-modules.conf
/etc/gnome-vfs-2.0/modules/mapping-modules.conf
/etc/gnome-vfs-2.0/modules/default-modules.conf

---

### Post by lancest on 2007-03-31
See this:[B]3.4 Sound (Alsa)

Supported by "snd_intel_hda" module with "model=3stack position_fix=1" parameter, 

Automatic load at boot with option:
edit "/etc/modprobe.conf"¹, add the following line:
options snd_hda_intel model=3stack position_fix=1
This is all over the web.[/B]
[COLOR="Blue"]Anyway I just added it into the /etc/modprobe.d/alsa-base file at the bottom.
Works fine.[/COLOR]

---

