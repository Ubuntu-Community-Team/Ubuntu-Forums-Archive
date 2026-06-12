---
title: "synaptic tweaking xorg.conf no permission"
date: 2009-02-03
forum: Hardware
---

### Post by {Nabla} on 2009-02-03
Hi, I've got ubuntu 8.04 installed on my sony vaio, and I'm trying to tweak the synaptic touchpad scrolling settings. Since there seems to be no built in preferences for scrolling with the touchpad, I found this guide, but it is for ubuntu 6.06 and 6.01:

[http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/)

Anyway, I couldn't find one for 8.04 so I thought I'd follow it anyway, however I'm unable to edit the xorg.conf file, as it says I dont have the necessary permissions. I tried to change the properties to allow me to change it but it says the user is root, and I'm unable to change them.

Is there anything else I can do?

(btw, I AM the administrator and only user of this OS/laptop, so there must be some way?)

---

### Post by Yashiro on 2009-02-03
Open a Terminal
> sudo gedit /etc/X11/xorg.conf
Edit away. Don't break it. :P

---

