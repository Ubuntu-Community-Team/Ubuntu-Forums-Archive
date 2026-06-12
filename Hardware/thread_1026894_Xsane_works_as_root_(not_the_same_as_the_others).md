---
title: "Xsane works as root (not the same as the others)"
date: 2008-12-31
forum: Hardware
---

### Post by skipfrehly on 2008-12-31
I have a Canon Pixma X700 all-in-one scanner, and I'm trying to get it to work through xsane.  I'm running 8.10 x64.  sane finds the scanner all right, and it works beautifully as root, but no matter what I do, it won't work as any other user.

I added myself into the group 'scanner', but still no avail.  When I start Xsane, I get a dialog saying 'failed to open device 'pixma:04A91729': access to resource has been denied'

Kind of a linux newbie, so please be patient with me :)

---

### Post by skipfrehly on 2008-12-31
EDIT:

So, in digging around, I found another group in the list called 'saned', after adding myself to that, everything appears to be working beautifully.

Sorry!

---

