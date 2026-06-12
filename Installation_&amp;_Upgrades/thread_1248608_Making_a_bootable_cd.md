---
title: "Making a bootable cd"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Sticks_uk on 2009-08-24
Afternoon all.

After struggling with gaming on ubuntu and I have zero hope I will be able to play Aion when it comes up I am forced to have a windows xp dual boot setup :( 

I have a couple of questions please

I am downloading win xp 64bit atm and was wondering what software I can use to burn a iso to a bootable cd. EDIT: FOUND SOME

Also I would like for ubuntu to load auotmatic when I dual boot so I have to manually select win xp when I want to play games how do I do that ? Can I install windows dual boot systems within ubuntu ?

thanks in advance

---

### Post by stlsaint on 2009-08-24
ok well you kow you can use a virtual machine inside ubuntu to run xp and play games just fine. but yes you can dual boot windows and ubuntu...
1. Use ubuntu livecd to create two partitions...1 for ubuntu....1 for xp
2. install xp to its respectable partition
3. install ubuntu to its respectable partition...but at the partitioner screen select manual and do the following...
4. make a partition and mount if for (/...root)
5. do another partition for mount to swap...

BETTER YET SEE HERE...THATS IF YOU WILL HAVE XP INSTALLED FIRST...

[http://oreilly.com/linux/archive/dual-boot-laptop.html](http://oreilly.com/linux/archive/dual-boot-laptop.html)

---

### Post by Sticks_uk on 2009-08-24
I was using virtual machine to run a theory test cd but it was a little choppy.

I never thoughe VM could run games a smooth as having win xp installed on a different partition ?

---

### Post by dandnsmith on 2009-08-24
> **Sticks_uk said:**
> Also I would like for ubuntu to load auotmatic when I dual boot so I have to manually select win xp when I want to play games how do I do that ? 
look at the menu.lst/grub.conf file - there will be a default OS indicated (numbered from the first) which you can change to make Ubuntu the default if it isn't already

> Can I install windows dual boot systems within ubuntu ?

I'm not sure what you intend by this question - but Windows maintains its own multi-boot system (and has a separate menu), and it *isn't* the easiest thing to get grub to do it all.

---

