---
title: "no internet acess with hoary"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by unisol on 2005-04-22
i did a full install of hoary and everthing works fine except for my modem its a conexant 56k pci modem and ubuntu will not initalize it  is there any other software or drivers i can get to make my modem work any heip would be greatly appreciated

---

### Post by jdodson on 2005-04-22
[QUOTE=unisol]i did a full install of hoary and everthing works fine except for my modem its a conexant 56k pci modem and ubuntu will not initalize it  is there any other software or drivers i can get to make my modem work any heip would be greatly appreciated[/QUOTE]

try this site: [http://www.linmodems.org/](http://www.linmodems.org/)

---

### Post by unisol on 2005-04-22
im new to linux so i am not sure how to install drivers i got the drivers but i cant figure where to install them and what ia <arch>

---

### Post by unisol on 2005-04-24
i downloaded the drivers both tar and deb when i try to install hcfpcimodem_1.05full_386.deb it says in cannot find the package. also what is <arch>please someone help

---

### Post by ludi on 2005-04-24
[QUOTE=unisol]i downloaded the drivers both tar and deb when i try to install hcfpcimodem_1.05full_386.deb it says in cannot find the package. also what is <arch>please someone help[/QUOTE]
<arch> mean what kind of "arch" your system belong. Eg. i386, i686, K7, power5 and so on...
Have you tried this: cd /dir_of_you_saved_the_file dpkg --install your_package.arch.deb ?

---

