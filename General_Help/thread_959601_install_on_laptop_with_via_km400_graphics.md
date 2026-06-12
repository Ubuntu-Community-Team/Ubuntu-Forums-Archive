---
title: "install on laptop with via km400 graphics"
date: 2008-10-26
forum: General Help
---

### Post by doug1212 on 2008-10-26
Just had a fun? afternoon installing Hardy (alternate cd) on an old Acer 1350 (via km400 graphics!), first off I had to add vga=773 (1024x768) to the end of the boot options line (f6) to see anything on the screen.

It seemed to install OK up until the reboot whereupon it just hung so I guessed that it was a graphics driver problem so I reset and booted to safe mode looked at xorg.conf and was left scratching my head as not much to see there anymore, googled around an found the answer was to find Section "Monitor" and add 
```
HorizSync       31.0 - 48.0
```
Found the info I required on the French Ubuntu forum, some good useful stuff over there.

Built Ralink drivers from source (serialmonkey) blacklist Hardy ralink driver, uninstalled gnome network manager and built Rutilt wifi manager tested WPA_PSK works OK, now have to find a way to turn the monitor back light off.

Hoping this information may be useful to anyone with similar ancient laptop and install issues.

BTW put XP sp3 on this machine 2 hours to download and it's like wading through treacle its so slooow.

Doug.

---

