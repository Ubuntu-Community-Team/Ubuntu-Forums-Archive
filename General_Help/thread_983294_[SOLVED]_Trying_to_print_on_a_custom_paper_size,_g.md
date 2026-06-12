---
title: "[SOLVED] Trying to print on a custom paper size, giving me all kinda of hell..."
date: 2008-11-15
forum: General Help
---

### Post by AFarris01 on 2008-11-15
Heres the issue:  I need to print a document, which is made up of a combination of graphics, and text, onto 5x8 notecards, and it's giving me a ton more trouble than i had hoped for.

The document in question was created in OpenOffice.org, and the templates I've created for the paper size print properly from OpenOffice, however the document itself will not print properly because some of the pictures on the page have transparent bitson them, which cannot be moved/changed, and when I print from OpenOffice the presence of the transparency of the pictures causes strange erroneous characters all over the printout, which is unacceptable. 

To remedy this, I tried exporting the document as a PDF, and this allows me to print the document normally, but I cannot print on my custom paper size.  trying to print with default settings makes it stretch the document to try and fit it to a 8x11 sheet of paper, which i cannot use, and if i set up a custom paper size and try to print that way, it cycles the 5x8 card almost all the way out before it tried to print anything, yet again botching the printout.

I also tried downloading/installing Adobe's PDF reader to try printing from there, but all my text comes up as boxes, so I can't use it at all.

Additionally, on top of all this, the coloring of the document makes it impossible for me to do something like a 'double print' from OpenOffice to print out the graphics, then the text, because doing that would make some of the text invisible, or hard to read.

Does anybody have any ideas how i could fix some of this?  I'd kind of like to quit wasting all my ink trying to get this working :)

*My printer is an HP Deskjet F4280, installed via HPLIP

Thanks!
Andrew


------------------------[EDIT]------------------------------
Problem solved... It's a bug in the way evince is handling PDF printing for custom sizes... I'll be reporting it promptly.

Workaround:
1. Using the HPLIP manager window, go to the 'Print Settings > General > Media Size' and select the appropriate paper type/size
2. Right click on the printer you wish to print from in the left hand menu, and click 'Print'.
3. In the dialog menu that pops up, click 'Add File...' and browse to your document and click 'open'
4. Click the 'Print' button.

---

