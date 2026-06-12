---
title: "no suitable module for running kernel found"
date: 2008-10-06
forum: General Help
---

### Post by sheazar on 2008-10-06
During every bootup I get this errormessage "no suitable module for running kernel found" which confuses me everytime as the cumputer continue to boot like normal and runs just fine. 
Any ideas what the problem is?

---

### Post by olhat on 2008-10-26
I noticed that too last time i fired up this computer.  Everything seems to be like last week except for hibernation that has started to act up again (meaning snaFU). And I have absolutely no idea why but I found this one while I was googling for my problem.:guitar:

---

### Post by nickoe on 2008-12-31
It is related to VirtualBox. You have upgraded your kernel, and you need to recompile the module for VB.
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by kananman on 2009-09-02
* Stopping VirtualBox kernel module                                            
 *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

---

### Post by omlet on 2010-04-09
after sudo /etc/init.d/vboxdrv setup

i've got sudo: /etc/init.d/vboxdrv: command not found

---

