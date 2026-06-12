---
title: "alt-key not working"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by tony11235 on 2006-11-11
I've installed 6.10 twice today, and my right alt-key has not worked. This has happened before when trying out 6.06. But it worked after the second install. This is on a Dell Latitude c610. Are there any quick fixes for this?

---

### Post by sharedagroove on 2006-11-11
I just recently upgraded to edgy and also lost my right alt key.  I'm running on an acer 5672.

---

### Post by GStubbs43 on 2006-11-11
Same problem here. I read a fix somewhere, but it didn't work. Any ideas? \\:D/

---

### Post by pwlodarczak on 2006-11-12
I had the same problem after upgrading to edgy, I had to change following lines in xorg.conf to:

        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"

and in system -> preferences -> keyboard -> layout options -> Third level choosers activate "Press Right Alt key to choose 3rd level."
Hope this helps.
Peter

---

### Post by GStubbs43 on 2006-11-12
I fixed it by going to System>Preferences>Keyboard>Layout Options>Third Level choosers>selected right windows key (since I don't have one) and it works perfectly now! yay!

---

### Post by sharedagroove on 2006-11-12
Selecting right windows key fixed my problem also, thanks

---

