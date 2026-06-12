---
title: "Trying to get the latest linux-uvc driver..."
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by kcy29581 on 2007-04-22
Hi all,

I'm trying to get the latest **linux-uvc** driver for my **Logitech Quickcam Pro 5000**, but the site is down (again).

This is the site I think I need: [http://developer.berlios.de/projects/linux-uvc](http://developer.berlios.de/projects/linux-uvc) but I have never ever (ever) seen it; every time I have tried for the past 6 months (been trying at least once a week) I always get the same error, that Firefox cannot establish a connection. And people on the Ubuntu forums seem to find the driver ok. :(

Am I using the wrong site? Where else can I get the latest driver?

Thanks for any help.

---

### Post by kcy29581 on 2007-04-22
I just realised I may have put this in the completely wrong forum... If there is an admin watching, please move to an appropiate forum! :???:

---

### Post by edm00se on 2007-04-24
When I go there I find the page perfectly fine (time now=3:30pm EST). I get the main page which looks exactly like the attached image. Ultimately, I use SVN (subversion) to anonymously checkout the necessary files. You may try doing so directly.

Install subversion:
```

sudo apt-get install subversion

```

then, to check out the files, you may wish to make a new directory into which you will place them (then cd into that directory) and:

```

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

```

Hope that works for you.

---

### Post by kcy29581 on 2007-04-28
Thanks, that did help.

---

