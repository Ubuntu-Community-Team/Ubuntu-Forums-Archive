---
title: "DLink card not working"
date: 2005-03-18
forum: Hardware &amp; Laptops
---

### Post by droogie on 2005-03-18
I just installed ubuntu on my laptop.  I have a dell insiron 8100.  I can't get the wi fi card to work.  It is a dlink dwl g630.  It uses the marvel chipset from what I've read.  Any ideas on this?

---

### Post by droogie on 2005-03-19
Does anybody know, it is tough to have to plug in every where I go.

---

### Post by alastair on 2005-03-19
I cannot help you much - I don't have this card. It appears to NOT have a Linux driver :

[http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless](http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless)

So you might have some luck with ndiswrapper :

[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

The pronlem might be figuring out the right windows .sys or .inf file to use.


A google search popped up some pages that might be of interest :

[http://www.linuxquestions.org/questions/archive/41/2004/12/3/267854](http://www.linuxquestions.org/questions/archive/41/2004/12/3/267854)
[http://ubuntuforums.org/archive/index.php/t-4200.html](http://ubuntuforums.org/archive/index.php/t-4200.html)
[http://article.gmane.org/gmane.linux.drivers.ndiswrapper.general/3646/match=dwl+-630](http://article.gmane.org/gmane.linux.drivers.ndiswrapper.general/3646/match=dwl+-630)
[http://article.gmane.org/gmane.linux.drivers.ndiswrapper.general/1908/match=dwl+-630](http://article.gmane.org/gmane.linux.drivers.ndiswrapper.general/1908/match=dwl+-630)

Good luck.

---

