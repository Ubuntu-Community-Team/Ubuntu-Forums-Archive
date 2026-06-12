---
title: "I can't find anything about this error message"
date: 2008-07-20
forum: General Help
---

### Post by Bill Roberts on 2008-07-20
BUG: soft lockup - CPU#3 stuck for 11s! [khubd:1598]

Who should I ask?

---

### Post by brian_p on 2008-07-21
> **Bill Roberts said:**
> BUG: soft lockup - CPU#3 stuck for 11s! [khubd:1598]

Who should I ask?

Google: Search with 'BUG soft lockup'. It's the best I can offer.

---

### Post by Tim Sharitt on 2008-07-21
It is a kernel bug related to khubd, which is a kernel daemon responsible for configuring usb devices (I think, it may be responsible for naming devices). Here is a link with instructions on reporting kernel bugs [http://www.kernel.org/pub/linux/docs/lkml/reporting-bugs.html]("http://www.kernel.org/pub/linux/docs/lkml/reporting-bugs.html").

---

### Post by Bill Roberts on 2008-08-13
I submitted a bug report to launchpad.

---

