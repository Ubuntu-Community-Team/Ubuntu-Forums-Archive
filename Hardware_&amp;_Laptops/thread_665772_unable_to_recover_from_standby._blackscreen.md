---
title: "unable to recover from standby. blackscreen"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by mikecicc on 2008-01-12
My Gateway4540GZ doesn't recover from standby, I can put the system to sleep, using the <FN> key + F3 (the sleep button) or through the system quit menu (top right of screen)..which all works fine, but when i attempt to recover the system from its standby state...it appears to be loading up, but my screen just remains black...i try the <FN> + F4 key combination which would be to export my video card to a projector or an external monitor..which doesn't help..

any ideas?


THanks in advance !!

---

### Post by erginemr on 2008-01-12
Hello,

Unfortunately this is a very common problem in Linux with some laptops (you will find lots of threads on suspend/resume problems in the forum). here is one that I have also been involved:
[http://ubuntuforums.org/showthread.php?t=608426&highlight=suspend](http://ubuntuforums.org/showthread.php?t=608426&highlight=suspend)

I think the solution lies inside the file:
/etc/default/acpi-support

and that you should focus on that file. Enabling / disabling some settings might save the day.

---

