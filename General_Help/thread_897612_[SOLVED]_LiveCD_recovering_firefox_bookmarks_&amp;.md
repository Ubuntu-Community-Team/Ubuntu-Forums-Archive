---
title: "[SOLVED] LiveCD recovering firefox bookmarks &amp;quot;Access Denied&amp;quot; help"
date: 2008-08-22
forum: General Help
---

### Post by SGoodyer on 2008-08-22
Couple days ago I did a fresh Windoze install and completely forgot to backup my firefox bookmarks. Luckily I remembered that my ubuntu had them but GRUB was overwritten (no getting on without installing it. not sure how to add it to windows boot menu).

Yada yada, I don't want to install GRUB because I just want Windoze to load right away (wine/cedega don't support 8.7/8.8 Catalyst drivers for my 4870 BOO :( ).

/home/user/.mozilla is secure and not sure how to open it. help?

---

### Post by y-lee on 2008-08-22
I would try to access my linux partition or drive from windows and copy the necessary firefox files to my windows partition. See [tools to-access linux partitions from windows]("http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html")

---

### Post by coffeecat on 2008-08-22
If you can't get into /home/user/.mozilla, this must mean that the live CD user has a different UID from the one in your HD install. Easy way around. Just:

```
gksudo nautilus
```in the live environment and you have root privileges in Nautilus.

[SIZE=3]Big BUT[/SIZE]

Is that Firefox 3 on your hard disc? If so, I have bad news for you. Simply copying bookmarks.html (I'm assuming that's what you wanted to do) won't work. That's what I used to do to synchronise my bookmarks around my various installs when using Firefox 2, but Firefox 3 uses a more sophisticated database system which I simply do not understand. When I copied my master bookmarks.html into the *.default folder of Firefox 3 they weren't picked up. You're going to do it the other way. It might work, but I think it won't.

It might mean re-installing grub after all to export your bookmarks from Firefox. Sorry.

---

### Post by SGoodyer on 2008-08-22
Thanks for the quick replies.

Linux Reader did it for me! :D

---

