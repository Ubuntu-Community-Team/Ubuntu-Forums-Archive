---
title: "gusty doesn't boot on ac power unless acpi=off, but boots on battery. ACPI bug?"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by rsferreira_rio on 2007-10-03
Hi;

Although Feisty runs fine in my Sony Vaio laptop on ac power or batteries, I can only boot to Gusty if the laptop is running on battery. 

If I try to boot with ac power the system crashes some seconds after GDM is loaded. And, if I boot on battery and, after the system is loaded, I plug the ac power, the system crashes instantly.

The only way to boot on ac power (or to plug it after boot on battery and keep the system running) is to set acpi=off in the kernel line. I've tried to check the acpi configs and events triggered by the ac power, but could not find any problem. I've also forced the crash plugging the ac power after system load to check system logs for that second, but nothing is registered.

What could be causing this? Is this an ACPI bug?

Regards,
Rodrigo

---

### Post by rsferreira_rio on 2007-10-28
This is confirmed in the latest Gusty release. Any ideas?

---

### Post by #Reistlehr- on 2007-10-28
Like many of us in the 7.10 hysteria, we too are experiencing bugs of such thorn binding magnitude, and it's really starting to hurt. Only thing to suggest is to file/confirm bug report, sit back and wait. It's not unusual expecially on laptops, to need to disable acpi, or apic, to get the laptop to function correcty.

---

### Post by rsferreira_rio on 2007-10-29
Hi;

The bug was already filled: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/148637](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/148637)

This is really strange because (i) the system runs fine on Feist, (ii) the system runs fine on Gusty if on batteries, (iii) the system runs fine on Gusty using the live CD. 

I've tested some beta releases and the final Gusty release with fresh installs (I keep Feisty in my first partition and have gusty in another partition) and the problem only exists in a installed version of Gusty if I plug the ac power.

I've tried to uninstall the gnome-power-manager, but that would break everything.

Regards,
Rodrigo

---

### Post by Neovos on 2008-02-11
You may be able to finesse acpi a little bit by looking here: 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

you may be able to specify the problem by trying some of the other acpi boot options instead of going straight to acpi=off.

---

