---
title: "remove loading bar at boot"
date: 2008-07-10
forum: General Help
---

### Post by giohappy on 2008-07-10
Hi list,
how can I remove the loading bar and replace it with the classical linuxian verbose boot?

I use Kubuntu 8.04

Thanks,
Giovanni

---

### Post by dracayr on 2008-07-10
hi,

in /boot/grub/menu.lst, remove the "splash" at the end of the ubuntu entry. You may also want to remove the "quiet" (or was it "silent"?) to get even more output.

dracayr

---

### Post by giohappy on 2008-07-10
thanks.

---

### Post by nikgare on 2008-07-10
You could install **startupmanager**, this will allow you to alter grub considerably

---

