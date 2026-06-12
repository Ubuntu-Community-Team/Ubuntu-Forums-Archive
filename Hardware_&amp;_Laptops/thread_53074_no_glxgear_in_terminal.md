---
title: "no glxgear in terminal"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by tbasten on 2005-07-30
OK. I am really really confused. When i install xserver-xfree86 it wants to uninstall xserver-xorg etc. Which one do i want to use. Because when i run xserver-xfree86 i get and error saying /etc/X11/X is not executable but whne i run xserver-xorg i get GUI. So i really dont know what to do.

+ When i am in xserver-xorg there is no glxgears command

Any ideas

---

### Post by heimo on 2005-07-30
xbase-clients package has glxgears


 ```
sudo apt-get install xbase-clients (this probably should be already installed)
glxgear**s**

```

---

### Post by mo_x on 2005-07-30
I think you should use xserver-xorg which is the Ubuntu default. Remove xserver-xfree86. Maybe you have to reinstall xserver-org. Normally X is loaded at startup or you type startx from the console. glxgears is located in the directory /usr/X11R6/bin. Check if it is there and if /usr/X11R6/bin is in your path (echo $PATH).

---

### Post by tbasten on 2005-07-30
xbase-clients is installed. There is no glxgears in /usr/X11R6/bin/

---

### Post by heimo on 2005-07-30
I don't have glxgears in that directory either, I'm running Breezy.

But if I download this package:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fx%2Fxorg%2Fxbase-clients_6.8.2-10_i386.deb&md5sum=77340096728b18977efc294551ccbb90&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fx%2Fxorg%2Fxbase-clients_6.8.2-10_i386.deb&md5sum=77340096728b18977efc294551ccbb90&arch=i386&type=main)
I can see that glxgears is there. Could you reinstall that package? Or just download it and put glxgears there manually? (I think in this case it should work, providing that the version is correct.)

---

