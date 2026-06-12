---
title: "Configuring xserver, get Error inserting battery.ko"
date: 2008-05-08
forum: Hardware
---

### Post by illume on 2008-05-08
I have tried to install a normal install of 8.04 ubuntu to an ancient pc of PIII 500Hz, 384Mb RAM

When I do "sudo dpkg-reconfigure xserver-xorg", after several screen I get this message

```
FATAL: Error inserting battery (/lib/modules/2.6.24-16-server/kernel/drivers/acpi/battery.ko): No such device
```

1. while booting, ubuntu will say that 
[ 0.000000]ACPI: no DMI BIOS year, acpi=force is required to enable ACPI

2. according to this post (i belive it's the same problem)
[http://ubuntuforums.org/showthread.php?t=761447&highlight=battery.ko%3Bxserver]("http://ubuntuforums.org/showthread.php?t=761447&highlight=battery.ko%3Bxserver")

I have tried 
A.add acpi=off to boot
B.blacklist battery, 
C.sudo apt-get remove acpi, 
D.check /usr/share/initramfs-tools/scripts/init-premount/

but none of above worked.

---

### Post by Abecedaria on 2008-06-09
Nothing but the crickets here in the ubuntu forums. I suppose it's because nobody has any idea how to solve the "battery.ko" problem that's keeping a lot of people from configuring their xserver. (Myself included) 

I've tried the exact same steps as you with no luck. The community really needs to come up with a better, more reliable way of setting screen resolution and drivers. Editing a xorg.conf file is baffling.

abc

---

