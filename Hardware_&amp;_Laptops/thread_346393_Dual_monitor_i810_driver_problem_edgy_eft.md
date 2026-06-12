---
title: "Dual monitor i810 driver problem edgy eft"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by zbychu on 2007-01-25
I'm trying to run X server using xinerama (card Intel Corporation 82852/855GM Integrated Graphics Device) - i've got laptop and crt monitor right on it. I configured X server according to some xinerama tutorials like [http://www.ubuntuforums.org/showthread.php?p=1773624](http://www.ubuntuforums.org/showthread.php?p=1773624) but when i restart X i got errors:

"vm86() system generated signal 4
vbe initialization failed"

I found it was (is?) a bug in i810 driver in breezy [http://ubuntuforums.org/showthread.php?t=155762](http://ubuntuforums.org/showthread.php?t=155762) but it's appering in my edgy eft.

Any help?

---

### Post by zbychu on 2007-01-29
Anyone with the same problem? Someone heard about it?

---

### Post by teknorah on 2007-04-08
Yes, I had that problem.  I abandoned the use of xinerama, modeline & the 915resolution solutions.

See [my]("http://ubuntuforums.org/showthread.php?p=2422240#post2422240") post for more details.

---

