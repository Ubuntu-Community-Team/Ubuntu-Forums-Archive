---
title: "How to Stop Dial-Up on Boot?"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by cquirke on 2005-05-21
Hi!

New to Ubuntu, and I have a couple of problems.  The main one is that it dials up the Internet connection as soon as it starts up, which incurs cost.  How to stop that?

The other issue is; how to edit the Grub boot menu, so as to change defaults etc.?

---

### Post by jasmuz on 2005-05-21
[QUOTE=cquirke]Hi!

New to Ubuntu, and I have a couple of problems.  The main one is that it dials up the Internet connection as soon as it starts up, which incurs cost.  How to stop that?

The other issue is; how to edit the Grub boot menu, so as to change defaults etc.?[/QUOTE]
 First off to disable the boot dialup use this:

[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

*Normally firefox saves items to the desktop, in any case specify the directory where it is downloaded to.

after you download do a:

#sudo dpkg -i filename.deb

After you reboot it will be available at the panel in System -> Administration

if at the install you are requested to satisfy dependencies, take notice of those dependencies, and download them, if you do not know how...do this 

#sudo apt-get install package

When you use the program deactivate the PPP daemon.

This will do the trick!

---

