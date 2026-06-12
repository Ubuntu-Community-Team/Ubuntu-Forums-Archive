---
title: "change home directory"
date: 2008-09-13
forum: General Help
---

### Post by amin_inb on 2008-09-13
Hi there

I want to change my home directory (/root/) to some other directory (/mnt/my-new-home) 

any idea ?

My idea :)

rm -r /root/
ln -s /mnt/my-new-home/ /root


it works but I don't think it is a good idea!

---

### Post by Frantic225 on 2008-09-13
just sudo vi /etc/passwd and edit it there, or use usermod

---

