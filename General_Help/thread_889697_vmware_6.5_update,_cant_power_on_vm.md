---
title: "vmware 6.5 update, cant power on vm"
date: 2008-08-14
forum: General Help
---

### Post by malanco on 2008-08-14
hi guys, yesterday i updated my vmware workstation installation and when i tried to power on my xp vm i get this message,

Unable to change virtual machine power state: This product has expired and your virtual machine cannot be powered on.
Be sure that your host machine's date and time are set correctly.

There is a more recent version available at the VMware Workstation Web site: [http://www.vmware.com/info?id=4](http://www.vmware.com/info?id=4).


why??, it is the latest beta, i downloaded yesterday from vmware site, and i had my vmware workstation working before this, any clue?

Thanks!!

---

### Post by pjg864 on 2008-10-28
I have the same problem.I googled a lot and tired a lot--but it never worked. I almost can't stand with it!

Who can help me?

---

### Post by yqlong000 on 2008-11-01
I tried to modify the time to "2006-11-1", then it's ok.

---

### Post by darkdiver on 2009-01-15
It's possilbe to start vmware in past time without changing system time. Download [libfaketime]("http://www.code-wizards.com/projects/libfaketime/index.html"). Then you can start vmware like this:

```
faketime '2008-01-01 00:00:00' vmware
```

---

