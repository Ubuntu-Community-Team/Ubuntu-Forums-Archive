---
title: "and it says :
Msg &quot;Can't find the kernel sources. Please, install them and ru"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by patrick295767 on 2005-10-02
I am installing a program via .sh

I did make load
then ./install.sh
and it says :
"Can't find the kernel sources. Please, install them and run this program"


Is there a easy way to add kernel sources to go on the installation ?

Thank you very much

Pat'

---

### Post by tehwa on 2005-10-03
[QUOTE=patrick295767]I am installing a program via .sh
I did make load
then ./install.sh
and it says :
"Can't find the kernel sources. Please, install them and run this program"
Is there a easy way to add kernel sources to go on the installation ?
Thank you very much
Pat'[/QUOTE]
Try```
sudo apt-get install linux-kernel-headers
```from memory, this was the package that solved these errors for me.

---

