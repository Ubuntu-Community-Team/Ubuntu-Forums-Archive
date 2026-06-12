---
title: "Print dialog box ignores duplex option"
date: 2008-08-15
forum: General Help
---

### Post by jhsachs on 2008-08-15
I'm using Unbuntu v8.04.

My printer is an HP LaserJet 4M Plus with a document duplexer.

The printer configuration utility knows the duplexer is there.  (On the Installable Options box it is ticked.)

The Print dialog box apparently does not know it is there.  On the Page Setup tab there is a "Two-sided" dropdown which has only one entry, "One Sided."

How do I tell Ubuntu to print double-sided copy?

---

### Post by mannheim on 2008-08-15
This may be a reflection of the choice of driver for the printer. You could try using the "ljet4d" driver, which supports the LaserJet 4M with duplex (that's the "d").

To switch drivers (on Ubuntu 8.04) you can go to System-->Administration-->Printing, select your printer in the left-hand panel and then click on "Change..." next to "Make and Model". Then navigate forward to select the driver "HP LaserJet 4M Foomatic/ljet4d".

Of course, perhaps you are already using this driver! (Or perhaps switching to it makes no difference.) But its' worth a try.

---

### Post by jhsachs on 2008-08-16
'fraid it doesn't work. At least not usefully.

When I print a document with that driver, I get a message box warning me that the dialog box ignores the double-sided option.  What that means is: the driver feeds the paper through the duplexer, but still prints on only one side -- the back instead of the front.

Perhaps there's a more esoteric way to try to make this work?

---

