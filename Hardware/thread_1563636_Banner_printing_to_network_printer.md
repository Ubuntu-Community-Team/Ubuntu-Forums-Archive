---
title: "Banner printing to network printer"
date: 2010-08-29
forum: Hardware
---

### Post by NMFTM on 2010-08-29
How would I go about printing a very long image that would take up about 2 sheets in landscape mode at 100% it's actual size to a network printer?

It doesn't seem like theirs a way to do this in the GTK print settings and the I'm having trouble getting it to work in lp.

Here's what I've tried:
```
lp -d dnssd://<rest_of_device_URI_omitted> -o scaling=200
```It gives me the error message that the "printer or class was not found".

I looked through lp's man page and did a grep search for "uri" and "network". But it didn't return anything.

---

