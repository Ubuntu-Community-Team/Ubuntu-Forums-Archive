---
title: "ATI Radeon driver install"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by mlomker on 2005-09-07
I spent the last day trying to get the latest ATI driver to work on my Uniwill laptop, which has an ATI Mobility 9700 Pro adapter.  The driver that came with Hoary didn't work neither does Kopete, the ipw2200 driver...probably lots more stuff that I haven't used yet, but that's another story.

It turns out that [ there's a bug](http://www.rage3d.com/board/showthread.php?p=1333896065#post1333896065) in the latest (8.16.20) driver that will cause it to not provide full resolution on widescreen laptops--you end up with 1024X768 and there's nothing that you can do to change it.

I tried *many* different means of getting the driver installed.  The only way that worked was to follow this how-to, but use the older [8.14.13 driver.](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27) 

[How-to for installing the package.](http://bobbens.dyndns.org/howto.php?id=fglrx) 

[Use this link](http://www.objorkum.com/scripts/fglrxconfig/) instead of fglxrconfig to create your new xorg.conf file--it's a much cleaner copy

---

### Post by c0rderr0y on 2005-09-07
the latest ati driver works for me and my ip2200 worked right out the box....

---

### Post by mlomker on 2005-09-07
[QUOTE=c0rderr0y]the latest ati driver works for me and my ip2200 worked right out the box....[/QUOTE]

The video issue is acknowledged by ATI (at least with Samsung LCD's) and will be fixed in the next rev.  There are many threads regarding the ipw2200 driver not working, so consider yourself fortunate.

---

