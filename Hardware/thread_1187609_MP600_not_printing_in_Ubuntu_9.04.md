---
title: "MP600 not printing in Ubuntu 9.04"
date: 2009-06-14
forum: Hardware
---

### Post by veritas20 on 2009-06-14
Been all around the web, including this forum, to get the print drivers for my Canon MP600 installed. 

Links used/reviewed:
[http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)
[https://www.linuxquestions.org/questions/linux-newbie-8/mp600-printer-installation-problem-on-ubuntu-9.04-720450/](https://www.linuxquestions.org/questions/linux-newbie-8/mp600-printer-installation-problem-on-ubuntu-9.04-720450/)

Printer is not printing at all.  System recognizes the printer and "sends a test page", but the page is never printed.  Originally I had install the drivers for MP610 before I found the drivers for MP600.  It printed but in double vision.

Don't know where to start to debug the issue or what information to provide.  Any assist would be greatly appreciated.

---

### Post by veritas20 on 2009-06-16
anyone?

---

### Post by veritas20 on 2009-06-26
bump

---

### Post by kubug on 2009-10-14
Hi there, 

I know it's been a while since you started this thread, but I am currently trying to get this working for my mom, who just recently upgraded to jaunty. 

Here is the message I get after install the printer driver again:
```
The following packages have unmet dependencies:
  cnijfilter-mp600: Depends: libglib1.2 (>= 1.2.0) but it is not installable
                    Depends: libxml1 (>= 1:1.8.14-3) but it is not installable

```

It looks like the drivers don't "see" the newer packages. 

I will post when I get a solution.

---

