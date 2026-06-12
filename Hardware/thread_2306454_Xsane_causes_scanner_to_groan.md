---
title: "Xsane causes scanner to groan"
date: 2015-12-15
forum: Hardware
---

### Post by ecowan on 2015-12-15
I rencently rebuilt my server system, which hosts  my scanner and printer, using Wily.
Wily came with Simple Scan, but I like Xsane's extra features. But now, when I try Xsane, locally or remotely, my HP8200 makes the most horrible grinding noise when it starts up. Luckily Simple Scan works just fine.
Thanks for any suggestions. - Erny

---

### Post by pqwoerituytrueiwoq on 2015-12-15
that seems odd, maybe the web based UI will work linked in my signature
i would suspect that sound is the scanner bar trying to move out of bounds where it is trying to find the starting point
id guess xsane is sending a option to the scanner that simple scans does not (or vise-versa) and the driver has a bug

---

### Post by ecowan on 2015-12-17
Yes. I'm sure that's what xsane is doing to my scanner.
I'm hoping someone who knows xsane well has a suggestion.

---

### Post by ecowan on 2016-01-06
Xsane seems to be treating my scanner with more respect now. I'm not sure why. But I'll mark this thread as [SOLVED].

---

