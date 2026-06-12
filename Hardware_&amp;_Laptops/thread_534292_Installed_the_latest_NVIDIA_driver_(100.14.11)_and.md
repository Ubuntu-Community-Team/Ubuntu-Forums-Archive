---
title: "Installed the latest NVIDIA driver (100.14.11) and can't login to X"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by jutirain on 2007-08-25
I've installed the latest NVIDIA driver (100.14.11) for IA32, which downloaded from NVIDIA official site on my laptop.

The installation was sucess, however, I can't get into X again after reboot...

restoring the xorg.conf was useless.

Laptop: VAIO SZ 92
OS: Ubuntu 7.04
Kernel version: 2.6.20-16-generic
Graphics Card: NVIDIA 7400

Any help??
Thanks a lot! :(

---

### Post by tseliot on 2007-08-25
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

then read this:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by jutirain on 2007-08-25
Still unsolved. :(

Maybe its not the problem of xorg.conf?

How can I uninstall the driver (100.14.11) and use the previous one?

---

### Post by Lexi on 2007-08-25
try this if you downloaded from the nvidia site:

```

sudo apt-get --purge remove NVIDIA-Linux-x86-100.14.11-pkg1.run

```

or replace NVIDIA...-pkg1.run with the name of your package

---

### Post by jutirain on 2007-08-25
I change directory to where I store the script and type what you say, the system reply:

```

E: Coudn't find package NVIDIA-Linux-x86-100.14.11-pkg1.run

```

---

### Post by tseliot on 2007-08-26
> **Lexi said:**
> try this if you downloaded from the nvidia site:

```

sudo apt-get --purge remove NVIDIA-Linux-x86-100.14.11-pkg1.run

```

or replace NVIDIA...-pkg1.run with the name of your package

the right command is:
```
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run --uninstall
```

---

### Post by jutirain on 2007-08-26
I've removed the driver downloaded from official site, and reconfigured the xserver-xorg (both vesa & vga), however, still unsolved... :(

Should I install original driver built in the feisty? How?

---

### Post by userlain on 2007-08-29
I had the exact same issue with the 100.14.11 driver but the 1.0.9755 driver works perfect. You can find it in the NVidia archives.

---

### Post by Marat Galiev on 2007-08-30
install deb packages
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia-glx-new&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia-glx-new&searchon=names&subword=1&version=feisty&release=all)
works fine with many cards.

---

