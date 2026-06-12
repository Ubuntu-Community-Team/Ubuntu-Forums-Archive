---
title: "command-line install"
date: 2008-10-29
forum: General Help
---

### Post by hammeraxe on 2008-10-29
i have two quick questions:
1)how come the ubuntu command-line install takes up no more no less than 900MB !? :confused:
2)is there a command line tool for monitoring disk usage e.g. showing how much free space there is on each device?

thanks in advance

---

### Post by geirha on 2008-10-29
1) command-line install?
2) **df -h** will list the usage of all mounted filesystems, and the **du** command can be used to see how much space is used inside directories. Read its man-page. ```
sudo du --max-depth=1 -h -x /
```

---

### Post by hammeraxe on 2008-10-29
1) apparently i didnt make myself clear. i installed ubuntu from the alternate cd with the option to install command-line only. it seems weird that it takes up so much space
2)thanks

---

### Post by bodhi.zazen on 2008-10-29
If you want a smaller, minimal system use the Ubuntu minimal CD, JEOS, or debootstrap

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[https://help.ubuntu.com/community/JeOS](https://help.ubuntu.com/community/JeOS)
    [http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)


Or 

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

---

### Post by geirha on 2008-10-29
Ah, I haven't tried the alternate CD. Didn't know there was a command-line only option. 900MB does sounds a bit large ...

The following should list the installed size (%I) and package name (%p) of all installed packages (~i)
```
aptitude -F '%I %p' search '~i'
```

Append **| grep MB** to that command to only list packages that take more than 10MB.

---

### Post by hammeraxe on 2008-10-30
hmmm... i tried the mini.iso and installed command line only. yet the system still takes up 563MB after upgrading and localepurging.
well its better than 900MB but still seems quite a lot

---

