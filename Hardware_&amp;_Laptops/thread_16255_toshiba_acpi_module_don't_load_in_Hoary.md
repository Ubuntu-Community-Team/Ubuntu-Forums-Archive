---
title: "toshiba_acpi module don't load in Hoary"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by mordecai on 2005-02-20
Hello, 

I have a toshiba satellite a50-110 and yesterday I upgrade from warty to hoary. Now i can't load the toshiba-acpi module:

$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.10-3-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device

Any help?

Thanks

---

### Post by markus on 2005-02-21
Hi,

I also own a toshiba laptop. I was trying to modprobe toshiba_acpi driver but it gave me the same error. But then I just typed modprobe toshiba-acpi and the driver was loaded and it worked.

I have only thouched the brightness and it works smoothly.

Just try it, although it should work  :grin: 

Good luck

---

### Post by mordecai on 2005-02-21
Hi,

I've tried with modprobe toshiba-acpi and I got the same error. 
I found there is a declared bug (#6197) in the last hoary upgrade with the tohiba_acpi module.

Thanks anyway.

---

### Post by josue on 2005-02-21
[QUOTE=mordecai]Hi,

I've tried with modprobe toshiba-acpi and I got the same error. 
I found there is a declared bug (#6197) in the last hoary upgrade with the tohiba_acpi module.

Thanks anyway.[/QUOTE]
 Same error here. Both with _ or -. Hoary aswell.
Hope it'll be fixed soon.

---

### Post by kelvin-kredens on 2006-05-08
Hello..

I'm having the same problem... Someone had found a solution??

Tanks...

---

