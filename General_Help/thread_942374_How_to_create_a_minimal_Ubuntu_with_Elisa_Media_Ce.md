---
title: "How to create a minimal Ubuntu with Elisa Media Center only"
date: 2008-10-09
forum: General Help
---

### Post by jollyr0ger on 2008-10-09
Hi to all, I'm creating a personal distribution for my own media center.
I need to install a minimal Ubuntu, without all the unneeded packages, but just with Elisa media center packages, and with all its dependences (compreensive of all needed audio/video codecs).
How can I?

A lot of thanks

---

### Post by armageddon08 on 2008-10-09
Try using [Remastersys]("http://www.remastersys.klikit-linux.com/").
It is really good if you want to create your own "distro".
[Reconstructor]("http://reconstructor.aperantis.com/") is also good.

---

### Post by _sAm_ on 2008-10-09
I would downloaded the minimal Ubuntu image([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)), then installed what I wanted(guide: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)). 

Another way is to install Ubuntu Server and then follow the guide above. 

And I would go for XBMC([http://xbmc.org/](http://xbmc.org/)), looks very nice, is very fast, plays everything you want(even ISO files directly), and its easy to install and use.

---

### Post by jollyr0ger on 2008-10-14
I've tryed the XBMC live cd. It work correctely but I don't like a lot it.
I want to do these media center with Elisa.

There's a way to have that achived?
Istalling a minimal ubuntu, and then install elisa and elisa dependencies work not great. because not installing the gnome environment some hardware is not properly setted.

do you know another way?

thanks

---

### Post by Scheater5 on 2008-11-03
Firstly, I second the recommendation of xbmc, and I highly suggest you give it another go and thoroughly check out the library function as well as the MediaStream skin and the Aeon skin.  
But, if you check that out and still don't like it, then I also second the recommendation of remastersys, as it really makes it easy to make a distro just how you like it - you just have to set up your system how you're used to, and then make an iso out of it.  If you're not interested in making a distro out of it - that is, make an installable iso or img of your custom distro - then exactly what you're describing doing is a minimal install.  It gives you just a stripped, base install and apt so you can install only what it is you want. You said that "some hardware is not properly settled" - have you tried it with Intrepid?  And if it still doesn't recognize your hardware properly, please file a bug report on the hardware autodetection.  If so, at least for the time being, it may require some manual configuration on your part, like editing xorg or lirc.conf.  
A possible (although a bit ugly) workaround, if it is indeed installing gnome which "fixes" your hardware, would be to install gnome, and then uninstall it.  But I was unaware of the fact that Elisa could run without a desktop environment.  Xbmc only recently developed the ability to run without gnome.  You may indeed need to install gnome.

---

