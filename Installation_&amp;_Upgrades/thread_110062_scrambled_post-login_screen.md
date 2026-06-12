---
title: "scrambled post-login screen"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by blackadde on 2005-12-30
having some trouble.

after installing the latest amd64 variant of ubuntu, i get this screen immediately after logging in. excuse the poor photography.

[img]http://otersi.com/tempjunk/P1010113.JPG[/img]

on a 4400+x2, 7800gt, 2 gigs of ram.

mouse works fine.

---

### Post by guywmustang on 2005-12-30
I have the exact same problem... 

My system... amd x2 3800+, 2GB Corsair XMS, eVGA 7800gt with 2 dell 2005fpw.

My screen shots:
pre-login
[IMG]http://i7.photobucket.com/albums/y262/guywmustang/ubuntu1.jpg[/IMG]
post-login
[IMG]http://i7.photobucket.com/albums/y262/guywmustang/ubuntu2.jpg[/IMG]

---

### Post by blackadde on 2006-04-12
so, um, anyways, bump. :x

---

### Post by f0rgiv3n on 2006-04-15
Same thing here dudes, i have an amd64, and 7800gt and i get teh scrambled screen as well... what in the world is goin on? haha. BTW: beautiful lcd's :D

---

### Post by blackadde on 2006-04-16
nothing? :(

---

### Post by blackadde on 2006-04-19
tried dapper drake too. same problem. :|

---

### Post by Jason_25 on 2006-04-19
```

sudo nano /etc/X11/xorg.conf

```
Change driver from nv to vesa. Then ctrl-o, enter, ctrl-z.
```

sudo /etc/init.d/gdm restart

```

---

### Post by blackadde on 2006-04-19
worked like a charm. thanks!

---

