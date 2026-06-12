---
title: "Changing Default Print Order"
date: 2008-08-09
forum: General Help
---

### Post by Greasyfingers on 2008-08-09
I'm using a Brother-DCP330C printer/scanner. It's not a great printer, but it could be made better if I could find a way to stop it printing multi-page documents in reverse order (last page first). I can understand the reason for having this setting in a printer with a face-up printer tray, but I do a lot of two-sided printing, and I prefer to have reverse mean reverse when I select reverse! It becomes especially confusing when some applications try to be helpful and automatically reverse the order in a two part run.

I've tried altering the file /usr/share/cups/model/brdcp330c.ppd which has the entry

*DefaultOutputOrder: Reverse

I believe the three options for this are Normal, Reverse and Automatic, but none of them make any difference. Is there something else I need to change?

---

