---
title: "Nvidia driver issues"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by Der Blaue Soldat on 2007-02-21
Hi, im new. i am having trouble with my nvidia geforce 6200. so much so i have had to roll back to my old 64mb ati card. anyway to the point. i found this on the site and am having trouble with the installation. [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) when i go to enter the second command it asks for password. (i assume my user one) so i type it in and it says "sudo: dpkg-i: command not found" i could use some help.

---

### Post by taurus on 2007-02-21
There should be a space between dpkg and -i as in

```
sudo dpkg -i package.deb
```

---

### Post by sanone on 2007-02-22
Or just double click the .deb file in nautilus (the file browser)

---

### Post by Der Blaue Soldat on 2007-02-23
thanks

---

### Post by Derspankster on 2007-03-24
> **Der Blaue Soldat said:**
> Hi, im new. i am having trouble with my nvidia geforce 6200. so much so i have had to roll back to my old 64mb ati card. anyway to the point. i found this on the site and am having trouble with the installation. [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) when i go to enter the second command it asks for password. (i assume my user one) so i type it in and it says "sudo: dpkg-i: command not found" i could use some help.

Did you ever get the geforce 6200 card installed? If so, how? I cannot seem to upgrade to the 6200 from the geforce 4000 even though the driver should be indentical.

---

