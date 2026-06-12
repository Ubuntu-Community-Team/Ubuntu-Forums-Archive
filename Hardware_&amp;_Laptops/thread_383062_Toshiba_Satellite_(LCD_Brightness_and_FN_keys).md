---
title: "Toshiba Satellite (LCD Brightness and FN keys)"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by NTITech on 2007-03-12
I have Ubuntu Edgy installed on my Toshiba Satellite A105-S4114.  How can I change the LCD brightness and also use the 'FN' keys?

---

### Post by SonicTheHedgehog on 2007-03-12
I too have the same trouble.

---

### Post by NTITech on 2007-03-19
*bump

---

### Post by Xenogis on 2007-03-20
if it has a phoenix bios you could look into the omnibook kernel module

---

### Post by NTITech on 2007-03-23
I've installed the omnibook module.  But when I change the LCD brightness, nothing happens.  I type ' echo 1 > /proc/omnibook/lcd', but nothing changes, the brightness is still at max.  What's wrong?

P.S. I tried to load the Fnfxd module, and I get this error:
```

nticompass@nticompass-laptop:~$ sudo fnfxd
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel.

```

So, I tried to load the toshiba_acpi module and I get this error:
```

nticompass@nticompass-laptop:~$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.17-11-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device

```

How do I get FnFxd to work?

---

### Post by Michielc on 2007-04-29
I have a Toshiba a100-405 (phoenix bios) and have the exact same problem. I've also tried the omnibook module and tested almost all ectypes but nothing happens when i try to change the brightness.

update:
I did some more searching and found this: [http://slu.ms/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/](http://slu.ms/articles/2007/02/08/toshiba-linux-and-lcd-brightness-2/)
So I updated my bios and tried to change the brightness with: echo &#8220;10&#8243; > /proc/acpi/video/VGA/LCD/brightness

**And it works!** Also suddenly most of the fn+F# keys work as well (though some just crash my X )

---

