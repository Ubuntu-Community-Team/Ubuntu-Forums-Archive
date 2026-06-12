---
title: "scrolling marquees via conky?"
date: 2008-10-31
forum: General Help
---

### Post by tryorke on 2008-10-31
yea, yet another conky thread :/ but i've searched the forums, ran a google search and got no results.

Is there any way to create a scrolling marquee effect with Conky?

---

### Post by cammin on 2008-10-31
They added **$scroll** a few months ago, but didn't update all of their documentation.
**${scroll 20 whatever you type here will scroll }**

From the man page

Scroll length text
Scroll 'text' showing 'length' number of characters at the  same time. The text may also contain variables. If a var creates output on multiple lines, then the lines are placed behind each other separated with a '|'-sign. Do NOT use vars that change colors or otherwise affect the design inside a scrolling text.
If  you want  spaces between the start and the end of 'text', place them at the end of 'text' not at the front ("foobar"  and  "  foobar" can  both  generate  "barfoo" but "foobar " will keep the spaces like this "bar foo").

---

### Post by Lîtus on 2009-09-14
> **cammin said:**
> They added **$scroll** a few months ago, but didn't update all of their documentation.
**${scroll 20 whatever you type here will scroll }**


Why that doesn't works for me?...

I'm using it in my .conkyBanshee.template:
```
${scroll 25 1 [--datatype=AL]}
```

Thanks!

---

