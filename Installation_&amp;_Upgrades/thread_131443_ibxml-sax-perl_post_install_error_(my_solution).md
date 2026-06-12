---
title: "ibxml-sax-perl post install error (my solution)"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by ldarby on 2006-02-16
When I try to install libxml-sax-perl I get this error.
E: libxml-sax-perl: subprocess post-installation script returned error exit status 255

After much wailing and searching the net and digging through documentation, 
I found that whin I used cpan  to install a differnt module, I had put another version up while "resolving dependencey issues"
I went to this folder:   /usr/local/share/perl/5.8.7/XML/SAX/ and deleted the two items there.
After that, it installed without errors.

---

