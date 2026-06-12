---
title: "Problem with finding &amp; deleting core dumps only"
date: 2008-08-05
forum: General Help
---

### Post by jakmite on 2008-08-05
I am trying to use the find command to locate all core dumps within the system and then delete them.

Here is what I have at the moment.

find / -type f -name "core.*" -exec rm {} \;

The problem now is that if there is file eg. core.png, core.txt, it will remove them as well together with the actual core dump, eg. core.3453

Is there a workaround for this, or do I need to write or bash script for this ?

---

### Post by ghostdog74 on 2008-08-05
core dumps are just named "core". remove the .*

---

