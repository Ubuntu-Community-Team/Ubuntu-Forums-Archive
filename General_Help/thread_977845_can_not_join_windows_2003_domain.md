---
title: "can not join windows 2003 domain"
date: 2008-11-10
forum: General Help
---

### Post by eppo on 2008-11-10
ok, i've done this a few time with other distros, and it worked, i've connected 2 ubunut 8.04 servers, and a gentoo box to this domain, with no problems.
i used this site to set it up:
[http://www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html](http://www.ubuntugeek.com/how-to-integrate-windows-active-directory-and-samba-in-ubuntu.html)
this box i'm using this time is a ubuntu 8.10 box, i'm not sure if that makes a differences.
i can connect using the kinit command and it works fine, can do klist that works fine. but when i try to join the domain, i get this:
net ads join -U eppo@DOMAIN
Enter eppo@DOMAIN's password:
[2008/11/10 15:35:36,  0] libads/kerberos.c:ads_kinit_password(356)
  kerberos_kinit_password eppo@DOMAIN@DOMAIN failed: Malformed representation of principal
Failed to join domain: failed to connect to AD: Malformed representation of principal
anyone know what that means? i tried searching around and couldnt find much info.
thank for any help you might be able to give me.

---

### Post by nexus_6 on 2008-12-15
same here, any solutions?

---

### Post by Coreigh on 2008-12-15
Has it always been a 2003 domain? I recently upgraded from 2000 to 2003 and I am finding all kinds of extra (and annoying) security 'road bumps' in 2003.
I used Evolution with 2000 and it worked great and I can't even get it to connect to 2003, it seems to authenticate but then can't display anything.

I don't have it set up right now but I did have a 8.04 LAMP joined to the 2003 domain during testing.

---

### Post by albandy on 2008-12-15
Try using likewise instead of winbind.
Use the latest version from [http://www.likewisesoftware.com/](http://www.likewisesoftware.com/)
read the documentation, is well explained

---

### Post by englund on 2009-04-22
> **eppo said:**
> i can connect using the kinit command and it works fine, can do klist that works fine. but when i try to join the domain, i get this:
net ads join -U eppo@DOMAIN
Enter eppo@DOMAIN's password:
[2008/11/10 15:35:36,  0] libads/kerberos.c:ads_kinit_password(356)
  kerberos_kinit_password eppo@DOMAIN@DOMAIN failed: Malformed representation of principal
Failed to join domain: failed to connect to AD: Malformed representation of principal
anyone know what that means? i tried searching around and couldnt find much info.
thank for any help you might be able to give me.
I too had this problem and I got it working! See the error line with "eppo@DOMAIN@DOMAIN", that's one domain too much. I got it working when I removed the domain from the join command and let it use the default, like: "net ads join -U eppo"

---

### Post by jamessnell on 2009-06-19
Awesome, thanks!! Removing the domain from the join command did it for me.

I'm connecting from a 9.04 box to a Win2K3 AD server. Thx!

---

