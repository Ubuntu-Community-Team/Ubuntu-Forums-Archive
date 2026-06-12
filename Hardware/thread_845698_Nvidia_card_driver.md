---
title: "Nvidia card driver"
date: 2008-06-30
forum: Hardware
---

### Post by guber112 on 2008-06-30
Hello,
I just got Ubuntu to work properly on my laptop with a Nvidia GeForce Go 8400M GS. I'm currently using the driver that Ubuntu installation picked but I'm wondering if I should install the Nvidia driver from the site? So that my laptop can have more resolutions.  Any advice? Also will it effect my "cube" or other features? Thank you..

---

### Post by sdennie on 2008-06-30
If the driver from Ubuntu is working for you, I don't recommend installing the drivers directly from the nvidia site.  There are few benefits to doing so for that card and it's best not to switch drivers unless you really must.

---

### Post by guber112 on 2008-06-30
Would it be possible to install it and uninstall if it doesn't work out? How could I also do this? Thanks!

---

### Post by sdennie on 2008-06-30
If you are new to Ubuntu, I *really* don't recommend installing from the website.  If you are looking for performance improvements, this link should work well on that card with compiz: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

If you absolutely must use the newest drivers, try: [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270).  You will probably see absolutely 0 difference in the driver except that it will break on kernel updates unless you follow this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573).  It will also break on some xorg updates and I'm not sure how to fix that.

I have no idea how to uninstall the driver and revert to the original.  Again, I recommend staying with the default driver if it's working.

---

