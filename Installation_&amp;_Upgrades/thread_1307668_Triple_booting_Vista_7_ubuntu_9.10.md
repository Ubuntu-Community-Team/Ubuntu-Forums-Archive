---
title: "Triple booting Vista 7 ubuntu 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Henr on 2009-10-31
Hi,

I'd like to edit the grub in my new ubuntu 9.10 to be able to choose at startup among vista windows 7 and ubuntu 9.10

currently I'm only able to choose either Windows 7 loader (which later gives me the option to choose between  vista or 7) & ubuntu

thanks in advance!

---

### Post by Herman on 2009-10-31
You only need to run 'sudo grub-mkconfig -o /boot/grub/grub.cfg', and GRUB 2 should detect all of your operating systems and add them to the boot menu automatically.
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

