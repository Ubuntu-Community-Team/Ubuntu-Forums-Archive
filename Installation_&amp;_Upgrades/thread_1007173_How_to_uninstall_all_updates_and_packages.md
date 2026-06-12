---
title: "How to uninstall all updates and packages??"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by gnlehcar on 2008-12-10
Dear all,

I am a new Ubuntu user and I have installed Ubuntu using a virtual box..
I give 4GB for Ubuntu to run..
However, I keep on updating and now it is fully utilized, and I cannot install anything now..
I would like to uninstall all the packages installed before, so that I can start all over again without installing Ubuntu again since it takes time..

I have tried "[FONT="Courier New"]apt-get remove *[/FONT]" and it gives me the following error:
[FONT="Courier New"]Reading package lists... Error!
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.[/FONT]

I really got no idea for this...><"
May anyone help me?? Thanks a lot!!

---

### Post by ibutho on 2008-12-10
Try running
```
sudo apt-get clean
```

---

