---
title: "Hypervisor with Hotswap"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by chuckmoney on 2009-08-10
Hey,

I'm looking to run both Ubuntu and Windows - at the same time, on the same system, with direct hardware access.  Now, I understand that this can't technically be done, however I have recently been considering a slightly altered approach.  My goal is to be able to have full graphics card support (I have a GeForce 9650m) but not have to wait on the time required to reboot either Ubuntu or Windows.  To do this, since I can't actually run both systems at the same time, I'm thinking of using a Hypervisor.  However, for this to work, I need it to be able to literally hot-swap between both running OSes, and to have full support for accessing the graphics card in Windows (and preferably Ubuntu, too), and I have had no luck finding a Hypervisor with these capabilities.  I understand I could just run Ubuntu in VMWare with Unity and accomplish much of the same functionality, and I have done this before, however I find VMWare to be really, really sluggish, and Tilda, my favourite application in the known universe, does not work in Unity at all!  Plus, since all I do in Windows is play games (I don't even have a browser installed) it seems like a lot of overhead just to be able to alt+tab between Evolution and Red Alert 3.

I have found one small glimmer of hope, but I have no idea if it'll work.  This RTOS seems to be able to run as a hypervisor and run multiple OS's and even swap between them on the local console, however I don't believe it grants Windows the needed access to the Graphics card, so if not, it will not work.

EDIT: Just noticed I forgot the link for the Hypervisor I found: [http://www.ghs.com/products/rtos/integrity.html](http://www.ghs.com/products/rtos/integrity.html)

Any thoughts?

---

