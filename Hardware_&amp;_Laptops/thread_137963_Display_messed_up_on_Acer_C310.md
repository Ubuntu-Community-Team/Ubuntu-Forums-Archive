---
title: "Display messed up on Acer C310"
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by astanix on 2006-03-01
OK, I had a long post and a screenshot here, but apparantly the SS looked 100% fine.
I'll try to explain the problem:
When I boot into live 5.10 all the text displayed is kind of... weird.. like the colors are backwards.
All the backgrounds are black and the text is white... but all the text isn't actually there.

well, it IS there.. if I highlight it I can almost read some of it...

---

### Post by astanix on 2006-03-01
Fixed the problem using the vga=771 boot command thingy... so to boot linux on an Acer C310 you need to do this:
live acpi=off noacpi vga=771

hope this helps someone out there someday :)

---

### Post by prizrak on 2007-01-16
No such problem from 6.06 on.

---

### Post by astanix on 2007-05-19
So I'm using Feisty Fawn on it now and it seems to work ok most of the time.  If I leave it sit for more than a few hours I'll come back and the display will be messed up.  I have to restart X to get it to look right again.  I took a pic of what it looks like:

[[IMG]http://img124.imageshack.us/img124/5364/dsc00037qu3.th.jpg[/IMG]](http://img124.imageshack.us/my.php?image=dsc00037qu3.jpg)

---

