---
title: "3COM PC Card works with Ubuntu but not Xubuntu"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by JeremyWorst on 2007-05-07
I have an old Toshiba Portege 3110CT laptop that had Ubuntu 6.10 installed and everything worked, including my 3Com LAN PC Card (model 3CXFE574BT).  I decided to see how much faster Xubuntu would be on the laptop and did a full install with a Xubuntu 6.06LTS CD I had.  Installing Xubuntu on this laptop is a little more involved than popping in the CD and rebooting, but I eventually got it installed and Xubuntu runs fine, but doesn't recognize the LAN card.  That is I don't see it under network-admin connections.  The card still works in other laptops that don't have Xubuntu.  Does Xubuntu have different hardware drivers than Ubuntu?  Any ideas or suggestions?  Thanks.
Jeremy

---

### Post by JeremyWorst on 2007-05-11
OK, I did some Yahoo searching and found the solution.  Apparently a file necessary to the operation of PCMCIA is not copied into the right directory when installing Xubuntu.  The file is config.opts, can be found in /usr/share/pcmciautils, but needs to go in  /etc/pcmcia.  After I copied the file there and rebooted, the LAN card was immediately recognized.  Here's a link to the original article, a blog entry posted 8/15/06:
[http://www.viraj.org/b2evolution/blogs/index.php/2006/08/15/](http://www.viraj.org/b2evolution/blogs/index.php/2006/08/15/)

It would be nice of this info made its way to the Xubuntu developers...

Jeremy

---

