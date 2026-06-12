---
title: "What is my Soundcard?"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by mapes12 on 2008-01-29
Hi

Is there any command I can use to query my box to find out what brand and model soundcard is in it??

Mark

---

### Post by Foxray on 2008-01-29
do a lspci command in the terminal and it should tell you the location and type of card you have

---

### Post by linuxwizard on 2008-01-29
Try this
lspci -v   Or  lshw

---

### Post by oldsoundguy on 2008-01-29
or you can try sudo gtk-lshw or sudo lshw

---

