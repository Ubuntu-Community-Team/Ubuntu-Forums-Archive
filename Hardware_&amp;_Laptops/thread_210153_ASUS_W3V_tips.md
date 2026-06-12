---
title: "ASUS W3V tips"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by mpokrywka on 2006-07-06
Official dapper kernels use libata acpi, which doesn't work on my ASUS W3V. Booting hangs (for a few minutes) on disk partition detection. To install dapper on notebook add **acpi=off** to kernel command line. After successfull install boot from hard drive with **acpi=off**. Libata acpi can be switched off separately from global kernel switch - follow this steps:

set libata module option:
```
sudo echo options libata noacpi=1 >> /etc/modprobe.d/options
```

rebuild initrd/initramfs to apply above change:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

Reboot without acpi=off, voila, kernel boots, acpi works. :smile: 

If you are running kubuntu (and kmilo) you probably noticed randomly showing  messages "Display changed: LCD on". This is kernel acpi problem, dapper **asus_acpi** module doesn't support ASUS W3V. I found patch on sf.net mailling list to correct that, see [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/17125](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/17125)

If you don't want compile kernel yourself (moderately easy: apt-get source linux-image-2.6.15-25-686; patch, make drivers/acpi/; make drivers/acpi/asus_acpi.ko) you can get patched module from [http://mikee.zalesie.eu.org/ubuntu/2.6.15-25.43-686/asus_acpi.ko](http://mikee.zalesie.eu.org/ubuntu/2.6.15-25.43-686/asus_acpi.ko)
Copy module to /lib/modules/2.6.15-25-686/kernel/drivers/acpi/, after reboot "Display changed" messages are gone.

One irritating thing is hanging xserver while trying to logout/shutdown. This can be cured by enabling **TerminateServer=true** in /etc/kde3/kdm/kdmrc:
```
sudo sed -i 's/^.*\(TerminateServer=true\)/\1/' /etc/kde3/kdm/kdmrc
```

HTH

---

