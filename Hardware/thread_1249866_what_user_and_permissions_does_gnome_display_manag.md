---
title: "what user and permissions does gnome display manager need?"
date: 2009-08-25
forum: Hardware
---

### Post by hockey97 on 2009-08-25
Hi, my gnome display manager fails at startup. I am thinking that it is a permission issue. 

I did chown -R root:root  with chmod 644. Where gdm is located under etc/init.d

any ideas on what permissions and user it needs. 

I also see mysql and other programs failing to boot at startup because of permission issues. The error said that user id 999 dosen't exist you don't have right permissions  Fail!!! 

So I am guessing that gdm must not have proper permissions. 

Does anyone know what permission that needs to be set? and how to do it?

---

### Post by tgeer43 on 2009-08-26
My /etc/init.d/gdm file is set like this:

root:root -rwxr-xr-x which equates to 755.

644 would prohibit all execute permissions.

tgeer

---

