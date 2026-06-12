---
title: "Install NS2"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by tyelemou on 2009-01-14
Hello,
I have a difficult to install NS2 on Ubuntu 8.10
The error message : 

checking for X11 header files
can't find X includes
otcl-1.11 configuration failed! Exiting ...

Please help me
thank you

---

### Post by opscure on 2009-01-14
you need to enable the source repos in /etc/apt/sources.list

and then do an 

```
sudo apt-get install xorg-dev
```

This will get you the X11 header files.

---

### Post by sheshta on 2009-04-14
in my installation it says that
' tcl8.4.15 make failed ! Exiting '

what to do ?? anyone can help??

---

### Post by 666odio on 2012-06-09
just run 
sudo ./install 
that  will do

---

### Post by oldos2er on 2012-06-09
Please don't bump old threads.

---

