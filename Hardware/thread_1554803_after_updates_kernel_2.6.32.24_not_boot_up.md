---
title: "after updates kernel 2.6.32.24 not boot up"
date: 2010-08-17
forum: Hardware
---

### Post by tadaskr on 2010-08-17
Hello everyone. I just installed updates via update manager on ubuntu 10.04 and my kernel 2.6.32.24 not boot up just black screen and nothing, no keyboard caps lock light working, nothing. now I booted it with 2.6.32.21 kernel which was in boot menu, but it's running on low grafic mode. any ideas? How restore my system?

---

### Post by tadaskr on 2010-08-17
update: I back up my display drivers, but now ati catalyst control panel say that ati drivers isn't isntalled or not working. So I think there is big problem with ati drivers again

---

### Post by Fafler on 2010-08-17
Is apt upgraded the kernel to 2.6.32.24, it probably also upgraded the catalyst drivers to a version compiled with the headers 2.6.32.24. Atleast i know the Nvidia drivers work that way.

Try
apt-cache search catalyst 2.6.32.21
and install try installing the correct package. You probably need some options to force apt to downgrade. And every apt-get install something you do after that is going to break things again, and it wants to upgrade to the latest version. I don't if it's possible to blacklist a package to prevent it from upgrading, but google might be able to help you on that one.

---

