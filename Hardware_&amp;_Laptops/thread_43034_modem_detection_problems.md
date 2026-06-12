---
title: "modem detection problems"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by jadecell on 2005-06-20
i can't seem to get ubuntu to recognize that i have a modem. it's an external u.s.robotics 56k. anybody have this problem before? any ideas how to fix?

---

### Post by intangible on 2005-06-20
Here's an easy howto, all you have to know is if your modem is on Com1, 2, 3, or 4
[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

Sometimes external modems aren't detected automagically, so you have to tell the system which port it's on.

For your reference:
Com1 = /dev/ttyS0
Com2 = /dev/ttyS1
Com3 = /dev/ttyS2
Com4 = /dev/ttyS3

---

### Post by jadecell on 2005-06-20
great, thanks so much :)

---

