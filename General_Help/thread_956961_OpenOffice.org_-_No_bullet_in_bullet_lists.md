---
title: "OpenOffice.org - No bullet in bullet lists"
date: 2008-10-23
forum: General Help
---

### Post by swinky on 2008-10-23
I am running Intrepid and OpenOffice.org 3, and I have been having problems with my bullet lists in Writer. The first indent correctly displays the dark round bullet symbol, but the next level of indent does not display any bullet (where it should display the open circle), nor does it display a bullet on the third level (where it should display a square.) I have uninstalled and reinstalled OpenOffice twice with no luck.

The bullets in question work 100% fine on my desktop (both in Debian and in XP) and also on my laptop's Vista installation, all of which are running OpenOffice 3. So I would assume (perhaps incorrectly) that it is a problem with Intrepid. A long time spent searching the web seems to indicate that there is no (easy) way to change the default bullet style, so I don't think that it was anything I did (again, I could be wrong.)

Interestingly, if I use any of the custom styles, they work just fine. And while using custom bullet styles is an option, I use my laptop to take notes in class, so it would be nice to have the default bullet style actually working. Does anybody have ideas for reasons why this would be happening, fixes, or workarounds?

---

### Post by swinky on 2008-10-23
I managed to solve it with some detective work and guessing. OpenOffice uses a font called OpenSymbol for its bullets. I assumed that the problem was that my Ubuntu install lacked the font. Ironically, the problem was that it HAD the font installed. Bullets worked fine on my Debian machine because it lacked the font, and would replace it with a working font for bullets. Installing the font on Debian caused the same problem Ubuntu had. 

Therefore, it was an easy fix:
```
sudo apt-get remove ttf-opensymbol
```

OpenOffice still tries to use OpenSymbol for bullets, but it replaces it with a font that works.

---

### Post by davescafe on 2009-03-19
Thanks to swinky, I finally learned that the root cause of this defect involves fonts. I dug around and I have come up with another way to solve this problem:

[LIST=1]
[*]Launch OpenOffice.org
[*]Go to Tools >> Options
[*]In the OpenOffice.org section, select “Fonts” from the list
[*]Check the box, "Apply replacement table"
[*]In the “Font” drop-down list, select, “OpenSymbol”
[*]In the “Replace with” drop-down list, select, “Times New Roman”
[*]Click the small, “Apply” button (marked with a green check)
[*]The font-substitution entry should appear in the table. Check the box in the “Always” column and then click OK.
[/LIST]

Thanks again for the tip.

~Dave

---

