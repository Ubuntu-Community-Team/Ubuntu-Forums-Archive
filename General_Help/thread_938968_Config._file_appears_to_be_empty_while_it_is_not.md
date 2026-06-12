---
title: "Config. file appears to be empty while it is not"
date: 2008-10-05
forum: General Help
---

### Post by kozlovsk on 2008-10-05
Hi!

I've had this issue before with fstab, now it happens with /ets/modules. When I do:

gedit /ets/modules
or
sudo gedit /ets/modules
or
sudo nano /ets/modules

the file appears to be empty, while opening the folder in nautilus and opening file by clicking on it displays the actual file contents. Probably it's not an issue at all and I just misunderstand something as a new user. Thanks for your help.

---

### Post by cariboo on 2008-10-05
You may be having issues with permissions /etc/modules should have a permission of 644.

Jim

---

### Post by kozlovsk on 2008-10-05
Thanks a lot, I'll try that. I've noticed that I can still edit them whith

sudo nautilus

and then just opening in gedit by clicking on them.

---

### Post by bodhi.zazen on 2008-10-05
it is "**/etc**" (with a c) and not ets (with a s)

---

