---
title: "Get a key code"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by darkthawt on 2008-03-08
how to I find a key code for a certain button on my keyboard?

---

### Post by UBUSNAFU on 2008-03-08
Try this [http://www.ryancooper.com/resources/keycode.asp](http://www.ryancooper.com/resources/keycode.asp) or else a google search for keycode will turn up a bucketload of tables.

---

### Post by darkthawt on 2008-03-08
Thanks

---

### Post by Whiffle on 2008-03-08
Open up a terminal, run "xev"  Put your cursor over the white window, and press the key, the info for that key should show up in the terminal.

Not all keys make keyboard events though, some may make acpi events instead.  To catch those, there is another program whose name escapes me at the moment.

---

