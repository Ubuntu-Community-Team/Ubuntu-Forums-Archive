---
title: "HP Deskjet D4160 with Ubuntu 14.04"
date: 2014-10-12
forum: Hardware
---

### Post by Zorgoth on 2014-10-12
I am trying to use an HP Deskjet D4160 (hooked up via USB) to print a document, but it isn't working. The computer recognizes the printer and submits jobs, but they all have size 0k, and the printer refuses to process more than one job without being restarted, and when the jobs are processed, it prints blank pages. I'm using Ubuntu 14.04. The printer works fine from my roommate's Windows machine, and worked fine in the past when I used this printer with Ubuntu 12.04 last year.

Does anyone have any idea what might help?

---

### Post by Zorgoth on 2014-10-12
My problem is fixed. I downloaded hplip-gui and used it to detect my printer, which created another printer, which I then set to default in Printers, which then worked.

---

