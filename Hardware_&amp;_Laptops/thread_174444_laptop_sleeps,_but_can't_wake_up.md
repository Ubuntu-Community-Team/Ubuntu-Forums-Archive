---
title: "laptop sleeps, but can't wake up"
date: 2006-05-11
forum: Hardware &amp; Laptops
---

### Post by Richard Roy on 2006-05-11
Hello,

I have a thinkpad X60s with Dapper ubuntu.
The laptop go to sleep, but does not wake up.
I read this bug in several places, but couldn't find a solution.

Does anyone know of a solution to the problem?

Thanks.

---

### Post by Richard Roy on 2006-05-12
Can someone please help ?

---

### Post by giociampa on 2006-05-13
I've got a T21, and the only way I've managed to get this to work is to use APM rather than ACPI to control the process.

I did this by adding "noacpi apm=on acpi=off" to the defoptions line in Grub's menu.lst file

Hope that helps

---

### Post by OPaul on 2006-05-14
Try turning DPMS off.

Add ```
Option         "DPMS"    "false"
``` to the Monitor section of your xorg.conf file.

---

