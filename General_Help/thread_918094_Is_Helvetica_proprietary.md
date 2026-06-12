---
title: "Is Helvetica proprietary?"
date: 2008-09-12
forum: General Help
---

### Post by SyCo123 on 2008-09-12
A clarification on this if you know the answer please.

Helvetica is listed as a Linux core font 
Re this site [http://andrew.triumf.ca/fonts/fonts.html](http://andrew.triumf.ca/fonts/fonts.html)

but linotype.com requires a license for use and show the register mark with the name - Helvetica®	
[http://www.linotype.com/526/helvetica-family.html](http://www.linotype.com/526/helvetica-family.html)

So how is this font free to use on Linux?

---

### Post by unutbu on 2008-09-12
If you open /usr/share/htmldoc/fonts/Helvetica.afm with a text editor, you will see

> Comment Copyright (URW)++,Copyright 1999 by (URW)++ Design & Development
Comment Creation Date: 12/22/1999
Comment See the file COPYING (GNU General Public License) for license conditions.
FontName Helvetica

The Helvetica fonts on Ubuntu appear have been released by URW under the GPL license.

See also [http://en.wikipedia.org/wiki/URW](http://en.wikipedia.org/wiki/URW)
> 
URW is also known for their providing some of their fonts as free fonts. These are used in open source projects. For example, URW's versions of the standard PostScript typeface set is included in Ghostscript.

---

### Post by SyCo123 on 2008-09-12
Makes sense, thanks for clearing that up.

---

