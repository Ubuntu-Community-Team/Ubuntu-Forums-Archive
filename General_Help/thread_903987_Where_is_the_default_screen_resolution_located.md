---
title: "Where is the default screen resolution located?"
date: 2008-08-28
forum: General Help
---

### Post by danbuter on 2008-08-28
For xfce, where is the default screen resolution listed? The graphical screen program just has default selected, without indicated what that resolution is and how I might change it. Thanks!

---

### Post by Dinghe on 2008-08-29
The default resolution is located in the xorg.conf file that is located in the /etc/X11/ folder.
more info on how to configure the file is found here: [http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html") 
But since you can only choose the default resolution option, i gues that you havent installed the videocard driver...
you normaly can install the driver via the restricted hardware driver option.
after that driver is installed you will be able to choose from different resolutions..
hope i was helpfull :)

---

