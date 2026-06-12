---
title: "[SOLVED] Problem in running 3d acceleration, in Acer TravelMate 6292"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by aria.radmand on 2007-12-20
Hi;
I'm trying hard to install VGA driver on my "[Acer TravelMate 6292]("http://global.acer.com/PRODUCTS/notebook/tm6292.htm")" laptop (in ubuntu 7.1 Gutsy Gibbon).

the first good result of my searchings, was this thread :
[Ubuntu 7.04 running on Acer TravelMate 6292]("http://ubuntuforums.org/showthread.php?t=497686&highlight=Santa+Rosa")

But it seems that he could not get what I want, from his laptop, too.
after googling more, i found this page: 
[Acer TravelMate 6292 and Fedora 7 Linux - Fishpool]("http://www.fishpool.org/post/2007/07/18/Acer-TravelMate-6292-and-Fedora-7-Linux")

He installed the driver successfully on fedora 7.0, i tried hard to understand what he said. (this is about one week i'm enjoying ubuntu not only by reading articles on weblogs about it! it means i'm very beginner in linux-ing.)
as he said in fishpool, i tried to install the new driver of my VGA (Mobile Intel Graphics Media Accelerator X3100) from [Here]("http://support.intel.com/support/graphics/sb/CS-010512.htm"), but ubuntu tells that i should first install the latest version of kernel, before installing the driver.
can anyone help me here step by step installing the latest version of kernel? and then the latest Intel driver!?

---

### Post by igknighted on 2007-12-20
That card should be fully supported out of the box... no additional drivers needed.  Is there any specific issue you are having that you are trying to install a new driver?

---

### Post by aria.radmand on 2007-12-20
> **igknighted said:**
> That card should be fully supported out of the box... no additional drivers needed.  Is there any specific issue you are having that you are trying to install a new driver?

I have some little problem:

1. I can not activate Extra/Normal Visual effects in the "Appearance Preferences"...
2. the pc crashes, when i am watching videos... 
plus that the quality of videos is really poor in compare with MSwindows.
3. When moving windows, it's obvious that there is a problem with the graphic drivers. (there is lags)
& ...

(resolution is set to maximum: 1280*800)

---

### Post by aria.radmand on 2007-12-20
and for your information, (in fact i have no idea what does this command do!?) the result of typing "compiz" in terminal is:

```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
```
can you tell me the meaning of these? please?

---

### Post by aria.radmand on 2008-05-24
[5 Months Later...]

Now I'm using Ubuntu Studio 8.04 , and it's working very good with everything and doesn't need to install any driver or anything. ;-)
and if anybody have the same problem, I recommend [Ubuntu Studio]("http://ubuntustudio.org/").

---

