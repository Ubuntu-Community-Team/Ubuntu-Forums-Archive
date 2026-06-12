---
title: "where is KDEDIR??"
date: 2008-11-01
forum: General Help
---

### Post by kakyoism on 2008-11-01
I'm trying to find this path, but "find" didn't lead me there...

$KDEDIR/share/apps/katepart/syntax

Can anybody tell me where the KDEDIR is?? Google didn't tell me either.

---

### Post by snova on 2008-11-01
KDEDIR is a shell variable, it doesn't exist literally. It's subsituted for its value at runtime.

It's probably set to /usr.

---

### Post by kakyoism on 2008-11-01
hi, 

echo $KDEDIR

gives me nothing.

I suspect that it should be ~/.kde??

Thx!

---

### Post by snova on 2008-11-01
It doesn't expand to anything here either, but it's definitely not ~/.kde, because the directory in question doesn't exist there. It *does* exist in /usr/share/apps/katepart/syntax, so that was probably what you wanted.

---

