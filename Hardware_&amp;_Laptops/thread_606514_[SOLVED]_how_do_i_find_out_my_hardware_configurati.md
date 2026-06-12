---
title: "[SOLVED] how do i find out my hardware configuration ?"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by adityakavoor on 2007-11-08
what is the " dxdiag " equivalent command for ubuntu ?
system -> pref -> hardware info doesnt giv info abt ram and grafix memory

any idea ?

---

### Post by wdbreen on 2007-11-08
Gday Mate,
Try this:

$sudo lshw

if you want this to come out as an easily read html document, try:

$sudo lshw -html > filename.html

Cheers

Breeny

---

### Post by adityakavoor on 2007-11-08
thanks mate :)

---

### Post by dabl on 2007-11-08
Here's more:

[http://www.computerbob.com/guests/how_to_get_system_info_in_linux.php](http://www.computerbob.com/guests/how_to_get_system_info_in_linux.php)

:)

---

### Post by adityakavoor on 2007-11-08
> **dabl said:**
> Here's more:

[http://www.computerbob.com/guests/how_to_get_system_info_in_linux.php](http://www.computerbob.com/guests/how_to_get_system_info_in_linux.php)

:)

getting this message

FORBIDDEN - YOU TRIED TO ACCESS A PAGE THAT YOU ARE FORBIDDEN FROM VIEWING. If you arrived here by clicking on a link from a search engine, then try clearing your browser's location bar and retyping the URL of the page that you want to see. If you believe that you should be able to view that page, you may send an email message to SECURITY403 at COMPUTERBOB.COM.

---

