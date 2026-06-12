---
title: "Suspend on Acer Aspire 3620"
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by Arjunanda on 2006-05-02
What is the standard way of dealing with laptop ACPI features in Ubuntu (Gnome)? As I found nothing for this, I have installed kcontrol and klaptop. With these utilities I got some of the things to work, but still I have problems with suspend.

I have tested chmod o+w /proc/acpi/sleep
after which suspend works fine. But I do not know howto make this change permanently.

When I click on Setup Helper Application button in kcontrol/klaptop ACPI Config -tab, I get "KLaptopDaemon" "The ACPI helper cannot be enabled because kdesu cannot be found. Please make sure it is installed correctly" What is the package to install to enable kdesu?

The other options are also cryptic:
1. "to enable this application make the file /proc/acpi/sleep writeable by anyone every time your system boots"
2. "to make the KDE ACPI help application set-uid root"
How one can do these?

---

