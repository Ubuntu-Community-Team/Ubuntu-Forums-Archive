---
title: "startx: Screen 0 is not DRI capable"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by Lars Noodén on 2007-10-16
I can get X running concurrently with two different configurations:

[INDENT] X -nolisten tcp -novtswitch -sharevts -layout seat0 :0 &
 X -nolisten tcp -novtswitch -sharevts -layout seat1 :1 &
[/INDENT]

But cannot get them to run under a single layout (layout "multiseat" )  See xorg.conf:

[INDENT][http://www-personal.umich.edu/~lars/xorg.conf](http://www-personal.umich.edu/~lars/xorg.conf)[/INDENT]

The error from X is  "*(EE) AIGLX: Screen 0 is not DRI capable*"

Obviously this won't work for startx either (e.g. startx -- -layout multiseat)

---

### Post by lucho64 on 2007-10-25
I don't think that's what's preventing you from running multihead. I do have the same error on one of my "seats", but multiseat works anyway.

---

