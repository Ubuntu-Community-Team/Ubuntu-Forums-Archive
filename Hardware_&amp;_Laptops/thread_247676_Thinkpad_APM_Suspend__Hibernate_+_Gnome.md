---
title: "Thinkpad APM Suspend / Hibernate + Gnome"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by norm-linux on 2006-08-31
Hi everyone... I need some help.  Using APM, I have suspend and hibernate working on a Thinkpad 600e when I press the Fn-key combinations.

However, it doesn't work when I use the gnome power-manager menu or the buttons on the shutdown menu.  As far as I can tell, it's trying to use ACPI instead of APM when I use those two methods to suspend and hibernate.

At some point, I think I tried setting up ACPI but gave up and switched back to APM.  So how do I get gnome/gnome power-manager to call the appropriate APM commands instead?

Researching gnome power-manager, it appears that this link:

[http://mail.gnome.org/archives/gnome-power-manager-list/2006-July/msg00007.html](http://mail.gnome.org/archives/gnome-power-manager-list/2006-July/msg00007.html)

Confirms that:

# hal-get-property --udi /org/freedesktop/Hal/devices/computer \
>   --key org.freedesktop.Hal.Device.SystemPowerManagement.method_names

Suspend Hibernate Shutdown Reboot SetPowerSave

# hal-get-property --udi /org/freedesktop/Hal/devices/computer \
>   --key org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths

hal-system-power-suspend hal-system-power-hibernate hal-system-power-shutdown hal-system-power-reboot hal-system-power-set-power-save

# ls /usr/share/hal/scripts
hal-system-lcd-get-brightness  hal-system-power-set-power-save
hal-system-lcd-set-brightness  hal-system-power-shutdown
hal-system-power-hibernate     hal-system-power-suspend
hal-system-power-reboot

... are the scripts being executed by gnome/gnome power-manager.

These scripts in turn call:

# ls /usr/sbin/pmi
/usr/sbin/pmi

Which is an ACPI script.

So technically, I can just put some custom stuff into this script.  But there's probably a proper script or setting to fix this instead.  Any thoughts?

Thanks.
     -Norm

---

