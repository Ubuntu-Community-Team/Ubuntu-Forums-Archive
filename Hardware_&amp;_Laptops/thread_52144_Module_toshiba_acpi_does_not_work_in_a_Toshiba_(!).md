---
title: "Module toshiba_acpi does not work in a Toshiba (!?)"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by Angel Herranz on 2005-07-26
I have a Toshiba M40-145 almost functional (acpi, wireless, lan ,etc.) thanks to [http://ubuntuforums.org/showthread.php?t=46423](http://ubuntuforums.org/showthread.php?t=46423) and [http://ubuntuforums.org/archive/index.php/t-46423.html](http://ubuntuforums.org/archive/index.php/t-46423.html).

My last problems (i hope):

 * The laptop does not suspend, it hangs.

 * Fn-Keys does not work because the module toshiba_acpi cannot be loaded:

root@exodo4:/home/angel # modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.10-5-686/kernel/drivers/acpi/toshiba_acpi.ko): No such device
root@exodo4:/home/angel # /etc/init.d/fnfxd start
Starting Toshiba hotkeys utils: FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).

Any positive orientation?  (I've found a negative one: [http://memebeam.org/toys/ToshibaAcpiDriver)](http://memebeam.org/toys/ToshibaAcpiDriver)).

Thanks in advance.

--
Angel

---

### Post by art on 2005-07-28
I am pretty sure that I read somewhere that for all this to work you need a native TOSHIBA BIOS on your lappy. Probably you don't... I don't too:(

---

### Post by Michalxo on 2008-04-24
Any new info about this issue?
I have the same problem but I have A200
:-/

---

