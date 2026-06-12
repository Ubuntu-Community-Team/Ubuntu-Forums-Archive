---
title: "Automatic powerdown on shutdown/halt is not working."
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by BlackDex on 2009-01-14
Hello there,

I have a problem with a very very new computer.
Because of this i need to add acpi=off to the kernel boot options.

The problem now is that i when i select to shutdown Ubuntu, it doesn't power-down the computer, but halts at the shutdown screen, and i need to manually push the power-button.

Is there a way to have acpi=off and automatically power-down the computer??

Thx in advance.

---

### Post by BlackDex on 2009-01-14
I finally fixed this problem after a long long discussion on freenode #kernel.

The problem occured arround: "ACPI: Expecting a [Reference] package element, found type 0"

Here it loaded the thermal and fan modules.
After adding the two modules to the blacklist, and executed the following command:
```
sudo update-initramfs -k all -c
```

All was fixed.
It seems this for some reason triggered the ACPI part of the BIOS to crash or something i think.

Also, i had USB errors, they are gone also.

Anyway it is fixed now, with many thanks to enouf.

---

### Post by blackSP on 2009-04-24
Thanks. I have the same ACPI error during boot, will try this fix tonight.

---

### Post by blackSP on 2009-04-27
I still have this error that I believe many users see during boot-up.

I have searched for a solution but have not seen anything really.
Anybody any ideas?
Thanks!

---

### Post by 73ckn797 on 2009-05-22
I am getting the same message but it is not affecting operation or performance on my system. I am just curious about it. Has not occurred until Jaunty.

---

