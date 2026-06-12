---
title: "Dapper Desktop Amilo m1437g problems with Ati X700"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by petitof on 2006-06-02
I can't install Ubuntu because my live cd serverX doesn't start!
I have only wireless connection and my problem is that Ati X700 does't compatible with xorg.
I tried with vmware on Windows to install driver manually but I don't konow how to modify the iso of distro for future installation...
How can I install driver? Is there another way to install fglrx driver?

..please I'm dummies!!!
I love Ubuntu and I want use it!!!!!

Thank you!

---

### Post by goncoloz on 2006-06-07
sudo dpkg-reconfigure xserver-xorg
choose vesa drivers then
startx
install fglrx drivers with synaptic

i think that will be the easiest for you

---

