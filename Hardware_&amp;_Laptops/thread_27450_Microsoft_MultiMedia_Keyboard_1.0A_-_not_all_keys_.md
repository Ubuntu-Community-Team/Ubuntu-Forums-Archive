---
title: "Microsoft MultiMedia Keyboard 1.0A - not all keys work"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by petehall on 2005-04-16
I've got a Microsoft MultiMedia Keyboard 1.0A, and for the most part I have got all the keys working, but a few of the keys aren't producing keycodes at all: "My Pictures", "My Music", "Messenger" and "Log Off". Has anybody else encountered this please?

---

### Post by erkki70 on 2005-04-16
Hi,
Have a look here to read the threads about how to set extra keys.
[http://www.ubuntuforums.org/search.php?searchid=544839]("http://www.ubuntuforums.org/search.php?searchid=544839")
Good luck and hope it helps,

Cheers,
Erkki

---

### Post by petehall on 2005-04-16
Thanks. I managed to get there in the end. I obtained the keycodes from this page: [http://www.win.tue.nl/~aeb/linux/kbd/scancodes-5.html](http://www.win.tue.nl/~aeb/linux/kbd/scancodes-5.html)

...and then used setkeycode to create scancodes. Then I could see the events in xev.

---

