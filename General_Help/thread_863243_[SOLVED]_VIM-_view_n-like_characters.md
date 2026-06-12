---
title: "[SOLVED] VIM- view \n-like characters"
date: 2008-07-18
forum: General Help
---

### Post by PGScooter on 2008-07-18
I, how can I see the \n, \t, \r characters while I am editing?

Thanks

---

### Post by pauper on 2008-07-18
Some of them via ":set list", others, I believe, are not meant to be seen.

---

### Post by PGScooter on 2008-07-18
thanks pauper, that is the kind of thing I am looking for. But instead of seeing a "$" at the end of a line, I would prefer to see a \n.

Is there any way to do this?

---

### Post by pauper on 2008-07-18
Only a _single_ character allowed for EOL.
In the example below every "$" symbol will be printed as "\"
:set lcs=eol:\

For more information see:
:h listchars

---

### Post by PGScooter on 2008-07-18
ah, interesting.

Great, thanks pauper!

---

