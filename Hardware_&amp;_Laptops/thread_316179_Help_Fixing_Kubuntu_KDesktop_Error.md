---
title: "Help Fixing Kubuntu KDesktop Error"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by TheBigBakedBean on 2006-12-10
I just installed kubuntu edgy on a laptop that barely scrapes by the minimum hardware requirements.  The initial install went great, and everything was running properly.

Then, I enabled extra repositories by editing /etc/apt/sources.list .  After running the aptitude update, I installed gstreamer plugins to enable support for windows audio formats, as well as the xine plugins to enable support for windows video formats.  I then installed msttcorefonts.

Everything ran fine, all updates and installations completed successfully, but now when I boot into KDE I get the following error:
"The process for the file protocol died unexpectedly."

It's obviously related to the extra repositories, gstreamer plugins, or installed fonts.  Is there a terminal command that will allow me to get some more information about the error?  Has anyone else run into this that could help me figure out what is causing this error and if the large dropoff I've noticed in overall speed has been a direct result?

Aside from removing each installed item individually to see which package causes the error, is there an easy way to determine what is causing this error?

---

### Post by TheBigBakedBean on 2006-12-11
Sorry to bump this soon, but I've seen a few others mention this same problem and I wanted to be sure to get assistance on this topic. ](*,)  Thanks!

---

