---
title: "a new install?"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by Therrol on 2005-12-09
Ok, so I installed ubuntu and hated GNOME. It's bloated and slow. Instead I installed fluxbox. I have decided that GNOME is interfering with my instal too much so I want to reinstall. If I do a server install can I just uncomment everything in the sources.list and apt-get install fluxbox?

one other quick question, I just used fdisk to delete an old NTFS partition and make a new linux partition. It never asked me if I wanted an ext3 or ext2, so I assume it's not formatted. How do I format this?

---

### Post by aysiu on 2005-12-10
[QUOTE=Therrol]If I do a server install can I just uncomment everything in the sources.list and apt-get install fluxbox?[/quote] Yes. You may need some other stuff, too, and those things you can apt-get as well. If you don't understand all the packages and what you might need, consider installing xubuntu-desktop and then fluxbox.

> 
one other quick question, I just used fdisk to delete an old NTFS partition and make a new linux partition. It never asked me if I wanted an ext3 or ext2, so I assume it's not formatted. How do I format this? ```
sudo apt-get install gparted
```

---

