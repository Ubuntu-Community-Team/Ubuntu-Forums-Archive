---
title: "error message"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by ukpooka on 2006-08-28
Hi i have just installed Ubuntu and it is going well, unfortunatly when i tried to install new programs from the add/remove list i get an error message which tells me to 'dpkg --configure -a'. logged in at the terminal and told that i need superuse access. im migrating from mac osx and know only a little. can any body please help in telling me why this has happened, how do i get superuser access and what to do to get this sorted. Many thanks in advance.

---

### Post by Rui Pais on 2006-08-28
Ubuntu use the same scheme as macosx. 1st user have admin (superusers) powers.
Just do:
```
sudo dpkg --configure -a
```
and enter your password (assuming you are logged as the 1st user or one with some admin rights)


PS, for a better application/package manager use synaptic.

---

### Post by ukpooka on 2006-08-29
Done and done, many thanks.:)

---

