---
title: "VIA UniChrome drivers – getting 2D acc./Flash to work"
date: 2012-07-28
forum: Hardware
---

### Post by Lukfi on 2012-07-28
Hi. I've got an old PC here and I decided to install Ubuntu 12.04 on it, but I can't get the graphics to work properly. The motherboard is an Asus A7V8X-MX with VIA KM400 / VT8235 chipset (yes, that old) and there's an onboard UniChrome graphics adapter in it. I had to use the alternate installation CD and select acpi=off, otherwise it would crash during the installation. I don't know if that's relevant.

Right after Ubuntu installation, the display resolution was set correctly, but performance when dragging windows etc. is sloppy and the cursor is flickering. The software control center thingy (I don't know the exact name, my system is not in English) shows that Openchrome is installed, which should be the correct driver, but I think it's not being used.

This is my first time using Ubuntu 12.04. I do have some limited experience with Linux, but unfortunately, getting graphics to work on any machine that is not virtual is not among it.

I'll be grateful for any help you could provide. I have searched the forums, but didn't find any similar problems to the one I have.

---

### Post by Lukfi on 2012-08-03
Nobody knows? So I'll at least "up" the thread, I hope it's not against the rules here.

---

### Post by gio10 on 2012-09-16
Hi I have a similar problem.

I have an acer aspire 1350. It used to work properly on 10.04. After upgrading to 12.04.1 I have few issues:

* flash player does not work in firefox
* mouse pointer flikering sometimes (in gimp is almost impossible to see the pointer).
* initial splash screen shows half graphics and half text
* sometimes it hangs during shutdown 

In 10.04 I had to work a lot to have display working. I cannot remember all the details, but I mainly solved by changing the xorg.conf file.

Just few details:

01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

Xorg.0.log gives two errors:
[    37.834] (EE) AIGLX error: dlopen of /usr/lib/i386-linux-gnu/dri/unichrome_dri.so failed (/usr/lib/i386-linux-gnu/dri/unichrome_dri.so: cannot open shared object file: No such file or directory)
[    37.834] (EE) AIGLX: reverting to software rendering

Please, help.
Thanks!!!

---

