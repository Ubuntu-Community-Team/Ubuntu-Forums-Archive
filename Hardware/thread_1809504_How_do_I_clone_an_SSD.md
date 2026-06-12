---
title: "How do I clone an SSD?"
date: 2011-07-21
forum: Hardware
---

### Post by chrisstankevitz on 2011-07-21
How do I clone my SSD?
a) use dd
b) use a hardware disk cloner
c) [your idea here]

If you are unfamiliar with the concept of TRIM and the performance loss associated with writing to every byte on the new SSD hard drive, please don't answer.

If you are familiar with these concepts, then you might dismiss options (a) and (b) as they write to every byte on the new SSD drive.

Thank you,

Chris

---

### Post by chrisstankevitz on 2011-07-21
Apparent answer: use method (a) or (b), then do an fstrim

[http://manpages.ubuntu.com/manpages/oneiric/man8/fstrim.8.html]("http://manpages.ubuntu.com/manpages/oneiric/man8/fstrim.8.html")

Not available in 10.10.

Chris

---

