---
title: "Installed and get error message on login"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by acyd burn on 2006-01-06
Ok, I installed Breezy today and when I go to log in with my account I created during setup, it gives me the error:

> Could not look up internet address for glacier [thats my comp name]. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding glacier to the file /etc/hosts

Log in Anyway | Try Again

I don't have internet except for a wireless card that isn't auto detected. Linksys PCIMCIA 802.11g +speedbooster

---

### Post by Ubluntu on 2006-01-06
Did you change a host file/entry, delete a localhost or 127.0.0.1? I believe the machine is just checking for that stuff at that point in time.

---

### Post by acyd burn on 2006-01-07
[QUOTE=Ubluntu]Did you change a host file/entry, delete a localhost or 127.0.0.1? I believe the machine is just checking for that stuff at that point in time.[/QUOTE]
I didn't do anything but install. localhost and 127.0.0.1 are still in /etc/hosts

---

