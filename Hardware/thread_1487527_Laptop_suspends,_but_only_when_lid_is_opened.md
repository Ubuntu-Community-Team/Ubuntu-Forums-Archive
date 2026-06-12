---
title: "Laptop suspends, but only when lid is opened"
date: 2010-05-19
forum: Hardware
---

### Post by naschas on 2010-05-19
Hi everyone,

I am battling with my HP nx7300. I thought suspend was not working as it did work perfectly in 9.10 after upgrading to 10.04. I realised though that the system suspends when closing the lid, but only after opening it. It appears as though the system is only suspending once the lid button has been pressed and released, instead of just being presses down.

Any help would be appreciated!

Thanks

---

### Post by martintremblay on 2010-06-11
I have the exact same problem on an HP laptop

Hibernate/suspend will work fine if selected from the shutdown menu
but when the lid is closed, nothing happens...

However, when the lid is re-opened, my laptop suspends or hibernates (depending on what is selected in System-Preferences-Power Management!

It appears to be an issue with the way ACPI recognizes the lid is open.
See here: [http://ubuntuforums.org/showthread.php?t=406250](http://ubuntuforums.org/showthread.php?t=406250)
I am reluctant to try any of the suggested code, as my system worked fine in 9.10 and earlier. I believe it's one of the lines in ACPI-support  file in 10.04 that is incorrectly set up for us. I'll be trying to modify my ACPI file and if I have any success will post results

---

### Post by martintremblay on 2010-06-12
Changes to etc/default/ACPI-support did not help.

I have found if I boot into an earlier Kernel, this problem goes away. I can select 2.6.31-20-generic from GRUB menu (instead of 2.6.32) and have no Hibernate/suspend/sleep issues.

I attempted to copy the ACPI-support file from 2.6.31-20-generic in 2.6.32, but it made no difference.

I believed this problem is ACPI-support related as making changes to ACPI-support file  and "power management preferences" causes the problem to behave differently (ie//no hibernate/suspend at all, or only partial hibernate/suspend)

Still working on it... appears the largest "group" of folks with a similar issue are congregating here: [http://ubuntuforums.org/showthread.php?t=1469340](http://ubuntuforums.org/showthread.php?t=1469340)

---

