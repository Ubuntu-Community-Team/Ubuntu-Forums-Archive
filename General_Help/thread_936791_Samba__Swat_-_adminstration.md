---
title: "Samba / Swat - adminstration"
date: 2008-10-03
forum: General Help
---

### Post by Technofear on 2008-10-03
Hi

 have just installed Ubuntu studio.

I am trying to get samba configured so have installed samba and swat.

When I use the browser to go to [http://localhost:901/status](http://localhost:901/status) I am asked for a user - I use first user I created on the system (in user manager - this user has the right to administer the system). But - I only seem to get info about active shares. I am not able to create/administer shares.

---

### Post by polki@mac.com on 2008-10-03
I think it expects "root" as the user :-(

---

### Post by Technofear on 2008-10-03
When I try to enter root and the password - it returns to the webpage login prompt.

---

### Post by hyper_ch on 2008-10-03
root needs to be enabled to use SWAT.

An option would be to create another user and assign it then the root's UID...

---

