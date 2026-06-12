---
title: "Wacom Tablet resolution"
date: 2009-03-10
forum: Hardware
---

### Post by huruixd on 2009-03-10
Dear All,

Does anybody could explain what difference is between the tablet
resolution and screen resolution? Suppose I have a tablet PC, 

	Screen Resolution = 1024 x 768
	Tablet Resolution = 600  x 600

What if I reset the tablet active zone by editing the Options Top X/Y
and Bottom X/Y? Say decrease the width and height of the active zone to
the half of the original one. 

Questions:

1. Do I still have the same tablet resolution (i.e. 600 x 600) in the
new tablet active zone?

2. Am I right if I say, in certain sense, the stylus' sensitivity would
change in the new active zone? i.e. it moves a shorter distance, the
mouse moves the same distance as it was?

Thank you.

---

### Post by Favux on 2009-03-10
Hi huruixd,

I'm no expert and you could post to the LWP or maybe Loic2's thread to get a better answer.

But yes as I understand it the separate external graphics tablet's resolution is "absolute".  You can map it to a larger screen, but then you loose resolution on that larger screen (your tablet resolution is unchanged, just covering a larger area).  That's what xsetwacom commands like KeepShape are for, to keep the active area proportional.  That way circles don't change into ellipses, etc.

---

