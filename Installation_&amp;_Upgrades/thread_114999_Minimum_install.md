---
title: "Minimum install"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by hen3rz on 2006-01-09
Hello,

I was wondering if there was a way i could configure ubuntu so i cauld install the bare minimum i would need to run it so i can use it on a very old low spec laptop.

Any help would be appreciated.

Thank you.

---

### Post by lha on 2006-01-09
[QUOTE=from Ubuntu Installer]
The default installation is suitable for most desktop or laptop systems.
Press F1control and F then 1 for help and advanced installation options.

To install only the base system, type 'server' then ENTER.
For the default installation, press ENTER.
[/QUOTE]

Put install cd in, boot, type server and press enter to start installation. It won't give you any GUI at all, you'll have to apt-get install for those. Maybe you would like [Xubuntu]("https://wiki.ubuntu.com/Xubuntu")? It installs [XFCE]("http://www.xfce.org/") as default desktop environment. XFCE is lighter than Gnome, but still pretty and nice to use.

---

### Post by stuporglue on 2006-01-09
If it's REALLY low and you know sort of what you're doing, as soon as the installer boots (right after the blue screen after typing server and hitting enter) you can press alt+RightArrow and use cfdisk or fdisk to partition your disk. Once you've partitioned you can immediately use the swap partition you make. Activate it by running:

mkswap /dev/hda3
swapon /dev/hda3

if /dev/hda3 were your swap partition. 

You may have enough memory to run the installer without this procedure, but it's made the install work a couple of times on older machines for me.

---

### Post by hen3rz on 2006-01-09
[QUOTE=stuporglue]If it's REALLY low and you know sort of what you're doing, as soon as the installer boots (right after the blue screen after typing server and hitting enter) you can press alt+RightArrow and use cfdisk or fdisk to partition your disk. Once you've partitioned you can immediately use the swap partition you make. Activate it by running:

mkswap /dev/hda3
swapon /dev/hda3

if /dev/hda3 were your swap partition. 

You may have enough memory to run the installer without this procedure, but it's made the install work a couple of times on older machines for me.[/QUOTE]

Hey thanks heaps this will come in handy.

Also is it possible to just install Gnome and nothing else without having to use apt-get to install it once the base system is done?

(**Reason:** No access to internet to use apt-get)

---

### Post by lha on 2006-01-13
[QUOTE=hen3rz]Hey thanks heaps this will come in handy.

Also is it possible to just install Gnome and nothing else without having to use apt-get to install it once the base system is done?

(**Reason:** No access to internet to use apt-get)[/QUOTE]

You can use your preferred package manager (and apt-get) to install packages from cd. "Nothing else but Gnome" part is impossible if taken at package level as Gnome depends on many libaries and other packages but you can install the minimum number of packages that Gnome needs. Apt or your chosen package manager will automatically install needed packages.

---

