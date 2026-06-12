---
title: "Slidescanner Minolta Dimage Dual II not working in Xsane"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by Jenske on 2006-07-26
Hi,

I can't seem to make Xsane work with my scanner (Dimage Minolta Dual II). I already found that I should be using the Avision backend (since Dual II is actually made by Avision).
I also found that there is communication between scanner and computer, though after one try the Xsane sends error messages.
It seems to me Xsane or it's backend isn't giving the scanner enough time to move the slide tray.
How and where can I adjust these timeouts in Dapper?

---

### Post by zxee on 2006-07-26
It seems more likely, having some experiance with sane/xsane, that the adjustments-if they can be made would be made in the specific backend for your device. Maybe there's a more recent backend? I would check out the man page for the backend. [http://www.sane-project.org/man/sane-avision.5.html](http://www.sane-project.org/man/sane-avision.5.html)
 And visiting the sane supported devices page shows that your film scanner has a status of "good" which translates as not yet complete.

---

