---
title: "bad .pdf printings"
date: 2010-03-08
forum: Hardware
---

### Post by kwstas on 2010-03-08
hi,

i have noticed that when i print .pdf docs i get a couple of blank lines, one at the top and the other at the bottom almost at the edges.
the printer is fine since xp prints fine any file format and even ubuntu prints fine except .pdf at least.

---

### Post by khelben1979 on 2010-03-08
What application are you using for print outs? I think this is the source of the problem.

---

### Post by efflandt on 2010-03-08
You have given no clue what printer you have, how it is connected [directly (USB?) or network), how you configured it, or what application you are printing from.

For creating PDFs I use the cups-pdf printer driver and simply print to that.  And my Lexmark network color laser printer is fairly generic in that it can do HP PCL or portscript, so all I had to do to configure it once cups printer setup found it on the network, was point cups at its ppd file.  So far everything appears to work fine.

---

### Post by kwstas on 2010-03-09
i tried printing with both evince and xournal. and it's the same. i really think it's about the .pdf files!

my printer xerox phaser 3100MFP is connected directly by usb.

---

### Post by kwstas on 2010-03-11
so after many tests i've found out that this issue comes only by some specific pdf docs and only in my "ubuntu" box.
i couldn't figure out which are the differences. i looked at their "properties" but they had no difference!
anyway as back-door solution i increased the "top margin" as much as the blank lines wouldn't have any effect on my important writings of the document.


some annoying thing i've noticed is that any changes i make in printer's settings either in "evince" nor in "admin>printing" menu have no affect in "preview" before printing!

---

### Post by redbook4574 on 2010-03-11
> **kwstas said:**
> hi,

i have noticed that when i print .pdf docs i get a couple of blank lines, one at the top and the other at the bottom almost at the edges.
the printer is fine since xp prints fine any file format and even ubuntu prints fine except .pdf at least.

Where are you, I had a similar problem in the U.K. and had to set ubuntu default printing to A4, it is U.S. letter by defa

---

### Post by kwstas on 2010-03-11
i'm in greece but if i remember well it is in A4...
i'll check it out tomorrow! i hope i'm wrong..

"edit":  it's A4 by default...

---

