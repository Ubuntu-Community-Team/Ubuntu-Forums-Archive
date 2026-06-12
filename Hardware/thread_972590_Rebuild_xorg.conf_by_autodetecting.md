---
title: "Rebuild xorg.conf by autodetecting?"
date: 2008-11-05
forum: Hardware
---

### Post by deadc0de on 2008-11-05
A little green here...

I uninstalled an old madwifi driver (make uninstall) and it looks like it destroyed my xorg.conf file - I don't know why or how but after rebooting it is absolutely basic now.

How do I rebuild it like it was after installing Ubuntu without reinstalling?  The installer autodetected everything - is there a way to do that again?

Thanks!!

---

### Post by pytheas22 on 2008-11-05
If you run this command it should create a new xorg.conf using auto-detected settings:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

You should probably backup your current xorg.conf first (even if it's not good, at least it starts X) just in case something weird happens:

```
cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.BACKUP
```

make uninstalling madwifi should not in any conceivable way have touched your xorg.conf file, however.  Are you sure you didn't change anything else?

---

### Post by victorsf on 2009-07-04
well, i had the same problem because the last package of ubuntu 8.04 or 9.04 have problems and the solution was more simply. reinstall xserver-xorg and remove completely the last version.
or other solution in console withouth graphic is 
```

```sudo /etc/init.d/gdm stop
```

```sudo X -configure 
```

```sudo cp /root/xorg.cong.new /etc/x11/xorg.conf
```

```sudo /etc/init.d/gdm start
And that is all

---

### Post by godwine on 2010-08-26
Additional thanks from someone who found this solution. I'll backup my xorg.conf before I start adding and subtracting monitors and TVs in future.

---

