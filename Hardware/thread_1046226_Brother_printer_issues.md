---
title: "Brother printer issues"
date: 2009-01-21
forum: Hardware
---

### Post by alenis on 2009-01-21
I am experiencing the following problem with a Brother MFC 8840D printing text documents.
The first print is usually ok. The second print of the same document, unchanged or modified, is unreadable. See attached picture for an example.

[IMG]http://www.euridea.com/grafici/example.jpg[/IMG]

It usually happens with OpenOffice. It once happened with adobe reader too. Other applications seem to work fine. It didn't happened with windows. I always had this problem (I'm using Ubuntu since Dapper.)
Currently I am using Hardy and the driver in the repository, which, as far as I know, is the same provided by Brother.

The other issue is that printing images takes ages...however, the first problem is more serious.
Thank you for any possibile advice .

---

### Post by alenis on 2009-01-23
After a lot of experiments, it seems that the problem was caused by the msttcorefonts package. The printer works well on a fresh ubuntu installation or after removing that package. Unfortunately, I can't use any more fonts that are important in porting documents form one plaftorm to the other. I have no idea where the bug hides, wether in the Brother driver or in the msttcorefonts package.

---

