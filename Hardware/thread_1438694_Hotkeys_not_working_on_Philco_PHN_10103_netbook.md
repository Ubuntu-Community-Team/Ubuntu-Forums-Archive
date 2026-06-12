---
title: "Hotkeys not working on Philco PHN 10103 netbook"
date: 2010-03-25
forum: Hardware
---

### Post by luisfpg on 2010-03-25
I bought a Philco PHN 10103 netbook and got everything to work, but the hotkeys.
It is recognized by the asus-laptop module, and I say in the windows drivers from the support page (download at [http://www.britania.com.br/arquivos/philcoshop/informatica/PHN10103aPHN10107/HotkeyUtility_V1.00.0049.zip](http://www.britania.com.br/arquivos/philcoshop/informatica/PHN10103aPHN10107/HotkeyUtility_V1.00.0049.zip)) that it is an ATK0100, which, according to acpi_asus manpage ([http://manpages.ubuntu.com/manpages/lucid/en/man4/acpi_asus.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/en/man4/acpi_asus.4freebsd.html)) is supported.

However, none of the hotkeys are working, and, for example, cat /proc/acpi/video/IGD/LCD/brightness yields <not supported>. It's clear that the hardware is not being correctly supported by the module.

Does anyone knows how to make it work? I'm attaching the results of lshw, and lspci -vv.

[EDIT]: I forgot to mention I'm using lucid netbook remix beta.

Thanks a lot.

---

### Post by Hawk__0 on 2010-03-26
bumping this, I'm still trying to figure this out.  I also have the asus laptop module on mine.  For me, it's the keyboard backlight (up and down, and off), and monitor brightness.

---

