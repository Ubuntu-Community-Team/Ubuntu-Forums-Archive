---
title: "ubuntu 8.04, xp and samba"
date: 2008-07-12
forum: General Help
---

### Post by Loukisgr on 2008-07-12
hello,

i am new to samba and i am trying to create a domain controller. I have edited the /etc/hosts to

127.0.0.1 localhost SPEEDY.speedy.gr
192.168.1.2 SPEEDY speedy.gr

where SPEEDY is my computer name and speedy.gr is the domain i want to create. After that i configured the smb.conf

workgroup = speedy.gr
netbios name = SPEEDY

etc

but my xp client can't find the domain(to join) but can ping it.

what am i missing here?

Thanks in advance

---

### Post by Loukisgr on 2008-07-13
i forgot to mention that i created the username of the machine

useradd -g users -d /dev/null -s /dev/null machine$
smbpasswd -a -m machine$

still doesen't works

---

