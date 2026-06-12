---
title: "Gigabyte HD4870 Graphics Card"
date: 2008-08-11
forum: Hardware
---

### Post by loseby on 2008-08-11
Cant get the card to work beyond 800x600.  Every time I boot I get "Ubuntu is running in low graphics mode" . I then select Radeon and continue to boot  I go to Hardware Drivers and enable the Radeon but get the following error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report."
Now if I run dpkg I get this message "requested operation requires superuser privilege"

I am new to linux

---

### Post by phidia on 2008-08-11
Prefix the dpkg command with "sudo" > sudo dpkg --configure -a

---

