---
title: "Cannot get power button on Dell laptop recognized"
date: 2006-04-20
forum: Hardware &amp; Laptops
---

### Post by gobucks on 2006-04-20
I've got a Dell Inspiron 5160 that has a power button at the very top of the keyboard.  Prior to installing Breezy, Windoze used it quite nicely.  Now it appears that the button is not even recognized.  I've tinkered with the powerbtn.sh script, and from all indications it's not getting run at all.  ACPI is installed and running, along with gnome-power-manager which has the action for the power button set to shutdown.  If and when the power button works, I'd like to configure it so that it asks for the shutdown action, like that in "gnome-session-save --kill".

There are no entries in the /var/log/acpi that indicate that the power button was pressed.

Any help would be appreciated.

---

### Post by gobucks on 2006-04-22
Bueller?

---

