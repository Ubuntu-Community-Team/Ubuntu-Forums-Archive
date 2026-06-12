---
title: "PLease help with getting my nvidia driver to work"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by mattnexus on 2009-03-23
Hey I am using ubuntu on a machine without Internet. When I try to enable extra visual effects, it recognizes that I have a nvidia 9 series graphic card , it then tries to go to the website to download it but I don't have the Internet ,I tried downloading the nvidia driver off the website and transferring it to my pc on a usb,I then copied the file to my documents, but when I run the installation file it says you can not run the installation because x-server is running. How do I quit x-server to get this to work . Is there another driver I can use like a deb file please help,Many thanks.

---

### Post by inobe on 2009-03-23
you still need linux headers !

you will need an internet connection.........


:)

---

### Post by inobe on 2009-03-23
to add' if you had an internet connection you wouldn't need to do it manually, a connection to the net is a must.

---

### Post by nematodsa on 2009-03-23
use still need internet connection for headers, unless you are going to write them yourself, btw im using 6600 and this is what i did.

use the official guide to get your driver, there is a few good one. but the basic is:

safe the file in to your home folder [/home/"ur user"]
get in to console mode with ctrl+alt+f1
login in with ur username and pass
stop gdm with [sudo /etc/init.d/gdm stop]

install the new driver with [sudo sh "file name"]
edit xorg.conf to use "nvidia" driver instead of "nv"
get back to GUI desktop with [sudo /etc/init.d/gdm start]

after youset up, go to adjust your xorg configuration. copy the conf if you cant safe it, go in to console mode, paste the whole thing and safe. works well for me.

---

