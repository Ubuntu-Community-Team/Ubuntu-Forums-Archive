---
title: "dmidecode failing on a macbook 2.1 (amd64)"
date: 2011-05-15
forum: Hardware
---

### Post by fkbtuidrsfqssfdgimsg on 2011-05-15
Hi, 

I'm using squeeze/AMD64 on a MacBook 2.1, and dmidecode returns the following error : 

# sudo dmidecode
# dmidecode 2.9
# No SMBIOS nor DMI entry point found, sorry.
Indeed, issuing : 
# dmesg | grep DMI
[    0.000000] DMI not present or invalid.

I'm booting using refit, which chainloads grub2 with the following grub.cfg config : 

fakebios
search --set /vmlinuz
linux /vmlinuz noefi acpi=force video=efifb root=/dev/sda3
initrd /initrd.img

Any hints ?

---

