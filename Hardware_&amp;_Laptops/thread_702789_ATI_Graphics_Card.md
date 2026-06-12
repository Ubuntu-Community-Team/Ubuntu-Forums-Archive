---
title: "ATI Graphics Card"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by commucom on 2008-02-20
Hey Guys,
I have just installed UBUNTU.

I have an ATI Radeon Xpress 1100 hyper memory gpu installed at present. It is 256mb dedicated and uses a further 256 from ram + 128 virtual.

First of all my screen appears to be stupidly bright, and i cannot find a option to turn it down, so i have to change physical screen settings to very low. This is not ideal, i am wondering if it has something to do with drivers. Also i am aware that ubuntu comes with desktop effects, when i try to enable them, it says it cannot. Does anyone know why this is, am i right in thinking this to is driver related?

Many Thanks

Adam

---

### Post by Yellow Pasque on 2008-02-20
The proprietary driver that Ubuntu installs does not support AIGLX, which Compiz uses. You can either try upgrading to the new Catalyst driver (using method 2 here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) ) or you can install xserver-xgl, but that method will probably screw up your video playback. To be honest, I would not do either of those things if I was you because your card probably isn't fast enough to run Compiz smoothly (not with ATI's sh!tty driver)

BTW, that's an awful lot of memory to give to an X1100. If it has 256MB on-board, I would try and stop it from taking any of my system's RAM.

---

