---
title: "init vs telinit"
date: 2008-09-04
forum: General Help
---

### Post by sulekha on 2008-09-04
Hi all, 

when switching runlevels in ubuntu hardy, what exactly is the subtle difference between sudo telinit <runlevel> and sudo init <runlevel> ?

---

### Post by Oldsoldier2003 on 2008-09-04
from the manpage:

>        init is not normally executed by a user process, and expects to have  a
       process  id  of  1.   If this is not the case, [B]it will actually execute
       telinit[/B]( 8 ) and pass all arguments to that.  See that  manual  page  for
       further details.


use telinit because init just calls it anyways.

---

