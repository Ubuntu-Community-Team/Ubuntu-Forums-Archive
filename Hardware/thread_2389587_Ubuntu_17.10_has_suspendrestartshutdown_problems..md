---
title: "Ubuntu 17.10 has suspend/restart/shutdown problems."
date: 2018-04-18
forum: Hardware
---

### Post by automate-stuff on 2018-04-18
I am dual booting Windows 10 alongside Ubuntu 17.10. I am using [this]("http://www.dell.com/support/home/us/en/04/product-support/product/inspiron-15-7567-laptop/drivers/advanced") laptop.

Under Ubuntu, When I try to suspend, Ubuntu randomly hangs, sometimes it suspends and sometime it doesn't.......Same behavior with shut down and restart and also when I try to access Ubuntu settings....I updated the BIOS to the latest version...tried disabling Wayland ... No Luck.

Does this have anything to do with fastboot/securboot or UEFI ? What should I try next ? Will this be resolved with Ubuntu 18.04 ?


Many Thanks

---

### Post by Bashing-om on 2018-04-20
automate-stuff; Hello;

Try this: [http://iam.tj/prototype/enhancements/Windows-acpi_osi.html](http://iam.tj/prototype/enhancements/Windows-acpi_osi.html)
Changing the DSDT might work wonders.

[INDENT]maybe Yes
[/INDENT]

---

### Post by automate-stuff on 2018-04-29
This didn't help, While it allows me to restart and access settings without crash(when set to "Windows 2001"), the suspend function doesn't work....I tried many other distros with different DEs...no luck....Any other suggestion ? Many thanks

---

