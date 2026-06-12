---
title: "Canon PIXMA MP600 not working"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by m94mni on 2007-01-11
Hi!

I'm trying to get my new Canon PIXMA MP600 to work.

I've tried the official Canon iP4200 drivers (which are said to unofficially support the MP600) and the turboprint drivers - both detect the printer, but none of them manage to print a test page.

This might be a Edgy or Feisty only issue, I don't know.

Ideas?

---

### Post by c-m on 2007-01-24
I tried the free turboprint and the pixma mp600 works fine. 

just need to find a free driver now.

I'm on dapper 6.10 i think

---

### Post by m94mni on 2007-01-29
Found the problem --- user "lp" was not in group "plugdev"

Running

sudo adduser lp plugdev

fixes the issue, and I can now print....!

---

