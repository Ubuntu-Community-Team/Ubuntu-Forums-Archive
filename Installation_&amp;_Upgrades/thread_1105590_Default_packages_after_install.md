---
title: "Default packages after install?"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by danking12 on 2009-03-24
Does anyone have or know of the location of a list of the packages that are installed by default when Ubuntu is first installed?

Thanks for any help provided!

---

### Post by aesis05401 on 2009-03-24
There are several ways to see what is installed on your machine.

Go to a terminal and try:
```

dpkg -l > installed
less installed

```

This info can be accessed through graphical interfaces as well.  

```

gksudo aptitude

```

Choose the 'Installed' option on the navigation tree located on the left side of your synaptic screen.

For a list by distribution try [packages.ubuntu.com]("http://packages.ubuntu.com/")

---

### Post by danking12 on 2009-03-24
> **aesis05401 said:**
> 
Go to a terminal and try:
```

dpkg -l > installed
less installed

```


This lists currently installed apps. I am looking for a list from a freshly installed system without having to install a system just to get that list.

> **aesis05401 said:**
> 
For a list by distribution try [packages.ubuntu.com]("http://packages.ubuntu.com/")

I think this lists all available packages for Ubuntu.

Thanks for the hand. I am just hoping that someone has a list and I don't have to do the grunt work.

Edit: I just want to add that I am looking for Ubuntu 8.10

---

### Post by rduke15 on 2010-01-19
I'm looking for the same information.I'm sure there is a list somewhere. But where?

---

### Post by rduke15 on 2010-01-19
I'm still looking for the "right" full package list, but in the meantime, I found a few lists by browsing [http://packages.ubuntu.desktop](http://packages.ubuntu.desktop). For example, for Intrepid:

[http://packages.ubuntu.com/intrepid/ubuntu-minimal](http://packages.ubuntu.com/intrepid/ubuntu-minimal)
[http://packages.ubuntu.com/intrepid/ubuntu-standard](http://packages.ubuntu.com/intrepid/ubuntu-standard)
[http://packages.ubuntu.com/intrepid/ubuntu-desktop](http://packages.ubuntu.com/intrepid/ubuntu-desktop)
[http://packages.ubuntu.com/intrepid/gnome-desktop-environment](http://packages.ubuntu.com/intrepid/gnome-desktop-environment)
etc.

---

### Post by zerwas on 2010-06-20
You can have a look at the download page, there are ".manifest" files, which include all default packages: [http://ftp-stud.hs-esslingen.de/pub/Mirrors/releases.ubuntu.com/lucid/](http://ftp-stud.hs-esslingen.de/pub/Mirrors/releases.ubuntu.com/lucid/)

---

