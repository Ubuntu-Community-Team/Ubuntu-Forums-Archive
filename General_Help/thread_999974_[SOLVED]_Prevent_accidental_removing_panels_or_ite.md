---
title: "[SOLVED] Prevent accidental removing panels or items?"
date: 2008-12-02
forum: General Help
---

### Post by opus_az on 2008-12-02
Hi...

Our thick thumbed users are in the habit of accidentally removing panel items, or deleting panels entirely. Since many of our users are not expected to be very computer literate, they're frequently confused and annoyed, and it's making the whole Linux experience a bit tainted.

I can lock items, but that just prevents items from moving, not preventing them from be removed. 

Any suggestions? (Hopefully I'm not missing something too obvious!)

---

### Post by glotz on 2008-12-02
Hello there!

Not exactly obvious but drop to a terminal and launch gconf-editor. Then select /apps/panel/global/locked_down. Now the panel cannot be dragged around or deleted. Ditto for locked applets.

---

### Post by opus_az on 2008-12-02
Well, you've already made two employees demonstrably happy, dang near gleeful!

---

### Post by glotz on 2008-12-02
Haha! :D

---

