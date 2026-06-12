---
title: "Update Manager in Ubuntu 7.10"
date: 2008-09-20
forum: General Help
---

### Post by bruparel on 2008-09-20
I have two Dell laptops, Latitude D800 and Latitude D600 that I have installed Ubuntu 7.10 on.  I try to keep them identical in terms of configuration.
I have observed a strange behavior (or rather difference) between the two in Update Manager's operation.  The Update Manager on Latitude D800 is picking up all the available security patches automatically whereas D600 does not.  Even when I manually start Update manager on D600 and ask it to check for updates, it will NOT pick up the changes and merely reports that my system is uptodate and that Ubuntu 8.04 is available and I can update to it which I do not want to do.
Is there a switch of some kind that I have accidentally set that is causing this problem?
Another question, is there something really important that I should look at for upgrading to Ubuntu 8.04.  Upgrade from 6.10 to 7.10 was a no brainer for  me since it has much better support for wi-fi drivers which was a critical need for me.
Thanks in advance for your time.
Bharat

---

### Post by Sef on 2008-09-20
> Another question, is there something really important that I should look at for upgrading to Ubuntu 8.04. Upgrade from 6.10 to 7.10 was a no brainer for me since it has much better support for wi-fi drivers which was a critical need for me.

If you are happy with 7.10, then stick with it for now.   7.10 support runs out in April 2009.

---

### Post by sayakb on 2008-09-20
Goto System->Administration->Software Sources->Updates *tab*
Check that in both cases, you have your important and recommended updates enabled. Also, **check** the checkbox for Check for updates, and set auto installation options as per your needs.

---

### Post by bruparel on 2008-09-20
> **LinuxIsInnovation said:**
> Goto System->Administration->Software Sources->Updates *tab*
Check that in both cases, you have your important and recommended updates enabled. Also, **check** the checkbox for Check for updates, and set auto installation options as per your needs.

Thanks.  That was the problem.  Appreciate the help.

---

### Post by bruparel on 2008-09-20
Thanks.  I will stay with 7.10.  I like it a lot.

---

