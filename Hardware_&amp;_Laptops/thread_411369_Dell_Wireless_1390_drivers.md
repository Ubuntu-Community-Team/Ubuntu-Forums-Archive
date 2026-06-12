---
title: "Dell Wireless 1390 drivers?"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by razr on 2007-04-16
I have a Dell e1405 laptop, and I just switched to Ubuntu, however, my Dell Wireless 1390 card refuses to show up. I'm new to the whole Linux scene, but am very excited about the idea of an open-source OS. Thanks for the help.

---

### Post by fulv on 2007-04-23
I have a Dell Latitude 620, with the same wireless card (1390) and found this to be incredibly helpful:

[http://sourceforge.net/projects/ubuntu-laptop/](http://sourceforge.net/projects/ubuntu-laptop/)

It installed very easily, and took care not only of the wifi issue, but of the touchpad sensitivity, as well.  It installs some other drivers, too, but I was not affected by those, either way.

I originally installed on Dapper, and then after upgrading to Edgy I had to install again.  Now my only question is whether it will work on Feisty, too.

---

### Post by chefweb on 2007-04-23
I think the Dell Wireless Card is based on a Broadcom -Chip. You can try to install the bcm43xx-package (sudo aptitude install bcm43xx-fwcutter)

---

### Post by staticsage on 2007-04-23
This thread worked for my Dell Precision M60 (same wireless card as you, it's Broadcom based).

[http://ubuntuforums.org/showthread.php?p=1071920](http://ubuntuforums.org/showthread.php?p=1071920)


Edit: This process is even easier: [http://ubuntuforums.org/showthread.php?p=2497734#post2497734](http://ubuntuforums.org/showthread.php?p=2497734#post2497734)
DarkN00b extracted the files from the firmware, packaged them and has a script to copy them to the proper location.

---

