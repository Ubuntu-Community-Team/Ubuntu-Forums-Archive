---
title: "Canon BJC 1000 prints too small."
date: 2009-05-19
forum: Hardware
---

### Post by jasti on 2009-05-19
Recently on my old Dell Dimension 4100, I installed the ubuntu 8.04.  The new OS recognizes the printer but the size of printing is only about 1/16th of a normal page.  I shall appreciate any help I can get.

---

### Post by dje on 2009-05-19
Wow, i had one of these until not that long ago :D
Go to System >> Administration >> Printing and change the driver to the one for BJC 600, if i remember correctly this should correct the issue

dje

---

### Post by jasti on 2009-05-19
Thanks dje - You are dead on the center.  Changing the driver for BJC 600 makes the printer work like a charm.  My frustration for several days is now gone and I am much indebted. - Jasti

---

### Post by martin_h on 2011-07-28
This still works in 10.04 LTS on an old compaq presario B2000 

Excellent

---

### Post by blokkendoos on 2012-09-05
Still works on Ubuntu 12.04 and BJC-1000 printer :)

---

### Post by aikishugyo on 2012-09-06
> **blokkendoos said:**
> Still works on Ubuntu 12.04 and BJC-1000 printer :)

Hi, I'm the maintainer of the Canon backend on the gutenprint project.
I'd like very much to know if you are now using the BJC-1000 driver (and it works), or if you are still using the BJC-600 driver (because BJC-1000 driver does not work).

I haven't looked at the BJC series in detail yet, but if there is a problem with the BJC-1000 driver, I wil follow it up at once.

I assume you are not setting any resolution, so just using whatever is the default set in the gutenprint driver. What version of the driver is it? gutenprint 5.2.9 I assume?

If you use the BJC-600 driver, then it is from ghostscript I believe. I would lke to add proper suport to gutenprint also though, eventually.

When you use the BJC-1000 driver, it seems that it uses the resolution modes developed for the BJC-240, of which there are 5 (from 90x90dpi up to 720x360dpi). Can you try all of these and see if any of them work.

Regards,
Gernot Hassenpflug

---

