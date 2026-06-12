---
title: "HP Pavillion dv7-1175nr sound not working except for drums at startup"
date: 2008-12-27
forum: Hardware
---

### Post by adaykin on 2008-12-27
Hello, when I got this laptop, it had problems detecting sound out of the box. 

[Link to Laptop]("http://www.bestbuy.com/site/olspage.jsp?skuId=9053007&st=hp+pavillion+dv7&type=product&id=1218012194815").

The only sound that works is the drums at the startup, and they beat a lot longer than they should.

---

### Post by swudee on 2008-12-27
Hi

The specs don't show the chipset used.
My Compaq had a similar problem with the Intel 8201I (ICH9 Family) HD Audio chipset.
run the command lshw in terminal and see what multimedia chipset it uses, and if that isnot the one used, post it here.
If it is this Intel chipset, take a look here

[http://ubuntuforums.org/showthread.php?t=912896&highlight=no+sound+intel+ich9&page=3](http://ubuntuforums.org/showthread.php?t=912896&highlight=no+sound+intel+ich9&page=3)

The solution is to add a line to a config file, you will find it halfway down the page.

---

