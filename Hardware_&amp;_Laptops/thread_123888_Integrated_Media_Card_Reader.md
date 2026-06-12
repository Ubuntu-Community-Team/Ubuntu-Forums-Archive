---
title: "Integrated Media Card Reader"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by dsierpin on 2006-01-31
Hello Forum-

My laptop has an integrated media card reader, and I guess there is no linux support for these yet.  What's the deal with that?  Are they just too new?

---

### Post by nocturn on 2006-01-31
[QUOTE=dsierpin]Hello Forum-

My laptop has an integrated media card reader, and I guess there is no linux support for these yet.  What's the deal with that?  Are they just too new?[/QUOTE]

What cardreader is it (or what brand/model laptop)?

---

### Post by dsierpin on 2006-01-31
I have an hp zv6000, I think the exact model is zv6130us.

I don't know the brand of the media reader, but the hp site describes it as:

"The integrated 6-in-1 digital media card reader For Secure Digital, MultiMediaCard, Memory Stick, Memory Stick Pro, SmartMedia, or xD-Picture Cards"

All the forum posts I've seen that make reference to media card readers aren't terribly hope-inspiring.  What's the deal?  :-k

---

### Post by mips on 2006-01-31
Support is very much dependant on the chipset used by the card reader.

---

### Post by dsierpin on 2006-01-31
Windows device manager tells me its a Texas Instruments PCIxx21 Integrated Flashmedia Controller.  Does that help?

---

### Post by mips on 2006-01-31
There might be a bit of hope on the horizon.

[http://www.linuxquestions.org/questions/showthread.php?t=320968&page=2](http://www.linuxquestions.org/questions/showthread.php?t=320968&page=2)
[http://www.everestinc.com/fml.htm](http://www.everestinc.com/fml.htm)
[http://www.webcon.ca/~imorgan/tifm21/](http://www.webcon.ca/~imorgan/tifm21/)

---

### Post by dsierpin on 2006-02-01
Thanks Mips,

I sent an email to the everest developers asking what's going on with the integrated device for the hp laptop (it's described as being in the testing phase on their success stories site).  I'll post here when I hear something.

---

### Post by nocturn on 2006-02-01
[QUOTE=dsierpin]I have an hp zv6000, I think the exact model is zv6130us.

I don't know the brand of the media reader, but the hp site describes it as:

"The integrated 6-in-1 digital media card reader For Secure Digital, MultiMediaCard, Memory Stick, Memory Stick Pro, SmartMedia, or xD-Picture Cards"

All the forum posts I've seen that make reference to media card readers aren't terribly hope-inspiring.  What's the deal?  :-k[/QUOTE]

If I'm not mistaken, it is the same Texas Instruments model as in mine (zv5000).

It is not currently supported, but I read that kernel 2.6.15 has basic support for it.  It might be working in Dapper but more likely Dapper +1.

---

