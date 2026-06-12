---
title: "strange password root"
date: 2005-01-29
forum: Installation &amp; Upgrades
---

### Post by emamarro on 2005-01-29
I did change the password like
#sudo su
password: 
#passwd root:
password:

I got my root password changed correctly  when I use in consolle by command "su"
but when i try to use any tool (synaptics,network,etc..) still requires the user password...
I have tried several times to change it but still the same..ok in consolle not in tools..
Hope to get some help!Thanks
Ciaoo

---

### Post by Juergen on 2005-01-29
That's because menu-entries are still called with gksudo.
You have tho change this to gksu in the menu.

---

