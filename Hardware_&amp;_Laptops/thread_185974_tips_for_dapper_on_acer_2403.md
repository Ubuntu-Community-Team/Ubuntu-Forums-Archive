---
title: "tips for dapper on acer 2403"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by Ugeek on 2006-06-01
I have just installed dapper on a freid's acer 2403 laptop. here are some tips.
it boots with acpi=off kernel parameter but does not recogniges bettery!!!

way out
________

use kernel parameter pci=biosirq instead of acpi=off
get the battery working

you can also get the correct resolution by installing

sudo apt-get install 915resolution and vbetools

then:

sudo vi /etc/default/915resolution

set:

MODE=auto

leave other parameters blank

enjoy.....

---

