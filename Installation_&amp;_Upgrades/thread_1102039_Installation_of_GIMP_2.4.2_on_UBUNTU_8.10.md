---
title: "Installation of GIMP 2.4.2 on UBUNTU 8.10"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by naveendv on 2009-03-21
I want to install gimp2.4.2 on UBUNTU 8.10.

I had uninstalled(removed) the newer version of gimp in UBUNTU8.10. Because the newer version of GIMP is not convenient for my use, Now I need to install GIMP 2.4.2.

How to achieve this...Please help me to come out of this problem.

---

### Post by taurus on 2009-03-21
How about version 2.4.5 from hardy?

[http://packages.ubuntu.com/hardy/gimp](http://packages.ubuntu.com/hardy/gimp)

---

### Post by drs305 on 2009-03-21
Here is a link from which I believe you can download the 2.4.2 deb. Note it is not an official repository:
[http://www.filehippo.com/download_the_gimp/]("http://www.filehippo.com/download_the_gimp/")

Welcome to the ubuntu forums.

---

### Post by Mark Phelps on 2009-03-21
You will need to get the following three debs:
- libgimpx.y_2.4.2-n...deb
- gimp-data_2.4.2-n...deb
- gimp_2.4.2...deb

When you install these, they will "break" gimp-gutenprint.  So, if you are using that, you will need to download those packages as well.

When you install the gimp packages, do the following:
1) install gimp-data
2) run "sudo apt-get install -f"
3) install libgimp
4) install gimp

Then, reinstall the gimp-gutenprint packages.

---

