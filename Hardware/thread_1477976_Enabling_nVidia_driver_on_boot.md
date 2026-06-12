---
title: "Enabling nVidia driver on boot"
date: 2010-05-09
forum: Hardware
---

### Post by James2k on 2010-05-09
Im running Ubuntu 10.04 with an nVidia GPU. I want to enable my nVidia GPU during boot so it doesn't go into low resolution mode until the log in screen. I've been googling around and apparently I have to add something in my /etc/modules file, if so what do I add, and if not what must I do to enable the driver during boot so the Ubuntu boot screen isn't massive.

Thanks

---

### Post by 1wayjonny on 2010-05-11
I came to ask the same question but did many searches only to find this.

I have installed the Nvidia drivers and the font was HUGE so I edited the config file for DPI of 120 x 120 and it fixed that issue.

Working acceleration but when I boot as well its like 

640 * 800 with 8 bit color

How can our boot screens boot the normal resolution and color?

Thanks

---

### Post by James2k on 2010-08-24
I found this solved my problem with the large boot screen:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

