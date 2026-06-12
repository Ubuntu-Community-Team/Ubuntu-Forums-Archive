---
title: "Server add-ons"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by akross6966 on 2009-10-04
Hello.  Can anyone tell me if there is a way to add certain server features to the Ubuntu 9.04 Desktop (DNS, DHCP, APACHE, etc)?  I've looked in the synaptics software search, but i cannot install DNS, etc.  I know that there is an Ubuntu 9.04 server edition, but i'm not that good with command line...YET and was wanting to work on some special network setups here at home.  

Thanks in advance.

---

### Post by stlsaint on 2009-10-04
truly i recommend that you install the server edition and install the gnome desktop environment as server edition was made for the webserver: apace2, and the dns server setup along with the rest you requested.
if you absolutely must use desktop you can look into [Tasksel]("https://help.ubuntu.com/community/Tasksel") as it will give you all options to install exactly what you want!

---

### Post by akross6966 on 2009-10-04
Thanks for the reply.

no, i don't have to run the desktop edition.  I just didn't know that you could install a GUI such as GNOME.  Is it an option during install?

---

### Post by stlsaint on 2009-10-04
no to install gnome environment into server edition you need to run
```
sudo apt-get install gnome-desktop-environment
```

or again see taskel
also look into webmin for server admin controls

---

