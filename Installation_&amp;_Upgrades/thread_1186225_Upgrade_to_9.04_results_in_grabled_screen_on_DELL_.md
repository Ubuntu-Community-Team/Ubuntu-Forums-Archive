---
title: "Upgrade to 9.04 results in grabled screen on DELL Optiplex 755"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by cyzak on 2009-06-13
Hi,

Today I upgraded my ubuntu from 8 to 9.04 using update manager.
Everything went fine but after restart there is nothing on the screen except for garbled stuff.

I read many threads on net about some graphics drivers and stuff but nothing concrete.

Its pretty horrifying. Please help.

Thanks

---

### Post by gradinaruvasile on 2009-06-13
Using the onboard graphics card?
you should try typing
sudo dpkg-reconfigure -phigh xserver-xorg
in the terminal. Then reboot

Else type 
lspci | grep V
in a terminal
what is the output?

---

### Post by cyzak on 2009-06-13
Hi,

Thanks for the response.

I tried following command.
sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20090613155515

Restrated. Same issue. Screen garbled.

lspci | grep V
00:02.0 VGA compatible controller: Intel Coorporation 82Q35 Express Integrated Graphics Controller (rev 02)

Thanks

---

### Post by gradinaruvasile on 2009-06-13
Try what i suggested to the other user...

[http://ubuntuforums.org/showthread.php?t=1181116&page=2]("http://ubuntuforums.org/showthread.php?t=1181116&page=2")

---

### Post by cyzak on 2009-06-13
Thanks a lot.
It worked. Now I can login.

Thanks again.

---

### Post by gradinaruvasile on 2009-06-13
Anytime

---

