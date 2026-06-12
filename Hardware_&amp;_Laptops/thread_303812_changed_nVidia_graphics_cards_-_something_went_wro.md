---
title: "changed nVidia graphics cards - something went wrong"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by RyanGT on 2006-11-20
I had an XFX nVidia GeForce 7600 GT that worked beautifully with Edgy but had some issues with Windows.  I returned it and got a GigaByte GeForce 7600 GS.  It is working beautifully in Windows, but this is my first boot into Edgy and it isn't working well (max resolution is 1024x768 and just scrolling on these webpages is slow).  What do I need to do to get Edgy to recognize that the new card is still nVidia and get things working well again?  I didn't have the proprietary nVidia driver installed before and like the idea of using what I think is an open one that comes with Edgy.

Thanks,

Ryan

---

### Post by David Corrales on 2006-11-21
In a terminal type **sudo dpkg-reconfigure xserver-xorg**. It'll allow you to pick good resolution/driver settings again.

---

