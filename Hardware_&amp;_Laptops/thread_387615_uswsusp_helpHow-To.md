---
title: "uswsusp help/How-To?"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by mattyj on 2007-03-18
Hello,

I am trying to get uswsusp figured out to suspend to disk on my desktop running a recent Edgy install  as I have a new Dell D820 laptop on the way and it would be really nice to be able to suspend.

I have found several resources for using uswsusp which seem to make me think it works well:

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

[http://www.linux.com/article.pl?sid=07/02/02/2117209](http://www.linux.com/article.pl?sid=07/02/02/2117209)

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

When I install the package in the Edgy universe file and try 

s2disk

I get:

suspend: Could not stat the resume device file

How do you configure the options for uswsusp?  I can't find any documentation on the home page for the development.

Could somebody in the know do a brief how-to or point me toward one, googling seems to have come up short...

Thank You.

---

### Post by StraNNicK on 2007-03-21
Try use it:
$sudo su
#s2disk `fdisk -l | grep "Linux swap" | awk '{print $1}'`

---

