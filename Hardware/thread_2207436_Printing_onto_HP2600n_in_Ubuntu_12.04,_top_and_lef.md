---
title: "Printing onto HP2600n in Ubuntu 12.04, top and left edges are cut off"
date: 2014-02-23
forum: Hardware
---

### Post by RichTheCoder on 2014-02-23
I have CUPS 1.5.3 and I used it to define my HP 2600n Color LaserJet printer-queue as type "HP Color LaserJet 2600n Foomatic/foo2hp (recommended)". 

When it prints, the first character of each line, and half the header and footer lines, are missing. It seems to think that the printable area is the entire page. For instance, this happens when printing from the Chrome browser, or the medit text editor.

What to do?

I notice that when CUPS asks which printer to pick for the new printer-queue, the 2600n appears twice as a networked printer: 
   HP Color LaserJet 2600n (Hewlett-Packard HP Color LaserJet 2600n)
   HP Color LaserJet 2600n (HP Color LaserJet 2600n)

This seems odd - is it?

---

### Post by tgalati4 on 2014-02-23
Delete your printer.  Open a terminal:

```
hp-toolbox
```

Install the printer from there and you will get better drivers.  There are foomatic drivers, gutenprint drivers, hp drivers, and community-contributed drivers.  Many times you will have multiple drivers for the same printer.  Some work better than others.

---

### Post by RichTheCoder on 2014-02-26
Thanks, this worked well. It took a few minutes, and it complained about being unable to verify a digital signature, but the printer works correctly now.

---

