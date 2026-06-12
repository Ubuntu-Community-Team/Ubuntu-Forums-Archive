---
title: "New Monitor"
date: 2005-02-24
forum: Hardware &amp; Laptops
---

### Post by Adrenal on 2005-02-24
Just got a new monitor (BenQ FP937 SILVER) and just installed her. Everything is great (so....big) but, how do I refresh the settings so that i can upgrade the res properly?
Cos right now, i can upgrade it, but the refresh rate stays at 60. It seems the settings are the ones from the old monitor, so, how do i upgrade it?

---

### Post by ember on 2005-02-24
[QUOTE=Adrenal]Just got a new monitor (BenQ FP937 SILVER) and just installed her. Everything is great (so....big) but, how do I refresh the settings so that i can upgrade the res properly?
Cos right now, i can upgrade it, but the refresh rate stays at 60. It seems the settings are the ones from the old monitor, so, how do i upgrade it?[/QUOTE]

Try dpkg-reconfigure xserver-xfree86 - if you haven't changed your XFConfig-4 file this will allow you to reselect everything X-related.

If you did change it by hand, there are instructions how to use dpkg-reconfigure anyway in the XFConfig-4 file

---

