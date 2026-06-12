---
title: "Is there no graphical mount tool in Ubuntu?"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by glue on 2007-01-03
I'm running Xubuntu and I'm having a difficult time mounting the CDROMs.  Actually, I'm not sure of their mount status - I just know they don't work. But, rather than ask for help with the mounting, I'm wondering why there's no graphical mount tool. There's one in DSL on the desktop. You just select what device you want to mount and set its mount status. You'd think a tool like this would be standared in an OS like Ubuntu which is about 15x larger than DSL.

---

### Post by angkor on 2007-01-03
Strange. CDs should be automounted when inserted. That's probably why there is no 'tool' for this in Ubuntu. (I assume they're supposed to be automounted in Xubuntu as well).

There was a gui (a gnome application) way in Dapper, however it is not there anymore in Edgy. I don't know if there ever was any in Xubuntu.

[https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/61728](https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/61728)
[http://ubuntuforums.org/showthread.php?t=260317](http://ubuntuforums.org/showthread.php?t=260317)

Maybe it'll be back or something similar in Feisty, supposed to be released in april 2007.



Edit:  You can try [this]("http://pysdm.sourceforge.net/"). I haven't though, so I don't know if it's any good or does what you want. I think it's only for hard disks. To install it, search for pysdm in Synaptic and mark the package for installation and apply or:

```
sudo apt-get install pysdm
```

---

