---
title: "[SOLVED] Releasing and Renewing Internet Connection"
date: 2008-09-16
forum: General Help
---

### Post by YldGuy on 2008-09-16
Whats the equivalent command in linux for ipconfig /release and ipconfig /renew in windows? ifconfig eth0 up and ifconfig eth0 down? I got confused at the man ifconfig looking at so many details.

---

### Post by john.nicholls on 2008-09-16
I don't know anything about Windows, but in Linux the commands for making and closing an internet connection are pon and poff respectively.

---

### Post by editrix on 2008-09-17
> **YldGuy said:**
> Whats the equivalent command in linux for ipconfig /release and ipconfig /renew in windows? ifconfig eth0 up and ifconfig eth0 down? I got confused at the man ifconfig looking at so many details.

If you're talking about switching from an ethernet card to a dialup modem, then yes, sudo ipconfig eth0 up/down.

pon and poff are for dialing a modem, if I recall correctly.

---

### Post by EmanresuusernamE on 2008-09-17
sudo ifconfig eth0 up/down

ipconfig doesn't exist in linux.

---

