---
title: "Upgrade to Ubuntu Studio"
date: 2008-08-17
forum: General Help
---

### Post by colobix on 2008-08-17
Hey. I decided to upgrade from ubuntu 8.04 to ubuntu studio by using
sudo apt-get install ubuntustudio-desktop
Ubuntu studio looks cool on the screenshots and what I've read about it.

Is this a good idea and will everything work fine after the installation then?
I will not do it if it costs me bugs and lots of work to do with fixing up everything.

And another thing, what's the diffrence between the desktop and alternative installation?

---

### Post by cszikszoy on 2008-08-17
You can install ubuntu studio and nothing should break.  In much the same way that you can install KDE or Xfce "on top" or alongside of your original install, so too can you install ubuntu studio.  Because everything is basically just a package, it's very easy to remove later should you decide not to want it.

Check out this guide for more information:

[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/)

They tell you how to install the components of Ubuntu studio on top of an existing install.

---

### Post by colobix on 2008-08-17
Thank you very very much :)

---

### Post by phil the dill on 2008-08-18
Just be aware that installing UbuntuStudio will install a realtime kernel (it did for me, without any warning) and that your graphics drivers may not work when booting into the new kernel. I've also been advised in these forums that installing the appropriate graphics drivers into the realtime kernel can mess up the graphics install for the generic kernel.

---

