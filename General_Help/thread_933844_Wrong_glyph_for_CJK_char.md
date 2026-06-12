---
title: "Wrong glyph for CJK char"
date: 2008-09-29
forum: General Help
---

### Post by John Chambers on 2008-09-29
If there's a forum where this question would be more appropriate, let me know, because I couldn't find it.

Anyway, I've been experimenting with Chinese text on ubuntu, and found a curious case of the wrong glyph being displayed.  It's for a CJK radical, with unicode value U+2EA8.  This is the "standing dog" character, and it displays OK on a couple of other machines, including the Mac sitting next to this ubuntu box and a nearby Windows box.  But on the ubuntu display, it shows the glyph for Kangxi radical 103 (pi3 = bolt of cloth).  I copied the glyph to a hex-dump program, and it shows E2 BA A8, which is the correct UTF-8 for U+2EA8.  So the file contains the correct bits for that char, but the glyph on the screen is a different character.

I tried it with a number of windows, including gnome-terminal and pointing two browsers (firefox and opera) at [http://unicode.org/charts/unihan.html](http://unicode.org/charts/unihan.html) and typing "2EA8" into its lookup box.  The resulting "Unicode Standard" column shows the correct standing-dog glyph (which is a GIF image), but the "Your Browser" column shows the incorrect bolt-of-cloth glyph. So the U+ code is right but the glyph displayed is wrong.

I've been trying to learn how to either fix the problem or report it somewhere, and I've hit brick walls for both.  Is there a way to examine the installed fonts, and see if the problem might be a wrong glyph in whatever font is being used?  Or is there a way to verify that this is a software bug that needs to be reported somewhere?

So far, this one char seems an isolated error, but of course I haven't looked at all the thousands of CJK characters, so there could well be more.  This one popped up in a dictionary file, which told me the CJK name of the character, and I saw a different char there.  And I'm at a loss to know what to do about it to get it to display right.

---

