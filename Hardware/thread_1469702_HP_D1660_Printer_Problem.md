---
title: "HP D1660 Printer Problem"
date: 2010-05-02
forum: Hardware
---

### Post by Ompsksch on 2010-05-02
What worked fine on 9.10 doesn't on 10.4. Job shuts down.

---

### Post by mr_niceguy on 2010-05-03
I'm getting exactly the same problem.

The printer installs but any time you print the job quits before the printer does anything. And if you look at the print queue it is empty.

---

### Post by mr_niceguy on 2010-05-03
I had to use the automatic installer from HP.

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Removed the printer first.

Had a little weirdness at the end of the process. Basically the drivers were successfully replaced but the install gui did not allow me to "Add Printer" and I had to quit at that point.

Running "sudo hp-setup" allowed the process to complete.

---

### Post by Ompsksch on 2010-05-06
Thank you Mr. Nice Guy. I guess I'm not that technical, so I'm hoping the fix may come through on a future update. Gone back to OpenSuSE 11.2 for awhile.

---

