---
title: "Current Asus Z87 Mainboards + Ubuntu (Z87-PLUS / Z87I-PRO)"
date: 2013-12-07
forum: Hardware
---

### Post by WeberMax on 2013-12-07
Hello,

i would like to ask if someone running Ubuntu/ Linux at such mainboards and how it works? Thank you!

Best regards

---

### Post by oldfred on 2013-12-09
Most users posting seem to be laptops.

 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

[http://openbenchmarking.org/s/ASUS%20Z87-PLUS](http://openbenchmarking.org/s/ASUS%20Z87-PLUS)

---

### Post by WeberMax on 2013-12-19
Hello,

thank you for your reply!

In the mean time a build a new system, based on a Asus Z87-Plus. Evertyhing works for me.
Xubuntu 13.04 does not recognize the on board sound, Ubuntu 13.04 do.

Best regards

---

### Post by oldfred on 2013-12-19
Glad to hear it worked.

Do not understand sound issue. The underlying system is supposed to be that same and the difference between Xubuntu & Ubuntu is the graphical display and default apps. If you want Xubuntu you can install it into Ubuntu. Or just install the gui without the different default applications.

I typically do not like having two installs in one as if then you like one it is very difficult to remove the other. You easily install with meta-package, but cannot uninstall the meta-package but have to choose each app.

       The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)

sudo apt-get install xubuntu-desktop

      
 XFCE installs XFCE only while xubuntu-desktop all other programmes
sudo apt-get install xfce4 xfce4-goodies

---

