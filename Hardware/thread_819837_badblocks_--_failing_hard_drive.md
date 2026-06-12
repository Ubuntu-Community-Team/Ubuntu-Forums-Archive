---
title: "badblocks -- failing hard drive?"
date: 2008-06-05
forum: Hardware
---

### Post by le_vainqueur on 2008-06-05
I ran badblocks on my hard drives last night because one of them spontaneously can no longer be mounted in XP or Ubuntu.  The result on the hard drive with problems was that badblocks took all night to run, and the following was the output.

> 
.
.
.
9476681 9476681/      199141707
9476682 9476682/      199141707
9476683 9476683/      199141707
9476684 9476684/      199141707
9476685 9476685/      199141707
9476686 9476686/      199141707
9476687 9476687/      199141707
.
.
.

a whole lot of that showed up!

Anyway, I don't really know what that means.  I don't think it ever finished because it never said anything like "found # bad blocks" or anything.  Thoughts?

---

### Post by le_vainqueur on 2008-06-05
New development:

I tried to reformat the drive using gparted, but it was not possible.  The error I received was when it tried to create a new filesystem.  It said that there was "no such file or directory"

I'm guessing that's a bad sign, but does that mean the drive is toast?

---

### Post by le_vainqueur on 2008-06-09
*bump*

---

### Post by ardvark71 on 2008-06-09
Hi...

I'm not sure if it will help, but you can try software that claims to repair the bad sectors. However, if the heads are touching and scratching the platters, I don't think even these (programs) will help. It all depends on what your drive is doing.

Here is a list here, I don't know if you can boot from them or not, you will have to see...

[http://www.freedownloadscenter.com/Best/bad-sectors.html](http://www.freedownloadscenter.com/Best/bad-sectors.html)

I've not tested or used this software, so "buyer beware." ;)

Best Regards...

---

