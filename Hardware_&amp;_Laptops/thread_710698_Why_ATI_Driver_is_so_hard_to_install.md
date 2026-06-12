---
title: "Why ATI Driver is so hard to install?"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by yardern on 2008-02-28
Officially ATI driver support RED HAT and SUSE.

Does this mean the installation on these two will be easy? And you can follow ATI's guide?
 
How different is Ubuntu from them?

---

### Post by Scarath on 2008-02-28
Its no different at all, the ATI drivers can be configured for Ubuntu too. 

Either use [Envy]("http://albertomilone.com/nvidia_scripts1.html") (it will do it for you and its how i got my ATI card working) or use the command:

```
sudo bash /path/to/your/ati-driver-installer.run --buildpkg Ubuntu/7.10
```

Obviously replace the relevant file path and release number ... it should work. It will create .deb packages for you to install.

Have fun.

---

### Post by Yellow Pasque on 2008-02-28
Follow method 2 of this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

