---
title: "printer offset dcp 135"
date: 2011-05-30
forum: Hardware
---

### Post by Hakimjo on 2011-05-30
I have installed the driver for the brother dcp 135 from the manufacturer site and from repositories.  It prints nicely (at least simple things), but with about one inch offset.  How can I correct this ?

---

### Post by dutchman77 on 2011-06-28
I know this is a very old thread, but for some people around looking ofr a solution on this, the follow command will help them:

sudo brprintconf_dcp150c -pt A4

My printer was a "Brother DCP 150C", so the appropriate command for you should like "brprintconf_<put_your_name_printer_here>" (in this case brprintconf_dcp135)

Hope it may help someone

---

