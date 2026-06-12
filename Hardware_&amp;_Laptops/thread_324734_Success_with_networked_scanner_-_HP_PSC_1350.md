---
title: "Success with networked scanner - HP PSC 1350"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by torstenaf on 2006-12-24
I can now scan over the network using my laptop.  I have an Aopen Mini PC connected to my multi-function HP PSC 1350, which acts as a headless server on my wireless network.
[IMG]http://www.circuitcity.com/IMAGE/product/detail/son/EC.SON.VGNS560PB.2.jpg[/IMG][IMG]http://www.newlaunches.com/entry_images/221005/aopen_mini_pc.jpg[/IMG][IMG]http://www.zdnet.fr/i/edit/pr/2004/01/hp_psc_1350_enlarged.jpg[/IMG]

I followed the directions from an article at Linux.com with one change.
[http://www.atacom.com/program/print_html_new.cgi?&USER_ID=www&cart_id=3695373_71_142_206_80&Item_code=MIPC_AOPE_MI_00]("http://www.atacom.com/program/print_html_new.cgi?&USER_ID=www&cart_id=3695373_71_142_206_80&Item_code=MIPC_AOPE_MI_00")

When setting entering the user in **/etc/inetd.conf**, I put the user as ***saned*** instead of ***saned.saned***.

```
sane-port stream tcp nowait saned /usr/sbin/saned saned
```

Ubuntu does not have inetd installed by default, this package is called **inetutils-inetd**.  The sane utilities package is **sane-utils**.
```
apt-get install inetutils-inetd
apt-get install sane-utils
```

---

### Post by MrFSL on 2007-02-01
I can only assume you are refering to this article from linux.com

[http://tips.linux.com/article.pl?sid=06/10/13/1751234&tid=100&tid=13]("http://tips.linux.com/article.pl?sid=06/10/13/1751234&tid=100&tid=13")

---

### Post by kingjere on 2007-05-12
torstenaf

Thank you so much. The name in inetd.conf was the magic bullet that I needed to win this fight. I am grateful.

---

