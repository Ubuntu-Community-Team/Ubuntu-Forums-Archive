---
title: "fglrxconfig don't save"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by kandahari on 2005-04-17
I installed binary driver after this: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

Everything works fine -ati driver loaded-, but I cannot save my fglrxconfig output in xorg.conf , if I run fglrxconfig -and I must run it because my tvoutput-
, it will save to the XFree86.conf *

how can I save my fglrxconfig output to the xorg.conf file?

I use Fedora too and there, all this save things work fine

---

### Post by colo on 2005-04-17
Well, what about just manually renaming the file, then?

---

### Post by kandahari on 2005-04-17
[QUOTE=colo]Well, what about just manually renaming the file, then?[/QUOTE]
 doesnt work ;(
Doesnt load than the X server, it write:load not a valid command in xorg.conf
and it have other problems too

:(
Can everybody save xorg.conf?this is only my problem?

---

### Post by mendicant on 2005-04-17
When I installed, it created everything for me correctly.  I never ran fglrxconfig, initially, and I think I remember seeing something about fglrxconfig not creating xorg.conf files correctly.  I would start with a working XF86Config-4, or use up to date drivers.  Also check out:

[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

where maqi says:

> 
And before anyone points out that the linked page is for xfree86 drivers - trust me on this one: the config works for xorg as well. I used this config on debian with instant success and no problems and when I finally ignored fglrxconfig and used it in ubuntu the drivers worked -finally!!! You will also notice that on that site it is expressly stated: DO NOT USE fglrxconfig TO GENERATE YOUR xorg.conf FILE!!!!!!!!!!! - at least the first time.


---

### Post by kandahari on 2005-04-18
but for me doesnt work correct
I dont understand why can not use fglrxconfig normaly
In Fedora Core this things worked fine

> 6. Edit your xorg.conf file using the guidelines above in this thread.
7. Test your X.org configuration:
a. Start X.org: 
why is ist so complicate?
In FC3 I must only run fgrlxconfig 
and all things is ok, here why not?

---

