---
title: "k3b wont write"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by shizow on 2005-11-23
i have a ibm t43
since some time k3b does not write cds
it prints an error:
cdrecord has no permission to open device
you may use k3bsetup2 to solve this problem

---

### Post by CrunchyDoodle on 2005-11-23
I suggest opening a terminal window and make yourself the super-user, and then run k3b.

sudo -s
Password: xxxxxxx
k3b &

Though K3B works for me as a regular user, I did notice a slew of errors saying it wasn't able to work as well as it should because it did not have the right permissions. As super-user, you have the permission to do just about anything.

Bye.     :cool:

---

