---
title: "Java font"
date: 2004-12-22
forum: General Help
---

### Post by Kraftwerk on 2004-12-22
I've just installed this 'linux' thing because my dad can't make electronic payments with XP sp2 (and I wanted to test it before installing it on my pc hehe :[ ).
The banking site -itself- is accessible now but still won't work.
It's using a java applet to verify a code and the font is WAY too big, the applet has a fixed size (sigh..) so the code is only partly visible :/
I guess the problem is that the applet wants to use windows fonts.. I already installed those though and it still too big, in fact, it's not using those fonts at all.

omgwtf :confused:

btw,  according to the bank my father should 'remove SP2' and 'uninstall Foxfire because it is dangerous hacker software'..... #-o

---

### Post by Kraftwerk on 2004-12-26
Sorry for *bump*ing my own post but I really need to find a way to solve this :-k

---

### Post by JsPr on 2004-12-26
Hi,
Try to change entries in this file:
/usr/lib/j2sdk1.4-sun/jre/lib/font.properties

IIRC, change the dialog.0 from lucidasans to some other font. Sometimes the lucidasans doesn't seem to "work" on Linux. I had a similar problem using SuSE where I changed it to susesans. Looked better.

---

