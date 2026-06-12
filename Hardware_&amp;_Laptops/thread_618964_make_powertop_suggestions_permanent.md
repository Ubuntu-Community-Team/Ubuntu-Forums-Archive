---
title: "make powertop suggestions permanent?"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by schmolch on 2007-11-21
Hello there,

im new to Ubuntu which i just installed on my Thinkpad X60T.

powertop makes quite a few suggestions which i all follow but i have to run it again after every boot.
Where would be the appriopriate place in Ubuntu to put theses commands to?
They all require root privileges.

---

### Post by 5-HT on 2007-11-21
Depends on what the commands are, but anything in /etc/rc.local will be run as root each boot after the daemons have started.

---

### Post by schmolch on 2007-11-23
That works, thank you!

---

