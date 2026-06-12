---
title: "Editing Boot Loader"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by starscreamsghost on 2006-02-02
I am getting an error when I try to install linspire, after it installs completely and then it reboots, and needs to boot into linspire, I get to grub, load linspire and it gives me an error.  I am just wondering if this could be an issue with grub.  Is there a way to edit it and delete the old linspire entry and put a new one in, cause I think it may be trying to load an old one.....

---

### Post by aysiu on 2006-02-02
Does this have anything to do with Ubuntu? Are you trying to dual-boot Ubuntu and Linspire?

---

### Post by JoshHendo on 2006-02-02
Err, this has nothing to do with ubuntu unless you are booting ubuntu with linspire. Take a look at this forum: [http://forum.linspire.com/](http://forum.linspire.com/)

---

### Post by starscreamsghost on 2006-02-02
This has everything to do with ubuntu.........
I am dual booting and using Ubuntu's grub.  HOw do I edit grub, that is all I need the answer to.

---

### Post by taurus on 2006-02-02
Use either pico or gedit to do that...

pico /boot/grub/menu.lst
-or-
gedit /boot/grub/menu.lst

---

