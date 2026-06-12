---
title: "Disable Suspend/Hibernate in Gnome?"
date: 2008-07-12
forum: Hardware
---

### Post by softtower on 2008-07-12
I bought Acer Extensa 5620Z as a gift for a friend. Ubuntu works like a champ on it, but after 7 hours of trying to get suspend/hibernate to work I want to call it a day - I give up.

However, I don't want her to try to use these non-working features by accident. How do I disable them in Gnome? I commented out required lines in /etc/default/acpi-support but gnome keeps showing "suspend" and "hibernate" as valid options.

How do I get rid of them?

--
Thank you.

---

### Post by sdennie on 2008-07-12
Hit Alt-F2, type gconf-editor and then navigate to /apps/gnome-power-manager/general and uncheck can_suspend and can_hibernate.

---

