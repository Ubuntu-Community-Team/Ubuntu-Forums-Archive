---
title: "Issues with Wacom pressure sensitivity"
date: 2012-03-25
forum: Hardware
---

### Post by Dustfang on 2012-03-25
So. I've got myself an ASUS b121-a1, and threw 11.10 onto it. Everything works except for the pressure sensitivity with the stylus. It reads, but it's just an 'on-off' type thing.

I was hoping someone here could help me get my pen input working properly

---

### Post by Favux on 2012-03-25
Hi Dustfang,

Welcome to Ubuntu forums!

In applications that support pressure are you configuring them for pressure with the stylus?

Let's look at some diagnostics.  Open a terminal and post the output of the following commands:
```
lsusb

xinput list
```

---

