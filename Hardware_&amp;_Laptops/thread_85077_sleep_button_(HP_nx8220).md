---
title: "sleep button (HP nx8220)"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by pepster on 2005-11-01
My sleep button (fn f3) is not working under ubuntu breezy.

I can manually send the laptop to sleep (sudo pmi action sleep, sudo /etc/acpi/sleep.sh).

When I open System|Preference|Keyboard Shortcuts I can see the button shortcut is assigned to sleep. I tested the button by re-assigning it to another function - which works - which means gnome does get notified when the button is pressed.

I know the button work for at least one other person using the same laptop.

What else can I do? I have a multiple (KDE/GNOME) installtion - can this be a problem??

Thanks, Joseph

---

### Post by curley_sue on 2006-02-06
I'm completely new to linux (4 months use) but...
editing /etc/default/acpi-support worked for me on an HP pavilion ze2070:

$ sudo cp /etc/default/acpi-support /etc/default/acpi-support.bak
   
$ sudo vim /etc/default/acpi-support
           ^ or whatever editor

uncomment (delete the "#" sign) ACPI_SLEEP=true

save and restart...

by the way, do u know whether sleep locks the hard disk (actually - is it safe to carry a laptop arround in a case while in sleep mode?

---

