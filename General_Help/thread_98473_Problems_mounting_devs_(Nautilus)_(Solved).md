---
title: "Problems mounting devs (Nautilus) (Solved)"
date: 2005-12-03
forum: General Help
---

### Post by freakcode on 2005-12-03
When I try to mount CD/DVD or floppy MANUALLY (right clicking on the dev icon on nautilus) the following error appears:

"Unable to mount the selected volume.
Show more details...
Error: given UDI is not a mountable volume"

The devices are working right, I can always mount manually on a terminal, but this nautilus bug is freakin me :confused: 

I tried to change my fstab, to mount cdrom and floppy for users (adding user parameter), and I've done a chmod 777 on /media/cdrom and floppy. Then tried to mount, and the same happens...

Anyone knows why? What is this UDI-thing? :) 

Thanx

---

### Post by kosmic on 2005-12-03
Hum have you updated your breezy with the lastest updates ? because what you are reporting was a bug that was been corrected

---

### Post by freakcode on 2005-12-03
Upgraded pmount with Ubuntu Official Updates Repository.

Now it works fine, thanks ;)

---

