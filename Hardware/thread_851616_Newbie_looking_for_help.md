---
title: "Newbie looking for help"
date: 2008-07-06
forum: Hardware
---

### Post by JLowe on 2008-07-06
I'm new to Linux and have installed Ubuntu on a Sony Vaio with a intel 82815 graphic's chipset.  I can't get the resolution any higher than 800X600.  How can I update the driver?

---

### Post by pytheas22 on 2008-07-06
Which version of Ubuntu are you using, and what is the output of this command in a terminal:
```

cat /etc/X11/xorg.conf?
```

(You can find a terminal under the Applications>Accessories menu.)  There are some well known issues with screen resolution and Intel graphics chips on Linux; this information will determine whether that's the root of your problem.

---

### Post by ppc_guy on 2008-07-07
Hey we all started out new @ one time or another! ;) Take a look here and see if it helps.. Let us know. Again a cat/paste is always good.

[http://cutecomputer.wordpress.com/2007/06/05/installing-nvidia-graphics-card-on-ubuntu/](http://cutecomputer.wordpress.com/2007/06/05/installing-nvidia-graphics-card-on-ubuntu/)

---

