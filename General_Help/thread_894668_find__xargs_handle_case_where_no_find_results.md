---
title: "find || xargs: handle case where no find results"
date: 2008-08-19
forum: General Help
---

### Post by jeffk on 2008-08-19
I have a convenience command to fix a [problem]("http://ubuntuforums.org/showthread.php?t=891008") with nfs-mounted folders receiving incorrect permissions. When there are no problem folders, the xargs part of the command gives a trivial error exit message.
```
$ sudo find . -type d ! -perm 0777 ! -path "*.Trash*" | sudo xargs -n 1 chmod a+rwx
chmod: missing operand after `a+rwx'
Try `chmod --help' for more information.
```
What bash command idiom can I use so that this short-circuits out before the xargs call when there are no find results?

Thanks.

---

### Post by rjack on 2008-08-19
use xargs with ```
--no-run-if-empty
```man xargs for details.

---

