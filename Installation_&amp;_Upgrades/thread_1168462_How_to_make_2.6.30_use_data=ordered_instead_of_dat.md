---
title: "How to make 2.6.30 use data=ordered instead of data=writeback ... ?"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by zika on 2009-05-24
is there a way I could make 2.6.30.rc7 boot with my ext3 on Jaunty in  data=ordered or data=guarded mode? I do not want to use writeback ...  too risky ... :smile:
as I understood data=guarded is not available in 2.6.28?
I've tried things that worked in 2.6.28... data=ordered in /etc/fstab  e.t.c. ... nothing worked. if I put data =ordered in /etc/fstab I get  read-only boot ... :sad:
p.s.
it worked now with ```
tune2fs -o journal_data_ordered/dev/sdax
``` now and I', stummied why it did not work before. I had it that way earlier and I do not know when it changed and by whom ... .)
_[http://www.ubuntu-rs.org/forum/viewthread.php?tid=8272&goto=search&pid=90690](http://www.ubuntu-rs.org/forum/viewthread.php?tid=8272&goto=search&pid=90690)_

---

