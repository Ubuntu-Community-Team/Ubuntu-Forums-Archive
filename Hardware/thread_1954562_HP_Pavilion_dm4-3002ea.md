---
title: "HP Pavilion dm4-3002ea"
date: 2012-04-08
forum: Hardware
---

### Post by ariskk on 2012-04-08
I've installed ubuntu 11.10 (64-bit) on my HP Pavilion dm4-3002ea ([http://h40059.www4.hp.com/uk/homelaptops/product.php?id=A8J29EA&experience=direct](http://h40059.www4.hp.com/uk/homelaptops/product.php?id=A8J29EA&experience=direct)) . All work ok except the laptop fan always been on and hot air comming out of it. I believe this to be due to the graphics card.

This laptop has a Radeon graphics card (HD 7470M). But on Preferences => System Info I see the driver been used to be "Intel® Sandybridge Mobile"

When activating the  "ATI/AMD FGLRX driver" using the "Additional drivers", the fan stops working and no more hot air comes out of it but the system falls back to compatibility mode, i.e. gnome 3 is in "Fallback" mode.

I've tried downloading and installing the amd/ati drivers from their web site but it just rendered ubuntu unusable and I had to reinstall.

Any ideas how to make it work without overheatting?

Thanks,

Kostas

---

### Post by ariskk on 2012-04-08
wow, this thread is so active, bump!):P

---

### Post by Redblade20XX on 2012-04-08
See if this wiki will help with the proprietary drivers:
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
I've found out that usually the prop drivers have better control over fans.

- Red

---

### Post by ariskk on 2012-10-13
I accidentally bumped on my own thread today as I was searcjing for the same issue :P

Thanks for the link, I actually run these 2 commands:

sudo aticonfig --initial
sudo aticonfig --overlay-type=opengl

And now (after 5 months of using ubuntu without graphics acceleration on!!!) I am finally using gnome not in failsafe. 

Which begs the question: why isn't that done automatically when I installed the driver???

---

